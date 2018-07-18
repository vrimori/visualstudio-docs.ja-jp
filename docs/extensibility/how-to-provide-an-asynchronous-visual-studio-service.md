---
title: '方法: 非同期の Visual Studio サービスを提供 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8741779cf96cb970f3ebc4907443b85ced5b80c0
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705074"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>方法: 非同期の Visual Studio サービスを提供
UI スレッドをブロックすることがなくサービスを取得する場合は、非同期のサービスを作成し、バック グラウンド スレッドでパッケージを読み込む必要があります。 この目的で使用することができます、<xref:Microsoft.VisualStudio.Shell.AsyncPackage>ではなく、 <xref:Microsoft.VisualStudio.Shell.Package>、非同期のパッケージの特別な非同期メソッドで、サービスを追加します。
  
 Visual Studio の同期サービスを提供する方法については、次を参照してください。[する方法: サービスを提供](../extensibility/how-to-provide-a-service.md)です。  
  
## <a name="implementing-an-asynchronous-service"></a>非同期のサービスを実装します。  
  
1.  VSIX プロジェクトを作成 (**ファイル > 新規 > プロジェクト > Visual c# > Extensiblity > VSIX プロジェクト**)。 プロジェクトに名前を**TestAsync**です。  
  
2.  VSPackage をプロジェクトに追加します。 プロジェクト ノードを選択、**ソリューション エクスプ ローラー**  をクリック**追加 > 新しい項目の追加 > Visual c# アイテム > Extensibility > Visual Studio パッケージ**です。 このファイルの名前を付けます**TestAsyncPackage.cs**です。  
  
3.  TestAsyncPackage.cs では、パッケージではなく、AsyncPackage から継承するパッケージを変更します。  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  サービスを実装するのには、次の 3 種類の作成が必要です。  
  
    -   サービスを識別するインターフェイスです。 これらのインターフェイスの多くは、空、つまりがないメソッドように、サービスを照会するためにのみ使用されます。
  
    -   サービス インターフェイスを表すインターフェイスです。 このインターフェイスには、実装するメソッドが含まれています。  
  
    -   サービスと、サービス インターフェイスの両方を実装するクラス。  
  
5.  次の例では、3 種類の非常に基本的な実装を示します。 サービス クラスのコンス トラクターは、サービス プロバイダーを設定する必要があります。 この例ではだけ追加サービス パッケージのコード ファイルにします。  
  
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
  
7.  非同期のサービスの実装を次に示します。 コンス トラクターで、同期サービス プロバイダーではなく、非同期サービス プロバイダーを設定する必要がある注意してください。  
  
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
  
## <a name="registering-a-service"></a>サービスを登録します。  
 サービスを登録するには追加、<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>サービスを提供するパッケージにします。 同期サービスを登録する異なるがあるパッケージとサービスの両方が非同期の読み込みをサポートしているかどうかを確認します。
  
-   追加する必要があります、 **AllowsBackgroundLoading = true**フィールドを<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>、PackageRegistrationAttribute の詳細についてはパッケージが非同期的に初期化するためには、次を参照してください[登録し、。Vspackage の登録を解除](../extensibility/registering-and-unregistering-vspackages.md)です。  
  
-   追加する必要があります、 **IsAsyncQueryable = true**フィールドを<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>サービス インスタンスを非同期的に初期化できるようにします。

 非同期サービス登録のため、asyncpackage からの例を次に示します。
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="adding-a-service"></a>サービスの追加  
  
1.  TestAsyncPackage.cs、削除、`Initialize()`メソッドを上書き、`InitializeAsync()`メソッドです。 サービスを追加し、サービスを作成するコールバック メソッドを追加します。 サービスを追加する非同期の初期化子の使用例を次に示します。  
  
    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }  
  
    ```  
  
2.  Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll への参照を追加します。  
  
3.  作成して、サービスを返す非同期メソッドとして、コールバック メソッドを実装します。  
  
    ```csharp  
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        TextWriterService service = new TextWriterService(this);  
        await service.InitializeAsync(cancellationToken);
        return service;
    }  
  
    ```  
  
## <a name="using-a-service"></a>サービスを使用します。  
 これで、サービスを取得し、そのメソッドを使用できます。  
  
1.  これを初期化子で説明しますが、サービスを使用する場合、サービス任意の場所を取得することができます。  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync(<userpath>), "this is a test");  
    }  
  
    ```  
  
     忘れずに変更 *\<userpath >* ファイル名とコンピューターに意味のあるパスにします。  
  
2.  ビルドし、コードを実行します。 Visual Studio の実験用インスタンスが表示されたら、ソリューションを開きます。 これにより、autoload を AsyncPackage です。 初期化子が実行時に、指定した場所でファイルを検索する必要があります。  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>コマンド ハンドラーで非同期のサービスの使用  
 メニュー コマンドで非同期のサービスを使用する方法の例を次に示します。 サービスを使用して、他の非非同期メソッドは、ここに示した手順を使用することができます。  
  
1.  プロジェクトにメニュー コマンドを追加します。 (で、**ソリューション エクスプ ローラー**を選択し、プロジェクト ノード、右クリックし、選択**追加/新しい項目の/機能拡張/カスタム コマンド**)。コマンド ファイルの名前を付けます**TestAsyncCommand.cs です。**  
  
2.  コマンドのカスタム テンプレートを再追加、`Initialize()`コマンドを初期化するために TestAsyncPackage.cs ファイルへのメソッドです。 Initialize() メソッドでは、コマンドを初期化する行をコピーします。 内容は次のようになります。  
  
    ```csharp
    TestAsyncCommand.Initialize(this);  
    ```  
  
     この行に移動する、 `InitializeAsync()` AsyncPackageForService.cs ファイル内のメソッドです。 これは非同期の初期化のため、切り替える必要があります、メイン スレッドにコマンドを使用して、初期化する前に<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>です。 今すぐに次のようになります。  
  
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
  
3.  削除、`Initialize()`メソッドです。  
  
4.  TestAsyncCommand.cs ファイルの検索、`MenuItemCallback()`メソッドです。 メソッドの本体を削除します。  
  
5.  using ステートメントを追加します。  
  
    ```csharp 
    using System.IO;  
    ```  
  
6.  名前付き、非同期メソッドを追加`UseTextWriterAsync()`とそのメソッドを使用してサービスを取得します。  
  
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
  
7.  このメソッドを呼び出して、`MenuItemCallback()`メソッド。  
  
    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        UseTextWriterAsync();  
    }  
  
    ```  
  
8.  ソリューションをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されたらに移動、**ツール**メニューおよび [検索対象]、**呼び出す TestAsyncCommand**メニュー項目。 をクリックすると、TextWriterService は指定したファイルに書き込みます。 (必要はありませんを開くには、ソリューションを読み込むパッケージを引き起こしますもコマンドを実行します。)  
  
## <a name="see-also"></a>関連項目  
 [サービスの使用と提供](../extensibility/using-and-providing-services.md)
