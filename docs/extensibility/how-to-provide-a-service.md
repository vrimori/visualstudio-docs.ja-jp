---
title: "方法: サービスを提供 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0adc9f69f1b0e873d2e1f38c9317070dc0d6a08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-a-service"></a>方法: サービスを提供
VSPackage では、その他の Vspackage を使用するサービスを提供できます。 サービスを提供するには、VSPackage は Visual Studio で、サービスの登録し、サービスの追加する必要があります。  
  
 <xref:Microsoft.VisualStudio.Shell.Package>クラスを実装する<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>と<xref:System.ComponentModel.Design.IServiceContainer>です。 <xref:System.ComponentModel.Design.IServiceContainer>要求時にサービスを提供するコールバック メソッドが含まれています。  
  
 サービスの詳細については、次を参照してください。[サービス Essentials](../extensibility/internals/service-essentials.md)です。  
  
> [!NOTE]
>  VSPackage が読み込まれますが、Visual Studio は VSPackage によって提供されるサービスに対するすべての要求を配信するまで待機します。 これらのサービスに対する新しい要求はできません。 明示的に呼び出す必要がありますいない、<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>をアンロードするときに、サービスを取り消す方法です。  
  
#### <a name="implementing-a-service"></a>サービスを実装します。  
  
1.  VSIX プロジェクトを作成 (**ファイル/新しい/プロジェクト/Visual c#/Extensiblity/VSIX プロジェクト**)。  
  
2.  VSPackage をプロジェクトに追加します。 プロジェクト ノードを選択、**ソリューション エクスプ ローラー** ] をクリック**追加/[新しい項目/Visual c# アイテム/機能拡張/Visual Studio パッケージ**です。  
  
3.  サービスを実装するのには、次の 3 種類の作成が必要です。  
  
    -   サービスを記述したインターフェイスです。 これらのインターフェイスの多くは、空、つまりがないメソッド。  
  
    -   サービス インターフェイスを表すインターフェイスです。 このインターフェイスには、実装するメソッドが含まれています。  
  
    -   サービスと、サービス インターフェイスの両方を実装するクラス。  
  
     次の例では、3 種類の非常に基本的な実装を示します。 サービス クラスのコンス トラクターは、サービス プロバイダーを設定する必要があります。  
  
    ```csharp  
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
  
### <a name="registering-a-service"></a>サービスを登録します。  
  
1.  サービスを登録するには追加、<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>サービスを提供する VSPackage にします。 次に例を示します。  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     この属性を登録`SMyService`Visual Studio とします。  
  
    > [!NOTE]
    >  同じ名前の別のサービスを置き換えるサービスを登録するには、使用、<xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>です。 注そのサービスの 1 つだけのオーバーライドを許可します。  
  
### <a name="adding-a-service"></a>サービスの追加  
  
1.  VSPackage の初期化子で、サービスを追加し、サービスを作成するコールバック メソッドを追加します。 ここでは、変更するのには、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>メソッド。  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  作成して、サービスが返さか作成できない場合は null にする必要がある、コールバック メソッドを実装します。  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio は、サービスを提供する要求を拒否することができます。 別の VSPackage は、サービスを既に提供している場合に行われます。  
  
3.  これで、サービスを取得し、そのメソッドを使用できます。 これを初期化子で説明しますが、サービスを使用する場合、サービス任意の場所を取得することができます。  
  
    ```csharp  
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
  
     値`helloString`「こんにちは」にする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [方法: サービスを取得](../extensibility/how-to-get-a-service.md)   
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)   
 [サービスの基本情報](../extensibility/internals/service-essentials.md)