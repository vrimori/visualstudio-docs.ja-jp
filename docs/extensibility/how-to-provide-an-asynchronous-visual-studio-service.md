---
title: "方法: Visual Studio の非同期サービスを提供 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: Visual Studio の非同期サービスを提供
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

UI スレッドをブロックすることがなくサービスを取得する場合は、非同期サービスを作成し、バック グラウンド スレッドでパッケージを読み込むことです。 この目的で使用することができます、 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> ではなく、 <xref:Microsoft.VisualStudio.Shell.Package>, 、非同期のパッケージの特別な非同期メソッドにより、サービスを追加  
  
 Visual Studio の同期サービスを提供する方法については、次を参照してください。 [方法: サービスを提供](../extensibility/how-to-provide-a-service.md)します。  
  
## 非同期のサービスを実装します。  
  
1.  VSIX プロジェクトを作成する \(**ファイル\/\[新しい\/プロジェクト\/Visual c\#\/Extensiblity\/VSIX プロジェクト**\)。 プロジェクトに名前を **TestAsync**します。  
  
2.  VSPackage をプロジェクトに追加します。 プロジェクト ノードを選択して、 **ソリューション エクスプ ローラー** \] をクリック **追加\/\[新しい項目\/Visual c\# アイテム\/機能拡張\/Visual Studio パッケージ**します。 このファイルに名前 **TestAsyncPackage.cs**します。  
  
3.  TestAsyncPackage.cs では、パッケージではなく、AsyncPackage から継承するパッケージを変更します。  
  
    ```c#  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  サービスを実装するには、次の 3 つの種類を作成する必要があります。  
  
    -   サービスを記述したインターフェイスです。 これらのインターフェイスの多くは、空、つまりがないメソッド。  
  
    -   サービス インターフェイスについて説明するインターフェイス。 このインターフェイスには、実装されるメソッドが含まれています。  
  
    -   サービスと、サービス インターフェイスの両方を実装するクラス。  
  
5.  次の例では、次の 3 つの種類の非常に基本的な実装を示します。 サービス クラスのコンス トラクターは、サービス プロバイダーを設定する必要があります。 この例では私たちだけ追加サービス パッケージのコード ファイルにします。  
  
6.  次の追加 using ステートメントをパッケージ ファイル。  
  
    ```c#  
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
  
## サービスを登録します。  
 サービスを登録するには、追加、 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> サービスを提供するパッケージにします。 同期サービスを登録するを 2 つの違いがあります。  
  
-   自動読み込みする場合は、パッケージに追加する必要がありますが、 <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> 属性に BackgroundLoad 値。 自動読み込み VSPackages に関する詳細については、次を参照してください。 [Vspackage を読み込む](../extensibility/loading-vspackages.md)します。  
  
-   追加する必要があります、 **AllowsBackgroundLoading \= true** フィールドを <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>です。 詳細については、PackageRegistrationAttribute を参照してください。 [Vspackage の登録と登録解除しています](../extensibility/registering-and-unregistering-vspackages.md)します。  
  
 非同期サービスの登録を使用する AsyncPackage の例を次に示します。  
  
```c#  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## サービスを追加します。  
  
1.  TestAsyncPackage.cs で、削除、 `Initialize()` メソッドをオーバーライドして、 `InitializeAsync()` メソッドです。 サービスを追加し、サービスを作成するコールバック メソッドを追加します。 サービスを追加する非同期の初期化子の例を次に示します。  
  
    ```  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
2.  Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll への参照を追加します。  
  
3.  作成して、サービスを返す非同期メソッドとして、コールバック メソッドを実装します。  
  
    ```c#  
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        STextWriterService service = null;  
        await System.Threading.Tasks.Task.Run(() => {  
                    service = new TextWriterService(this);  
             });  
  
        return service;  
    }  
  
    ```  
  
## サービスを使用します。  
 今すぐサービスを取得し、そのメソッドを使用できます。  
  
1.  初期化子は、この説明しますが、サービスを使用する場合、サービス任意の場所を取得することができます。  
  
    ```c#  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     変更することを忘れないでください *\< userpath \>* ファイル名やコンピューターに意味のあるパスに\!  
  
2.  ビルドして、コードを実行します。 Visual Studio の実験用インスタンスが表示されたら、ソリューションを開きます。 これにより、自動読み込みを AsyncPackage です。 初期化子が実行された場合、指定した場所にファイルが見つかるはずです。  
  
## コマンド ハンドラーで非同期のサービスの使用  
 メニュー コマンドで非同期のサービスを使用する方法の例を次に示します。 他の非非同期メソッドで、サービスを使用するには、ここに示した手順を使用することができます。  
  
1.  プロジェクトにメニュー コマンドを追加します。 \(で、 **ソリューション エクスプ ローラー**, 、選択、プロジェクト ノードを右クリックし、 **追加\/\[新しい項目の\/機能拡張\/カスタム コマンド**.\) コマンド ファイルの名前 **TestAsyncCommand.cs**。  
  
2.  カスタム コマンドのテンプレートを再追加、 `Initialize()` コマンドを初期化するために TestAsyncPackage.cs ファイルへのメソッドです。 Initialize\(\) メソッドでは、コマンドを初期化する行をコピーします。 次のようになります。  
  
    ```  
    TestAsyncCommand.Initialize(this);  
    ```  
  
     この行に移動する、 `InitializeAsync()` AsyncPackageForService.cs ファイル内のメソッドです。 これは、非同期初期化でに切り替える必要がありますをメイン スレッドを使用してコマンドを初期化する前に <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>します。 今すぐに次のようになります。  
  
    ```c#  
  
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
  
3.  削除、 `Initialize()` メソッドです。  
  
4.  TestAsyncCommand.cs ファイルの検索、 `MenuItemCallback()` メソッドです。 メソッドの本体を削除します。  
  
5.  使用して、追加のステートメント。  
  
    ```  
    using System.IO;  
    ```  
  
6.  という非同期メソッドを追加 `GetAsyncService()`, とそのメソッドを使用してサービスを取得します。  
  
    ```c#  
    private async System.Threading.Tasks.Task GetAsyncService()  
    {  
        ITextWriterService textService =   
           this.ServiceProvider.GetService(typeof(STextWriterService))  
              as ITextWriterService;  
        // don’t forget to change <userpath> to a local path  
        await writer.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  このメソッドを呼び出して、 `MenuItemCallback()` メソッド。  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        GetAsyncService();  
    }  
  
    ```  
  
8.  ソリューションをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されたらに移動、 **ツール** メニューおよび \[検索対象の **呼び出す TestAsyncCommand** メニュー項目です。 をクリックすると、TextWriterService は、指定したファイルに書き込みます。 \(がなくても、ソリューションを開くに読み込むパッケージのコマンドを呼び出すもあるためです。\)  
  
## 参照  
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)