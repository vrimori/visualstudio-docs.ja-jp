---
title: "方法: サービスの取得 |Microsoft ドキュメント"
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
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dd51497bb73981ca81623ad495edc9561e85d3da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-a-service"></a>方法: サービスを取得
多くの場合、さまざまな機能にアクセスする Visual Studio サービスを取得する必要があります。 一般に、Visual Studio サービスは、使用できる 1 つまたは複数のインターフェイスを提供します。 ほとんどのサービスは、VSPackage から取得できます。  
  
 派生した任意の VSPackage<xref:Microsoft.VisualStudio.Shell.Package>を正しく配置されているが、すべてのグローバル サービスに尋ねることができます。 パッケージのクラスが実装されているため<xref:System.IServiceProvider>、パッケージから派生した任意の VSPackage は、サービス プロバイダーもです。  
  
 Visual Studio を読み込むときに、 <xref:Microsoft.VisualStudio.Shell.Package>、渡します、<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>オブジェクトを<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>の初期化中にメソッドです。 これと呼ばれる*サイト設定*VSPackage です。 パッケージのクラスは、このサービス プロバイダーをラップし、提供、<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>サービスを取得するためのメソッドです。  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>初期化の VSPackage からサービスを取得します。  
  
1.  すべての Visual Studio 拡張機能は、資産を拡張機能を含んでいる VSIX 配置プロジェクトを開始します。 作成、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前の VSIX プロジェクト`GetServiceExtension`です。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c# > Extensibility**です。  
  
2.  という名前のカスタム コマンド項目テンプレートを追加するようになりました**GetServiceCommand**です。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c# > 機能拡張**選択と**にカスタム コマンド**です。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する**GetServiceCommand.cs**です。 詳細については、カスタム コマンドを作成する方法についての[メニュー コマンドを使用して、拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  GetServiceCommand.cs で MenuItemCommand メソッドの本体を削除し、次のコードを追加します。  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     このコードは SVsActivityLog サービスを取得し、キャスト、<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>インターフェイスで、アクティビティ ログに書き込むために使用できます。 例については、次を参照してください。[する方法: アクティビティ ログを使用して](../extensibility/how-to-use-the-activity-log.md)です。  
  
4.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
5.  実験用インスタンスの [ツール] メニューの検索、**呼び出す GetServiceCommand**ボタンをクリックします。 このボタンをクリックすると表示されているメッセージ ボックスを表示する必要があります**アクティビティ ログ サービスを検出します。**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>ツール ウィンドウまたはコントロールのコンテナーからのサービスの取得  
 ツール ウィンドウからサービスを取得またはサービスが認識していないサービス プロバイダーのコンテナーに配置されているか、または配置されていないするコンテナーを制御する必要があります。 たとえば、コントロール内のアクティビティ ログに書き込むことができます。  
  
 静的な<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>メソッドが初めてから派生した任意の VSPackage は初期化されているキャッシュされたサービス プロバイダーに依存<xref:Microsoft.VisualStudio.Shell.Package>が配置されています。  
  
 VSPackage のコンス トラクターが呼び出されるため、VSPackage が配置される前に、グローバル サービス通常ご利用いただけませんから VSPackage コンス トラクター内で。 参照してください[する方法: サービスのトラブルシューティングを行う](../extensibility/how-to-troubleshoot-services.md)問題を回避します。  
  
 ツール ウィンドウまたはその他の VSPackage ではない要素で、サービスを取得する方法の例を次に示します。  
  
```csharp  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>DTE オブジェクトからサービスを取得します。  
 サービスを取得することもできます。<xref:EnvDTE.DTEClass>オブジェクト。 ただし、取得する必要あります DTE オブジェクトをサービスとして、VSPackage または静的なを呼び出すことによって<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>メソッドです。  
  
 DTE オブジェクトを実装する<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>、使用できるクエリを使用してサービスの実行に<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>です。  
  
 DTE オブジェクトからサービスを取得する方法を次に示します。  
  
```csharp  
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
  
## <a name="see-also"></a>参照  
 [方法: サービスを提供](../extensibility/how-to-provide-a-service.md)   
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)   
 [サービスの基本情報](../extensibility/internals/service-essentials.md)