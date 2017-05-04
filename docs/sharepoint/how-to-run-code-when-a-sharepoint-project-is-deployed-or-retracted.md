---
title: "How to: Run Code When a SharePoint Project is Deployed or Retracted | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 353bbe6d-9b76-48ad-9fba-7e3c3712452f
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Run Code When a SharePoint Project is Deployed or Retracted
  SharePoint プロジェクトの配置時または取り消し時に別途タスクを実行する必要がある場合は、Visual Studio によって生成されるイベントを処理する方法があります。  詳細については、「[Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)」を参照してください。  
  
### SharePoint プロジェクトの配置時または取り消し時にコードを実行するには  
  
1.  プロジェクト項目の拡張機能、プロジェクトの拡張機能、または新しいプロジェクト項目の種類の定義を作成します。  詳細については、次のトピックを参照してください。  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  拡張機能で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> オブジェクトにアクセスします。  詳細については、「[How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)」を参照してください。  
  
3.  プロジェクト サービスの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> イベントと <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> イベントを処理します。  
  
4.  イベント ハンドラーで、<xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> パラメーターを使用して、現在の配置セッションに関する情報を取得します。  たとえば、現在の配置セッションにあるプロジェクトや、そのプロジェクトが配置中なのか取り消し中なのかを判別することができます。  
  
 プロジェクトの拡張機能で <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> イベントと <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> イベントを処理する方法を示すコード例を次に示します。  SharePoint プロジェクトの配置が開始され、完了すると、この拡張機能によって **\[出力\]** ウィンドウに追加のメッセージが書き込まれます。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/handleprojectdeploymentevents.vb#12)]  
  
## コードのコンパイル  
 この例は、次のアセンブリへの参照を必要とします。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 拡張機能の配置  
 拡張機能を配置するには、アセンブリと、拡張機能に同梱する必要のあるその他のファイルを提供するための [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  