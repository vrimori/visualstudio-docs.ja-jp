---
title: '方法: サービスを提供 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cbad09a19aeaf297505de215566b14df067c760a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639589"
---
# <a name="how-to-provide-a-service"></a>方法: サービスを提供
VSPackage では、その他の Vspackage を使用できるサービスを提供できます。 サービスを提供するには、VSPackage は Visual Studio でサービスを登録して、サービスの追加する必要があります。  
  
 <xref:Microsoft.VisualStudio.Shell.Package>両方を実装するクラス<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>と<xref:System.ComponentModel.Design.IServiceContainer>します。 <xref:System.ComponentModel.Design.IServiceContainer> オンデマンドでサービスを提供するコールバック メソッドが含まれています。  
  
 サービスの詳細については、次を参照してください。 [essentials サービス](../extensibility/internals/service-essentials.md)します。  
  
> [!NOTE]
>  VSPackage は、アンロードしようとしていますが、Visual Studio は、VSPackage が提供するサービスのすべての要求が配信されたまでを待機します。 これらのサービスに対する新しい要求は許可されません。 明示的に呼び出す必要がありますいない、<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>をアンロードするときに、サービスを取り消すメソッド。  
  
## <a name="implement-a-service"></a>サービスを実装します。  
  
1.  VSIX プロジェクトを作成 (**ファイル** > **新規** > **プロジェクト** > **Visual c#**  > **拡張** > **VSIX プロジェクト**)。  
  
2.  VSPackage をプロジェクトに追加します。 プロジェクト ノードを選択、**ソリューション エクスプ ローラー**クリック**追加** > **新しい項目の** > **Visual c# アイテム**  > **拡張** > **Visual Studio パッケージ**します。  
  
3.  サービスを実装するには次の 3 つの種類を作成する必要があります。  
  
    -   サービスを表すインターフェイスです。 これらのインターフェイスの多くは、空、つまり、どのメソッド。  
  
    -   サービス インターフェイスを記述するインターフェイスです。 このインターフェイスには、実装するメソッドが含まれています。  
  
    -   サービスと、サービス インターフェイスの両方を実装するクラス。  
  
     次の例では、3 種類の基本的な実装を示します。 サービス クラスのコンス トラクターは、サービス プロバイダーを設定する必要があります。  
  
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
  
### <a name="register-a-service"></a>サービスを登録します。  
  
1.  サービスを登録するには、追加、<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>サービスを提供する VSPackage にします。 次に例を示します。  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     この属性を登録`SMyService`Visual Studio を使用します。  
  
    > [!NOTE]
    >  同じ名前の別のサービスを置換するサービスを登録するには、使用、<xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>します。 注サービスの 1 つだけそのオーバーライドを許可します。  
  
### <a name="add-a-service"></a>サービスを追加します。  
  
1.  VSPackage の初期化子では、サービスを追加し、サービスを作成するコールバック メソッドを追加します。 に対する変更をここでは、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>メソッド。  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  作成し、サービスを返す、または作成できない場合は null にする必要がありますコールバック メソッドを実装します。  
  
    ```csharp  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new MyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio では、サービスを提供する要求を拒否できます。 そうなった場合、別の VSPackage に、サービスが既に用意されています。  
  
3.  これで、サービスを取得し、そのメソッドを使用できます。 サービスを使用して、初期化子で次の例を示していますが、サービスを使用する任意の場所サービスを取得することができます。  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.Goodbye();  
  
        base.Initialize();  
    }  
    ```  
  
     値`helloString`「こんにちは」にする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [方法: サービスを取得](../extensibility/how-to-get-a-service.md)   
 [使用し、サービスを提供](../extensibility/using-and-providing-services.md)   
 [サービスの基本情報](../extensibility/internals/service-essentials.md)
