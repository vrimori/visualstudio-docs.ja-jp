---
title: "How to: Run Code When Deployment Steps are Executed | Microsoft Docs"
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
ms.assetid: 6b0a52e5-e0ba-41bc-9e8a-1013e51fd3ba
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# How to: Run Code When Deployment Steps are Executed
  SharePoint プロジェクトの配置手順に関して別途タスクを実行する必要がある場合は、Visual Studio が個々の配置手順を実行する前と後に SharePoint プロジェクト項目によって生成されるイベントを処理する方法があります。  詳細については、「[Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)」を参照してください。  
  
### 配置手順を実行するときにコードを実行するには  
  
1.  プロジェクト項目の拡張機能、プロジェクトの拡張機能、または新しいプロジェクト項目の種類の定義を作成します。  詳細については、次のトピックを参照してください。  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  拡張機能で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> オブジェクト \(プロジェクト項目の拡張機能またはプロジェクトの拡張機能\) または <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> オブジェクト \(新しいプロジェクト項目の種類の定義\) の <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> イベントおよび <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> を処理します。  
  
3.  イベント ハンドラーで、<xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> パラメーターおよび <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> パラメーターを使用して、配置手順に関する情報を取得します。  たとえば、実行されている配置手順や、ソリューションが配置中なのか取り消し中なのかを判別することができます。  
  
## 例  
 リスト インスタンス プロジェクト項目の拡張機能で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> イベントおよび <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> イベントを処理する方法を次のコード例に示します。  この拡張機能は、ソリューションの配置中および取り消し中、Visual Studio によってアプリケーション プールがリサイクルされると、**\[出力\]** ウィンドウに追加のメッセージを出力します。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/handledeploymentstepevents.cs#4)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/handledeploymentstepevents.vb#4)]  
  
## コードのコンパイル  
 この例は、次のアセンブリへの参照を必要とします。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 拡張機能の配置  
 拡張機能を配置するには、アセンブリと、拡張機能に同梱する必要のあるその他のファイルを提供するための [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [How to: Run Code When a SharePoint Project is Deployed or Retracted](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  