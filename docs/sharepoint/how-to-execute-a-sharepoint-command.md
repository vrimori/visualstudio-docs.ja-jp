---
title: '方法: SharePoint コマンドを実行します |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d6e529420db8261e87c856e2fc80ef436bbc3e73
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53953119"
---
# <a name="how-to-execute-a-sharepoint-command"></a>方法: SharePoint コマンドを実行します。
  SharePoint ツール拡張機能で、サーバー オブジェクト モデルを使用する場合は、カスタムを作成する必要があります*SharePoint コマンド*API を呼び出します。 コマンドを定義し、SharePoint ツール拡張機能で、デプロイ後、拡張機能は、SharePoint サーバー オブジェクト モデルを呼び出すコマンドを実行できます。 コマンドを実行するには、ExecuteCommand メソッドのいずれかの操作を使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>オブジェクト。  
  
 SharePoint コマンドの目的に関する詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)します。  
  
### <a name="to-execute-a-sharepoint-command"></a>SharePoint コマンドを実行するには  
  
1.  SharePoint ツール拡張機能では、取得、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>オブジェクト。 取得する方法、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>オブジェクトを作成する拡張機能の種類によって異なります。  
  
    -   SharePoint プロジェクト システムの拡張機能で使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A>プロパティ。  
  
         プロジェクト システムの拡張機能の詳細については、次を参照してください。 [SharePoint プロジェクト システムを拡張](../sharepoint/extending-the-sharepoint-project-system.md)します。  
  
    -   拡張機能で、 **SharePoint 接続**ノード**サーバー エクスプ ローラー**を使用して、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A>プロパティ。 取得する、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext>オブジェクトを使用して、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A>プロパティ。  
  
         詳細については**サーバー エクスプ ローラー** 、拡張機能を参照してください[サーバー エクスプ ローラーで、SharePoint 接続 ノードを拡張](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)します。  
  
    -   プロジェクト テンプレートのウィザードなど、SharePoint ツールの拡張機能の一部でないコードで使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>プロパティ。  
  
         プロジェクト サービスを取得する方法についての詳細については、次を参照してください。 [SharePoint プロジェクト サービスを使用して、](../sharepoint/using-the-sharepoint-project-service.md)します。  
  
2.  ExecuteCommand 方法の 1 つを呼び出して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>オブジェクト。 ExecuteCommand メソッドの最初の引数を実行するコマンドの名前を渡します。 場合は、コマンドは、カスタム パラメーターを持ち、ExecuteCommand メソッドの 2 番目の引数は、そのパラメーターを渡します。  
  
     各コマンドがサポートされている署名に対して異なる ExecuteCommand オーバー ロードがあります。 次の表は、サポートされている署名と署名に使用するどのオーバー ロードを示します。  
  
    |コマンドの署名|ExecuteCommand のオーバー ロードを使用するには|  
    |-----------------------|------------------------------------|  
    |コマンドが既定値のみ<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>パラメーターと戻り値はありません。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |コマンドが既定値のみ<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>パラメーターと戻り値。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |コマンドが 2 つのパラメーター (既定値<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>パラメーターとカスタム パラメーター) と戻り値はありません。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |コマンドは、2 つのパラメーターと戻り値にします。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>例  
 次のコード例は、使用する方法を示します、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>オーバー ロードを呼び出す、`Contoso.Commands.UpgradeSolution`で説明されているコマンド[方法。SharePoint コマンドを作成する](../sharepoint/how-to-create-a-sharepoint-command.md)します。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 `Execute`この例に示すようにメソッドの実装は、<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A>のメソッド、<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>インターフェイスでカスタムの配置手順。 例のコンテキストでは、このコードを表示するには、次を参照してください。[チュートリアル。SharePoint プロジェクトのカスタム配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)です。  
  
 次の詳細への呼び出しに注意してください、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>メソッド。  
  
-   最初のパラメーターは、呼び出そうとコマンドを識別します。 この文字列に渡す値に一致する、<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>コマンド定義。  
  
-   2 番目のパラメーターは、コマンドのカスタムの 2 番目のパラメーターに渡す値です。 この例では、完全なパスは、 *.wsp*ファイルを SharePoint サイトにアップグレードしています。  
  
-   コードは、暗黙的な渡さない<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>パラメーターをコマンド。 このパラメーターに渡されるコマンドは、自動的に SharePoint プロジェクト システムの拡張機能またはの拡張機能から、コマンドを呼び出すときに、 **SharePoint 接続**ノード**サーバー エクスプ ローラー**. 他の種類のソリューション、プロジェクト テンプレートのウィザードを実装するように、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>インターフェイスでは、このパラメーターは**null**します。  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 この例では、Microsoft.VisualStudio.SharePoint アセンブリへの参照が必要です。  
  
## <a name="see-also"></a>関連項目
 [SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [方法: SharePoint コマンドを作成します。](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [チュートリアル: Web パーツを表示するサーバー エクスプ ローラーを拡張します。](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
