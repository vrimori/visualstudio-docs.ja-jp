---
title: '方法: SharePoint コマンドを実行 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 824a747d9253817e1f188730996dac707b3e5ee5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-execute-a-sharepoint-command"></a>方法: SharePoint コマンドを実行する
  を SharePoint ツール拡張機能で、サーバー オブジェクト モデルを使用する場合は、カスタムを作成する必要があります*SharePoint コマンド*API を呼び出すためです。 コマンドを定義して、SharePoint ツールの拡張機能を展開した後に、拡張機能は、SharePoint サーバー オブジェクト モデルへの呼び出しをコマンドを実行できます。 コマンドを実行するには、ExecuteCommand メソッドのいずれかの操作を使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>オブジェクト。  
  
 SharePoint コマンドの目的に関する詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)です。  
  
### <a name="to-execute-a-sharepoint-command"></a>SharePoint コマンドを実行するには  
  
1.  SharePoint ツール拡張機能では、取得、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>オブジェクト。 取得する方法、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>オブジェクトを作成する拡張機能の種類に依存します。  
  
    -   SharePoint プロジェクト システムの拡張機能を使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A>プロパティです。  
  
         プロジェクト システムの拡張機能の詳細については、次を参照してください。 [SharePoint プロジェクト システムを拡張する](../sharepoint/extending-the-sharepoint-project-system.md)です。  
  
    -   拡張機能に、 **SharePoint 接続**内のノード**サーバー エクスプ ローラー**を使用して、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A>プロパティです。 取得する、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext>オブジェクトを使用して、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A>プロパティです。  
  
         詳細については**サーバー エクスプ ローラー**拡張機能を参照してください[サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張する](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)です。  
  
    -   プロジェクト テンプレート ウィザードなどの SharePoint ツールの拡張機能の一部ではないコードで使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>プロパティです。  
  
         プロジェクトのサービスの取得の詳細については、次を参照してください。 [SharePoint プロジェクト サービスを使用して](../sharepoint/using-the-sharepoint-project-service.md)です。  
  
2.  ExecuteCommand 方法の 1 つを呼び出して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>オブジェクト。 ExecuteCommand メソッドの最初の引数を実行するコマンドの名前を渡します。 場合は、コマンドは、カスタム パラメーターを持ち、そのパラメーター ExecuteCommand メソッドの 2 番目の引数を渡すことです。  
  
     サポートされているコマンドのシグネチャごとの異なる ExecuteCommand オーバー ロードがあります。 次の表は、サポートされている署名と各署名に使用するオーバー ロードを一覧表示します。  
  
    |コマンドの署名|ExecuteCommand のオーバー ロードを使用するには|  
    |-----------------------|------------------------------------|  
    |既定値のみがコマンドにある<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>パラメーターと戻り値はありません。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |既定値のみがコマンドにある<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>パラメーターと戻り値。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |コマンドが 2 つのパラメーター (既定値<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>パラメーターとカスタム パラメーター) と戻り値はありません。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |コマンドは、2 つのパラメーターと戻り値がします。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>例  
 次のコード例を使用する方法を示しています、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>のオーバー ロードを呼び出して、`Contoso.Commands.UpgradeSolution`に記載されているコマンド[する方法: SharePoint コマンドを作成する](../sharepoint/how-to-create-a-sharepoint-command.md)です。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 `Execute`この例に示すようにメソッドの実装は、<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A>のメソッド、<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>カスタム配置手順のインターフェイスです。 このコード例のコンテキストを参照してください[チュートリアル: SharePoint プロジェクトのカスタム配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)です。  
  
 呼び出しに関する以下の詳細に注意してください、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>メソッド。  
  
-   最初のパラメーターは、呼び出しに使用するコマンドを識別します。 この文字列に渡す値に一致する、<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>コマンド定義にします。  
  
-   2 番目のパラメーターは、コマンドのカスタムの 2 番目のパラメーターに渡す値です。 この例では、SharePoint サイトにアップグレードされている .wsp ファイルの完全なパスを勧めします。  
  
-   コードは、暗黙的に渡さない<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>パラメーターをコマンド。 このパラメーターに渡されるコマンドは、自動的に SharePoint プロジェクト システムの拡張機能またはの拡張機能から、コマンドを呼び出すときに、 **SharePoint 接続**内のノード**サーバー エクスプ ローラー**. その他の種類のソリューション、プロジェクト テンプレートのウィザードを実装するように、<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>このパラメーターは、インターフェイス、 **null**です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、Microsoft.VisualStudio.SharePoint アセンブリへの参照が必要です。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint オブジェクト モデルの呼び出し](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [方法: SharePoint コマンドを作成します。](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [チュートリアル: サーバー エクスプローラーを拡張して Web パーツを表示する](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  