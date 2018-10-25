---
title: '方法: サービスを提供 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b9dc7d2ef8aabab628f13ce9648e0fa5dc1f3b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845096"
---
# <a name="how-to-provide-a-service"></a>方法: サービスを提供
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage では、その他の Vspackage を使用できるサービスを提供できます。 サービスを提供するには、VSPackage は Visual Studio でサービスを登録して、サービスの追加する必要があります。  
  
 <xref:Microsoft.VisualStudio.Shell.Package>両方を実装するクラス<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>と<xref:System.ComponentModel.Design.IServiceContainer>します。 <xref:System.ComponentModel.Design.IServiceContainer> オンデマンドでサービスを提供するコールバック メソッドが含まれています。  
  
 サービスの詳細については、次を参照してください。 [Service Essentials](../extensibility/internals/service-essentials.md)します。  
  
> [!NOTE]
>  VSPackage は、アンロードしようとしていますが、Visual Studio は、VSPackage が提供するサービスのすべての要求が配信されたまでを待機します。 これらのサービスに対する新しい要求は許可されません。 明示的に呼び出す必要がありますいない、<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>をアンロードするときに、サービスを取り消すメソッド。  
  
#### <a name="implementing-a-service"></a>サービスの実装  
  
1. VSIX プロジェクトを作成 (**ファイル/新規、プロジェクト/Visual c#/呼び出/VSIX プロジェクト**)。  
  
2. VSPackage をプロジェクトに追加します。 プロジェクト ノードを選択、**ソリューション エクスプ ローラー**クリック**追加/新しい項目/Visual c# アイテム/機能拡張/Visual Studio パッケージ**。  
  
3. サービスを実装するには次の 3 つの種類を作成する必要があります。  
  
   - サービスを表すインターフェイスです。 これらのインターフェイスの多くは、空、つまり、どのメソッド。  
  
   - サービス インターフェイスを記述するインターフェイスです。 このインターフェイスには、実装するメソッドが含まれています。  
  
   - サービスと、サービス インターフェイスの両方を実装するクラス。  
  
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
  
### <a name="adding-a-service"></a>サービスの追加  
  
1.  1.  VSPackage の初期化子では、サービスを追加し、サービスを作成するコールバック メソッドを追加します。 に対する変更をここでは、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>メソッド。  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  作成し、サービスを返す、または作成できない場合は null にする必要がありますコールバック メソッドを実装します。  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio では、サービスを提供する要求を拒否できます。 そうなった場合、別の VSPackage に、サービスが既に用意されています。  
  
3.  これで、サービスを取得し、そのメソッドを使用できます。 これで、初期化子を説明しますが、サービスを使用する任意の場所サービスを取得することができます。  
  
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

