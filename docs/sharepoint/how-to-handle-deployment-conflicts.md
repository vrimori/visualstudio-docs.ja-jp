---
title: "How to: Handle Deployment Conflicts | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 8e545873-3fed-46cf-a95f-27b5fc0d5f83
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# How to: Handle Deployment Conflicts
  独自のコードを使用して SharePoint プロジェクト項目の配置競合を処理できます。  たとえば、現在のプロジェクト項目に含まれるファイルが配置場所に既に存在するかどうかを判断し、現在のプロジェクトの項目を配置する前に、配置されているファイルを削除します。  配置競合の詳細については、「[Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)」を参照してください。  
  
### 配置競合を処理するには  
  
1.  プロジェクト項目の拡張機能、プロジェクトの拡張機能、または新しいプロジェクト項目の種類の定義を作成します。  詳細については、次のトピックを参照してください。  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  拡張機能で、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> オブジェクト \(プロジェクト項目の拡張機能またはプロジェクトの拡張機能\) または <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> オブジェクト \(新しいプロジェクト項目の種類の定義\) の <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> イベントを処理します。  
  
3.  イベント ハンドラーで、シナリオに適用される条件に基づいて、配置しようとしているプロジェクト項目と SharePoint サイトに配置されているソリューションの間で競合が発生しているかどうかを判断します。  イベント引数パラメーターの <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> プロパティを使用して、配置しようとしているプロジェクト項目を分析できます。また、このために定義する SharePoint コマンドを呼び出して、配置場所にあるファイルを分析できます。  
  
     多くの種類の競合では、最初にどの配置手順が実行されているかを判断する必要があります。  これは、イベント引数パラメーターの <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> プロパティを使用して行うことができます。  一般的には、組み込みの <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> 配置手順中に競合を検出することが理にかなっていますが、いずれの配置手順中でも競合を確認できます。  
  
4.  競合が存在する場合は、イベント引数の <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> プロパティの <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> メソッドを使用して、新しい <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> オブジェクトを作成します。  このオブジェクトは配置競合を表します。  <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> メソッドの呼び出しで、競合を解決するために呼び出すメソッドも指定します。  
  
## 例  
 次のコード例は、リスト定義プロジェクト項目のプロジェクト項目の拡張機能における配置競合を処理する基本的なプロセスを示しています。  別の種類のプロジェクト項目の配置競合を処理するには、別の文字列を <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> に渡します。  詳細については、「[Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)」を参照してください。  
  
 説明を簡単にするため、この例の <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> イベント ハンドラーでは、配置競合が存在することを前提としており \(つまり、常に新しい <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> オブジェクトを追加する\)、`Resolve` メソッドは競合が解決されたことを示す **true** だけを返します。  実際のシナリオでは、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> イベント ハンドラーは、最初に現在のプロジェクト項目に含まれるファイルと配置場所にあるファイルの間で競合が存在しているかどうかを判断し、競合が存在する場合にのみ <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> オブジェクトを追加します。  たとえば、イベント ハンドラーで `e.ProjectItem.Files` プロパティを使用してプロジェクト項目に含まれるファイルを分析し、SharePoint コマンドを呼び出して配置場所にあるファイルを分析します。  同様に、実際のシナリオでは、`Resolve` メソッドが SharePoint コマンドを呼び出して SharePoint サイト上での競合を解決します。  SharePoint コマンドの作成の詳細については、「[How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)」を参照してください。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/cs/extension/deploymentconflictextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/vb/extension/deploymentconflictextension.vb#1)]  
  
## コードのコンパイル  
 この例は、次のアセンブリへの参照を必要とします。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 拡張機能の配置  
 拡張機能を配置するには、アセンブリと、拡張機能に同梱する必要のあるその他のファイルを提供するための [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  