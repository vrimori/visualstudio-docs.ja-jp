---
title: "How to: Execute a SharePoint Command"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint commands [SharePoint development in Visual Studio], executing"
ms.assetid: 2d1a163b-b601-4dac-bcea-328f24cb4d57
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# How to: Execute a SharePoint Command
  SharePoint ツールの拡張機能でサーバー オブジェクト モデルを使用する必要がある場合は、API を呼び出すためのカスタム *SharePoint コマンド*を作成する必要があります。  コマンドを定義し、SharePoint ツールの拡張機能を使用してコマンドを配置した後に、拡張機能でコマンドを実行して SharePoint サーバー オブジェクト モデルを呼び出すことができます。  <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> オブジェクトの ExecuteCommand メソッドのいずれかを使用して、コマンドを実行します。  
  
 SharePoint コマンドの用途の詳細については、「[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)」を参照してください。  
  
### SharePoint コマンドを実行するには  
  
1.  SharePoint ツールの拡張機能で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> オブジェクトを取得します。  <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> オブジェクトをどのように取得するかは、作成しようとしている拡張機能の種類によって異なります。  
  
    -   SharePoint プロジェクト システムの拡張機能の場合は、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> プロパティを使用します。  
  
         プロジェクト システムの拡張機能の詳細については、「[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)」を参照してください。  
  
    -   **サーバー エクスプローラー**の **\[SharePoint 接続\]** ノードの拡張機能の場合は <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> プロパティを使用します。  <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> オブジェクトを取得するには、<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> プロパティを使用します。  
  
         **サーバー エクスプローラー**の拡張機能の詳細については、「[Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)」を参照してください。  
  
    -   プロジェクト テンプレート ウィザードなど、SharePoint ツールの拡張機能には属さないコードの場合は、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> プロパティを使用します。  
  
         プロジェクト サービスの取得の詳細については、「[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)」を参照してください。  
  
2.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> オブジェクトの ExecuteCommand メソッドのいずれかを呼び出します。  実行するコマンド名を ExecuteCommand メソッドの 1 番目の引数に渡します。  コマンドにカスタム パラメーターがある場合には、そのパラメーターを ExecuteCommand メソッドの 2 番目の引数に渡します。  
  
     ExecuteCommand には複数のオーバーロードが存在し、それぞれ異なるコマンド シグネチャがサポートされています。  サポートされているシグネチャと、各シグネチャに対応するオーバーロードを次の表に示します。  
  
    |コマンド シグネチャ|対応する ExecuteCommand オーバーロード|  
    |----------------|---------------------------------|  
    |既定の <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> パラメーターのみ、戻り値なし。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |既定の <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> パラメーターのみ、戻り値あり。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |パラメーターは 2 つ \(既定の <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> パラメーターとカスタム パラメーター\)、戻り値なし。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |パラメーターは 2 つ、戻り値あり。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## 使用例  
 次のコード例は、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> オーバーロードを使用して、[How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md) に記載されている `Contoso.Commands.UpgradeSolution` コマンドを呼び出す方法を示します。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#6)]  
  
 この例で示す `Execute` メソッドは、カスタムの配置手順における <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> インターフェイスの <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> メソッドの実装です。  このコードのコンテキストを確認するには、「[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)」を参照してください。  
  
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> メソッドの呼び出しに関しては、次の点に注意してください。  
  
-   第 1 パラメーターには、呼び出すコマンドを指定します。  この文字列は、コマンド定義で <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> に渡す値と一致します。  
  
-   第 2 パラメーターは、コマンドのカスタムの第 2 パラメーターに渡す値です。  この場合、値は SharePoint サイトにアップグレードされる .wsp ファイルの完全パスです。  
  
-   このコードでは、暗黙の <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> パラメーターをコマンドに渡すことはしていません。  このパラメーターは、SharePoint プロジェクト システムの拡張機能から、または**サーバー エクスプローラー**の **\[SharePoint 接続\]** ノードの拡張機能からコマンドを呼び出すときに自動的に渡されます。  <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> インターフェイスを実装するプロジェクト テンプレート ウィザードなど、他のタイプのソリューションでは、このパラメーターは **null** です。  
  
## コードのコンパイル  
 この例では、Microsoft.VisualStudio.SharePoint アセンブリへの参照が必要です。  
  
## 参照  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  