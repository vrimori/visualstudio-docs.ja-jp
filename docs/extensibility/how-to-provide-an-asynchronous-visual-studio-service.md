---
title: '方法: Visual Studio の非同期のサービス提供 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6139187ec619ac1825cc56f801035bc4f719854b
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639261"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>方法: 非同期の Visual Studio サービスを提供
UI スレッドをブロックすることがなくサービスを取得する場合は、非同期のサービスを作成し、バック グラウンド スレッドでパッケージを読み込みます。 この目的に使用することができます、<xref:Microsoft.VisualStudio.Shell.AsyncPackage>なく<xref:Microsoft.VisualStudio.Shell.Package>、非同期のパッケージの特殊な非同期メソッドを持つサービスを追加します。
  
 Visual Studio の同期サービスを提供する方法の詳細については、次を参照してください。[方法: サービスを提供](../extensibility/how-to-provide-a-service.md)します。  
  
## <a name="implement-an-asynchronous-service"></a>非同期のサービスを実装します。  
  
1.  VSIX プロジェクトを作成 (**ファイル** > **新規** > **プロジェクト** > **Visual c#**  > **呼び出** > **VSIX プロジェクト**)。 プロジェクトに名前を**TestAsync**します。  
  
2.  VSPackage をプロジェクトに追加します。 プロジェクト ノードを選択、**ソリューション エクスプ ローラー**クリック**追加** > **新しい項目の** > **Visual c# アイテム**  > **拡張** > **Visual Studio パッケージ**します。 このファイルに名前を*TestAsyncPackage.cs*します。  
  
3.  *TestAsyncPackage.cs*から継承するようにパッケージを変更`AsyncPackage`なく`Package`:  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  サービスを実装するには次の 3 つの種類を作成する必要があります。  
  
    -   サービスを識別するインターフェイスです。 これらのインターフェイスの多くは、空、つまりがないメソッドように、サービスのクエリを実行するためにのみ使用されます。
  
    -   サービス インターフェイスを記述するインターフェイスです。 このインターフェイスには、実装するメソッドが含まれています。  
  
    -   サービスと、サービス インターフェイスの両方を実装するクラス。  
  
5.  次の例では、3 種類の非常に基本的な実装を示します。 サービス クラスのコンス トラクターは、サービス プロバイダーを設定する必要があります。 この例でのみ、サービス パッケージのコード ファイルに追加します。  
  
6.  次の追加ステートメントを使用して、パッケージ ファイル。  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```  
  
7.  非同期のサービスの実装を次に示します。 コンス トラクターで、同期サービス プロバイダーではなく、非同期サービス プロバイダーを設定する必要があることに注意してください。  
  
    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService  
    {  
        private IAsyncServiceProvider asyncServiceProvider;  
        
        public TextWriterService(IAsyncServiceProvider provider)  
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;  
        }
        
        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);               
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }
        
        public async Task WriteLineAsync(string path, string line)  
        {  
            StreamWriter writer = new StreamWriter(path);  
            await writer.WriteLineAsync(line);  
            writer.Close();  
        }  
    }  

    public interface STextWriterService  
    {  
    }  
    
    public interface ITextWriterService   
    {  
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);  
    }  
    ```  
  
## <a name="register-a-service"></a>サービスを登録します。  
 サービスを登録するには、追加、<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>サービスを提供するパッケージにします。 同期サービスを登録するのには異なる場合があるパッケージとサービスの両方が非同期の読み込みをサポートしているかどうかを確認します。
  
-   追加する必要があります、 **AllowsBackgroundLoading = true**フィールドを<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>、PackageRegistrationAttribute の詳細についてはパッケージを非同期的に初期化できることを確認するを参照してください[を登録し、。Vspackage の登録解除](../extensibility/registering-and-unregistering-vspackages.md)します。  
  
-   追加する必要があります、 **IsAsyncQueryable = true**フィールドを<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>サービス インスタンスを非同期的に初期化できることを確認します。

 次の例に示します、`AsyncPackage`非同期のサービスの登録で。
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="add-a-service"></a>サービスを追加します。  
  
1.  *TestAsyncPackage.cs*、削除、`Initialize()`メソッドとオーバーライド、`InitializeAsync()`メソッド。 サービスを追加し、サービスを作成するコールバック メソッドを追加します。 サービスを追加する非同期の初期化子の例を次に示します。  
  
    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }  
  
    ```  
  
2.  参照を追加*Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*します。  
  
3.  作成して、サービスを返す非同期メソッドとしては、コールバック メソッドを実装します。  
  
    ```csharp  
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        TextWriterService service = new TextWriterService(this);  
        await service.InitializeAsync(cancellationToken);
        return service;
    }  
  
    ```  
  
## <a name="use-a-service"></a>サービスを使用します。  
 これで、サービスを取得し、そのメソッドを使用できます。  
  
1.  これで、初期化子を説明しますが、サービスを使用する任意の場所サービスを取得することができます。  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync(<userpath>), "this is a test");  
    }  
  
    ```  
  
     変更することを忘れないでください *\<userpath >* ファイル名とコンピューターに意味のあるパスに!  
  
