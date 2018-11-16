---
title: '方法: Visual Studio の非同期のサービス提供 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4833fcef561bcc7c81a8c19fd5c4a1fcb2f7ccea
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767631"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>方法: Visual Studio の非同期のサービス提供
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UI スレッドをブロックすることがなくサービスを取得する場合は、非同期のサービスを作成し、バック グラウンド スレッドでパッケージを読み込みます。 この目的に使用することができます、<xref:Microsoft.VisualStudio.Shell.AsyncPackage>なく<xref:Microsoft.VisualStudio.Shell.Package>と非同期のパッケージの特殊な非同期メソッドでサービスの追加  
  
 Visual Studio の同期サービスを提供する方法の詳細については、次を参照してください。[方法: サービスを提供](../extensibility/how-to-provide-a-service.md)します。  
  
## <a name="implementing-an-asynchronous-service"></a>非同期のサービスを実装します。  
  
1.  VSIX プロジェクトを作成 (**ファイル/新規、プロジェクト/Visual c#/呼び出/VSIX プロジェクト**)。 プロジェクトに名前を**TestAsync**します。  
  
2.  VSPackage をプロジェクトに追加します。 プロジェクト ノードを選択、**ソリューション エクスプ ローラー**クリック**追加/新しい項目/Visual c# アイテム/機能拡張/Visual Studio パッケージ**。 このファイルに名前を**TestAsyncPackage.cs**します。  
  
3.  TestAsyncPackage.cs では、パッケージではなく、AsyncPackage から継承するようにパッケージを変更します。  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  サービスを実装するには次の 3 つの種類を作成する必要があります。  
  
    -   サービスを表すインターフェイスです。 これらのインターフェイスの多くは、空、つまり、どのメソッド。  
  
    -   サービス インターフェイスを記述するインターフェイスです。 このインターフェイスには、実装するメソッドが含まれています。  
  
    -   サービスと、サービス インターフェイスの両方を実装するクラス。  
  
5.  次の例では、3 種類の非常に基本的な実装を示します。 サービス クラスのコンス トラクターは、サービス プロバイダーを設定する必要があります。 この例でのみ、サービス パッケージのコード ファイルに追加します。  
  
6.  次の追加ステートメントを使用して、パッケージ ファイル。  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;  
    ```  
  
7.  非同期のサービスの実装を次に示します。 コンス トラクターで、同期サービス プロバイダーではなく、非同期サービス プロバイダーを設定する必要があることに注意してください。  
  
    ```  
    public class TextWriterService : STextWriterService, ITextWriterService  
    {  
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;  
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)  
        {  
            serviceProvider = provider;  
        }  
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)  
        {  
            StreamWriter writer = new StreamWriter(path);  
            await writer.WriteLineAsync(line);  
            writer.Close();  
        }  
        public TaskAwaiter GetAwaiter()  
        {  
            return new TaskAwaiter();  
        }  
    }  
    public interface STextWriterService  
    {  
    }  
    public interface ITextWriterService   
    {  
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);  
        TaskAwaiter GetAwaiter();  
    }  
    ```  
  
## <a name="registering-a-service"></a>サービスを登録します。  
 サービスを登録するには、追加、<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>サービスを提供するパッケージにします。 同期サービスの登録から 2 つの違いがあります。  
  
- 自動読み込みする場合は、パッケージを追加する必要がある、 <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> BackgroundLoad 属性の値。 自動読み込みの Vspackage の詳細については、次を参照してください。 [Vspackage の読み込み](../extensibility/loading-vspackages.md)します。  
  
- 追加する必要があります、 **AllowsBackgroundLoading = true**フィールドを<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>します。 PackageRegistrationAttribute の詳細については、次を参照してください。[の登録および登録を解除する Vspackage](../extensibility/registering-and-unregistering-vspackages.md)します。  
  
  非同期のサービスの登録、asyncpackage からの例を次に示します。  
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="adding-a-service"></a>サービスの追加  
  
1.  TestAsyncPackage.cs、削除、`Initialize()`メソッドとオーバーライド、`InitializeAsync()`メソッド。 サービスを追加し、サービスを作成するコールバック メソッドを追加します。 サービスを追加する非同期の初期化子の例を次に示します。  
  
    ```  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
