---
title: '方法: サービスを取得 |Microsoft Docs'
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
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea5f3be4f5792213c5625e4c287195161eb1dd62
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785067"
---
# <a name="how-to-get-a-service"></a>方法: サービスを取得
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

多くの場合、さまざまな機能にアクセスする Visual Studio サービスを取得する必要があります。 一般に、Visual Studio service は、使用できる 1 つまたは複数のインターフェイスを提供します。 ほとんどのサービスは、VSPackage から取得できます。  
  
 派生したすべての VSPackage<xref:Microsoft.VisualStudio.Shell.Package>を正しく配置されていますが、任意のグローバル サービスを要求できます。 パッケージ クラスが実装されているため<xref:System.IServiceProvider>、パッケージから派生したすべての VSPackage は、サービス プロバイダーもです。  
  
 Visual Studio が読み込まれたら、 <xref:Microsoft.VisualStudio.Shell.Package>、合格、<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>オブジェクトを<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>メソッドの初期化中にします。 これは呼び出されます*サイト設定*VSPackage です。 パッケージ クラスは、このサービス プロバイダーをラップし、提供、<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>サービスを取得するためのメソッド。  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>初期化の VSPackage からサービスを取得します。  
  
1.  すべての Visual Studio 拡張機能は、拡張機能資産が含まれる VSIX 配置プロジェクトで開始します。 作成、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]という名前の VSIX プロジェクト`GetServiceExtension`します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**します。  
  
2.  という名前のカスタム コマンド項目テンプレートを追加するようになりました**GetServiceCommand**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択と**カスタム コマンド**。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイル名を変更して**GetServiceCommand.cs**します。 詳細については、カスタム コマンドを作成する方法についての[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  GetServiceCommand.cs、MenuItemCommand メソッドの本体を削除し、次のコードを追加します。  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     このコードは、SVsActivityLog サービスを取得しにキャスト、<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>インターフェイスで、アクティビティ ログに書き込むことができます。 例については、次を参照してください。[方法: アクティビティ ログを使用して、](../extensibility/how-to-use-the-activity-log.md)します。  
  
4.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
5.  実験用インスタンスの [ツール] メニューの検索、**呼び出す GetServiceCommand**ボタンをクリックします。 このボタンをクリックするとは、ことを示すメッセージ ボックスが表示されます**アクティビティ ログのサービスを検出します。**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>ツール ウィンドウまたはコントロールのコンテナーからサービスを取得します。  
 場合によっては、ツール ウィンドウからサービスを取得するサービスを認識しませんが、サービス プロバイダーをコンテナーに配置されているか、またはしない配置されているコンテナーを制御したり必要があります。 たとえば、コントロール内からアクティビティ ログに書き込む可能性があります。  
  
 静的な<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>メソッドが初めてから派生したすべての VSPackage に初期化される、キャッシュされたサービス プロバイダーに依存<xref:Microsoft.VisualStudio.Shell.Package>が配置されています。  
  
 VSPackage コンス トラクターが呼び出されたは、VSPackage を配置する前に、グローバル サービスは、VSPackage のコンス トラクター内から、通常は利用されません。 参照してください[方法: サービスのトラブルシューティングを行う](../extensibility/how-to-troubleshoot-services.md)問題を回避します。  
  
 ツール ウィンドウまたはその他の VSPackage ではない要素で、サービスを取得する方法の例を次に示します。  
  
```csharp  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>DTE オブジェクトからのサービスの取得  
 サービスを取得することもできます。<xref:EnvDTE.DTEClass>オブジェクト。 ただし、取得する必要あります DTE オブジェクトをサービスとして VSPackage から、または静的なを呼び出すことによって<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>メソッド。  
  
 DTE オブジェクトを実装して<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>、使用できるを使用してサービスを照会する<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [方法: サービスを提供](../extensibility/how-to-provide-a-service.md)   
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)   
 [サービスの基本情報](../extensibility/internals/service-essentials.md)

