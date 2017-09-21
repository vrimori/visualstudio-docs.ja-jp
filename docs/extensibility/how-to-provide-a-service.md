---
title: "方法: サービスを提供 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "提供するサービス"
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# 方法: サービスを提供
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackage では、その他の VSPackages に使用できるサービスを提供できます。 サービスを提供するには、VSPackage は Visual Studio でサービスを登録し、サービスを追加する必要があります。  
  
 <xref:Microsoft.VisualStudio.Shell.Package> クラスでは、両方を実装して <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> と <xref:System.ComponentModel.Design.IServiceContainer>です。<xref:System.ComponentModel.Design.IServiceContainer> 要求時にサービスを提供するコールバック メソッドが含まれています。  
  
 サービスの詳細については、次を参照してください。 [サービスの基礎](../extensibility/internals/service-essentials.md) します。  
  
> [!NOTE]
>  VSPackage が読み込まれますが、Visual Studio は、VSPackage を提供するサービスのすべての要求が送信されたまでを待機します。 これらのサービスに対する新しい要求は許可しません。 明示的に呼び出す必要がありません、 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> をアンロードするときに、サービスを取り消す方法です。  
  
#### サービスを実装します。  
  
1.  VSIX プロジェクトを作成する \(**ファイル\/\[新しい\/プロジェクト\/Visual c\#\/Extensiblity\/VSIX プロジェクト**\)。  
  
2.  VSPackage をプロジェクトに追加します。 プロジェクト ノードを選択して、 **ソリューション エクスプ ローラー** \] をクリック **追加\/\[新しい項目\/Visual c\# アイテム\/機能拡張\/Visual Studio パッケージ**します。  
  
3.  サービスを実装するには、次の 3 つの種類を作成する必要があります。  
  
    -   サービスを記述したインターフェイスです。 これらのインターフェイスの多くは、空、つまりがないメソッド。  
  
    -   サービス インターフェイスについて説明するインターフェイス。 このインターフェイスには、実装されるメソッドが含まれています。  
  
    -   サービスと、サービス インターフェイスの両方を実装するクラス。  
  
     次の例では、次の 3 つの種類の非常に基本的な実装を示します。 サービス クラスのコンス トラクターは、サービス プロバイダーを設定する必要があります。  
  
    ```c#  
    public class MyService : SMyService, IMyService  
    {  
        private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;  
        private string myString;  
        public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)  
        {  
            Trace.WriteLine(  
                   "Constructing a new instance of MyService");  
            serviceProvider = sp;  
        }  
        public void Hello()  
        {  
            myString = "hello";  
        }  
        public string Goodbye()  
        {  
           return "goodbye";  
        }  
    }  
    public interface SMyService  
    {  
    }  
    public interface IMyService  
    {  
        void Hello();  
        string Goodbye();  
    }  
  
    ```  
  
### サービスを登録します。  
  
1.  サービスを登録するには、追加、 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> サービスを提供する VSPackage にします。 次に例を示します。  
  
    ```c#  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     この属性を登録 `SMyService` Visual Studio を使用します。  
  
    > [!NOTE]
    >  別のサービスを同じ名前に置き換え、サービスを登録するには、使用、 <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>です。 注サービスの 1 つだけそのオーバーライドを許可します。  
  
### サービスを追加します。  
  
1.  1.	VSPackage 初期化子では、サービスを追加し、サービスを作成するコールバック メソッドを追加します。 ここでは、変更を <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> メソッド。  
  
    ```c#  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  作成し、サービスを返すまたは作成できない場合は null にする必要がありますコールバック メソッドを実装します。  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio では、サービスを提供する要求を拒否できます。 では、サービスが別の VSPackage で提供されている場合。  
  
3.  今すぐサービスを取得し、そのメソッドを使用できます。 初期化子は、この説明しますが、サービスを使用する場合、サービス任意の場所を取得することができます。  
  
    ```c#  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     値 `helloString` 「こんにちは」にする必要があります。  
  
## 参照  
 [方法: サービスを取得](../Topic/How%20to:%20Get%20a%20Service.md)   
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)   
 [サービスの基礎](../extensibility/internals/service-essentials.md)