2.  ビルドして、コードを実行します。 Visual Studio の実験用インスタンスが表示されたら、ソリューションを開きます。 これにより、 `AsyncPackage` autoload をします。 初期化子が実行すると、場合に、指定した場所でファイルを検索する必要があります。  
  
## <a name="use-an-asynchronous-service-in-a-command-handler"></a>コマンド ハンドラーでの非同期のサービスを使用します。  
 メニュー コマンドで非同期のサービスを使用する方法の例を次に示します。 ここで示すように、他の非非同期メソッドで、サービスを使用するプロシージャを使用することができます。  
  
1.  プロジェクトにメニュー コマンドを追加します。 (で、**ソリューション エクスプ ローラー**、選択、プロジェクト ノードを右クリックし、**追加** > **新しい項目の** >  **機能拡張** > **カスタム コマンド**)。コマンド ファイルの名前を付けます*TestAsyncCommand.cs*します。  
  
2.  カスタム コマンド テンプレートは再追加、`Initialize()`メソッドを*TestAsyncPackage.cs*コマンドを初期化するためにファイル。 `Initialize()`メソッドでは、コマンドを初期化する行をコピーします。 内容は次のようになります。  
  
    ```csharp
    TestAsyncCommand.Initialize(this);  
    ```  
  
     この行に移動、`InitializeAsync()`メソッドで、 *AsyncPackageForService.cs*ファイル。 コマンドを使用して初期化する前にメイン スレッドへ切り替える必要がありますので、これは、非同期の初期化では、<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>します。 次のようにはなります。  
  
    ```csharp  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  

        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync((<userpath>, "this is a test");  
  
        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);  
        TestAsyncCommand.Initialize(this);
    }  
  
    ```  
  
3.  削除、`Initialize()`メソッド。  
  
4.  *TestAsyncCommand.cs*ファイルで、検索、`MenuItemCallback()`メソッド。 メソッドの本体を削除します。  
  
5.  using ステートメントを追加します。  
  
    ```csharp 
    using System.IO;  
    ```  
  
6.  非同期メソッドという名前の追加`UseTextWriterAsync()`とそのメソッドを使用してサービスを取得します。  
  
    ```csharp  
    private async System.Threading.Tasks.Task UseTextWriterAsync()  
    {  
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =   
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))  
              as ITextWriterService;  

        // don't forget to change <userpath> to a local path  
        await textService.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  このメソッドを呼び出し、`MenuItemCallback()`メソッド。  
  
    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        UseTextWriterAsync();  
    }  
  
    ```  
  
8.  ソリューションをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されたらを参照してください。、**ツール**メニューを探して、**呼び出す TestAsyncCommand**メニュー項目。 これをクリックすると、TextWriterService は指定したファイルに書き込みます。 (必要はありません、ソリューションを開くに読み込むパッケージをによりもコマンドを呼び出すためです。)  
  
## <a name="see-also"></a>関連項目  
 [使用し、サービスを提供](../extensibility/using-and-providing-services.md)
