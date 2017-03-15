---
title: "方法: サービスを取得 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f66c7e1f01c8d8eb69c6718314890bfb02cccc17
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-get-a-service"></a>方法: サービスを取得
多くの場合、さまざまな機能にアクセスする Visual Studio のサービスを取得する必要があります。 一般に、Visual Studio サービスは、使用できる&1; つまたは複数のインターフェイスを提供します。 ほとんどのサービスは、VSPackage から取得できます。  
  
 派生したすべての VSPackage<xref:Microsoft.VisualStudio.Shell.Package>とするサイトが正しく関連付けられたすべてのグローバル サービスに問い合わせることができます</xref:Microsoft.VisualStudio.Shell.Package>。 パッケージのクラスが実装されているため<xref:System.IServiceProvider>、パッケージから派生したすべての VSPackage でも、サービス プロバイダー</xref:System.IServiceProvider> 。  
  
 Visual Studio が読み込まれたときに、 <xref:Microsoft.VisualStudio.Shell.Package>、渡す、<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>オブジェクトを<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>の初期化中にメソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A></xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider></xref:Microsoft.VisualStudio.Shell.Package>。 これと呼ばれる*サイト設定*VSPackage します。 パッケージ クラスは、このサービス プロバイダーをラップし、提供、<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>サービスを取得するためのメソッドです</xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>。  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>初期化された VSPackage からサービスを取得します。  
  
1.  すべての Visual Studio 拡張機能は、拡張機能の資産を格納する VSIX 配置プロジェクトから開始します。 作成、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前の VSIX プロジェクト`GetServiceExtension`します。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**します。  
  
2.  という名前のカスタム コマンド項目テンプレートを今すぐ追加**GetServiceCommand**します。 **新しい項目の追加**ダイアログ ボックスに移動**Visual c#/機能拡張**を選択して**にカスタム コマンド**します。 **名**ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する**GetServiceCommand.cs**します。 カスタム コマンドを作成する方法の詳細についての[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  GetServiceCommand.cs、MenuItemCommand メソッドの本体を削除し、次のコードを追加します。  
  
    ```c#  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     このコードは SVsActivityLog サービスを取得し、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>、アクティビティ ログへの書き込みに使用できるインターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>にキャスト 例については、次を参照してください。[方法:、動作状況ログを使用して](../extensibility/how-to-use-the-activity-log.md)します。  
  
4.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
5.  実験用インスタンスの ツール メニューの検索、**呼び出す GetServiceCommand**  ボタンをクリックします。 このボタンをクリックするとは、というメッセージ ボックスが表示されます**アクティビティ ログ サービスを検出します。**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>ツール ウィンドウまたはコントロールのコンテナーからのサービスの取得  
 場合によって、ツール ウィンドウからサービスを取得またはサービスが認識していないサービス プロバイダーに配置されているか、または配置されていないするコンテナーを制御する必要があります。 たとえば、コントロール内のアクティビティ ログに書き込むことができます。  
  
 静的な<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>メソッドが初めてから派生したすべての VSPackage に初期化される、キャッシュされたサービス プロバイダーに依存している<xref:Microsoft.VisualStudio.Shell.Package>が配置されています</xref:Microsoft.VisualStudio.Shell.Package></xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>。  
  
 VSPackage コンス トラクターが呼び出されるため、VSPackage を配置する前に、グローバル サービス通常ご利用いただけませんから VSPackage コンス トラクター内で。 参照してください[方法: サービスのトラブルシューティングを行う](../extensibility/how-to-troubleshoot-services.md)問題を回避します。  
  
 ツール ウィンドウまたは他の非 VSPackage 要素内のサービスを取得するための方法の例を次に示します。  
  
```c#  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>DTE オブジェクトからのサービスの取得  
 サービスを取得することもできます<xref:EnvDTE.DTEClass>オブジェクト。</xref:EnvDTE.DTEClass> 。 ただし、取得する必要あります DTE オブジェクト サービスとして VSPackage からを呼び出すか、静的な<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>。  
  
 DTE オブジェクトを実装して<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>、使用できる<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.</xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>を使用してサービスを照会する</xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
 DTE オブジェクトからサービスを取得する方法を次に示します。  
  
```c#  
// Start with the DTE object, for example:   
// using EnvDTE;  
// DTE dte = (DTE)GetService(typeof(DTE));  
  
ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
if (sp != null)  
{  
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log != null)  
    {   
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [方法: サービスを提供](../extensibility/how-to-provide-a-service.md)   
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)   
 [サービスの基礎](../extensibility/internals/service-essentials.md)