2.  Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll への参照を追加します。  
  
3.  作成して、サービスを返す非同期メソッドとしては、コールバック メソッドを実装します。  
  
    ```csharp  
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        STextWriterService service = null;  
        await System.Threading.Tasks.Task.Run(() => {  
                    service = new TextWriterService(this);  
             });  
  
        return service;  
    }  
  
    ```  
  
## <a name="using-a-service"></a>サービスを使用します。  
 これで、サービスを取得し、そのメソッドを使用できます。  
  
1.  これで、初期化子を説明しますが、サービスを使用する任意の場所サービスを取得することができます。  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     変更することを忘れないでください *\<userpath >* ファイル名とコンピューターに意味のあるパスに!  
  
2.  ビルドして、コードを実行します。 Visual Studio の実験用インスタンスが表示されたら、ソリューションを開きます。 これにより、autoload を AsyncPackage です。 初期化子が実行すると、場合に、指定した場所でファイルを検索する必要があります。  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>コマンド ハンドラーでの非同期のサービスの使用  
 メニュー コマンドで非同期のサービスを使用する方法の例を次に示します。 ここで示すように、他の非非同期メソッドで、サービスを使用するプロシージャを使用することができます。  
  
1.  プロジェクトにメニュー コマンドを追加します。 (で、**ソリューション エクスプ ローラー**、選択、プロジェクト ノードを右クリックし、**追加/新しい項目の/拡張機能/カスタム コマンド**)。コマンド ファイルの名前を付けます**TestAsyncCommand.cs します。**  
  
2.  カスタム コマンド テンプレートは再追加、`Initialize()`コマンドを初期化するために TestAsyncPackage.cs ファイルへのメソッド。 Initialize() メソッドでは、コマンドを初期化する行をコピーします。 内容は次のようになります。  
  
    ```  
    TestAsyncCommand.Initialize(this);  
    ```  
  
     この行に移動、 `InitializeAsync()` AsyncPackageForService.cs ファイル内のメソッド。 コマンドを使用して初期化する前にメイン スレッドへ切り替える必要がありますので、これは、非同期の初期化では、<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>します。 次のようにはなります。  
  
    ```csharp  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        TestAsyncCommand.Initialize(this);    
  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync((<userpath>, "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
3.  削除、`Initialize()`メソッド。  
  
4.  TestAsyncCommand.cs ファイルでは、検索、`MenuItemCallback()`メソッド。 メソッドの本体を削除します。  
  
5.  using ステートメントを追加します。  
  
    ```  
    using System.IO;  
    ```  
  
6.  非同期メソッドという名前の追加`GetAsyncService()`とそのメソッドを使用してサービスを取得します。  
  
    ```csharp  
    private async System.Threading.Tasks.Task GetAsyncService()  
    {  
        ITextWriterService textService =   
           this.ServiceProvider.GetService(typeof(STextWriterService))  
              as ITextWriterService;  
        // don’t forget to change <userpath> to a local path  
        await writer.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  このメソッドを呼び出し、`MenuItemCallback()`メソッド。  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        GetAsyncService();  
    }  
  
    ```  
  
8.  ソリューションをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されたらを参照してください。、**ツール**メニューを探して、**呼び出す TestAsyncCommand**メニュー項目。 これをクリックすると、TextWriterService は指定したファイルに書き込みます。 (必要はありません、ソリューションを開くに読み込むパッケージをによりもコマンドを呼び出すためです。)  
  
## <a name="see-also"></a>関連項目  
 [サービスの使用と提供](../extensibility/using-and-providing-services.md)

