---
title: "Extending SharePoint Packaging and Deployment | Microsoft Docs"
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
ms.assetid: 4789ebb2-12bc-42b9-9427-e63d77137765
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Extending SharePoint Packaging and Deployment
  SharePoint プロジェクトのパッケージ化と配置のプロセスを拡張できます。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
##  <a name="creating_deployment_steps"></a> 配置手順を作成する  
 SharePoint プロジェクトを配置するとき、[!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] によって一連の配置手順が実行されます。  Visual Studio には、ソリューションの取り消しや追加など、さまざまなタスクに関する組み込みの配置手順が用意されています。  ただし、配置手順は独自に作成することもできます。  
  
 配置手順の作成方法を示すチュートリアルについては、「[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)」を参照してください。  
  
##  <a name="creating_deployment_configurations"></a> 配置構成を作成する  
 配置構成は、特定のプロジェクトについて実行される一連の配置手順ですが、すべての SharePoint プロジェクト項目に影響を与えることがあります。  すべての配置構成には、プロジェクトが配置されるときに実行される手順と、プロジェクトが取り消されるときに実行される手順が含まれています。  [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] には、組み込みの配置構成が 2 つ付属していますが、独自に作成することもできます。  配置構成を自分で作成する場合、組み込みの配置手順と独自に作成した配置手順とを混在させることができます。  
  
 配置構成の作成方法を示すチュートリアルについては、「[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)」を参照してください。  
  
##  <a name="run_code_before_and_after_each_deployment_step"></a> SharePoint ソリューションの配置時または取り消し時にコードを実行する  
 SharePoint ソリューションの配置時または取り消し時に、別途タスクを実行するためにイベントを処理することができます。  Visual Studio では、次のシナリオで処理できるイベントが生成されます。  
  
-   SharePoint プロジェクト項目について各配置手順が実行される前後。  詳細については、「[How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)」を参照してください。  
  
-   SharePoint プロジェクトの配置または取り消しが行われる前後。  詳細については、「[How to: Run Code When a SharePoint Project is Deployed or Retracted](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)」を参照してください。  
  
##  <a name="deployment_conflicts"></a> 配置競合の処理  
 モジュール、Web パーツ、リスト インスタンス、コンテンツ タイプなど、一部の種類の SharePoint プロジェクト項目では、組み込みの配置競合の解決が用意されています。  これらのいずれかのプロジェクト項目が含まれるソリューションを配置すると、Visual Studio は、まず、配置しようとしている項目に含まれるファイルと同じ名前、URL、または ID を持つファイルが、SharePoint サイトに既に存在しているかどうかを確認します。  競合が発生する場合、Visual Studio に自動的に競合を解決させることも、Visual Studio に競合を解決させるか配置を取り消すかを判断するようユーザーに要求することもできます。  詳細については、「[SharePoint のパッケージ化と配置のトラブルシューティング](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)」を参照してください。  
  
 配置競合を確認および解決する独自のコードを使用して、この機能を拡張できます。  詳細については、「[How to: Handle Deployment Conflicts](../sharepoint/how-to-handle-deployment-conflicts.md)」を参照してください。  
  
##  <a name="run_command_line_operations_before_or_after_a_project_is_deployed"></a> プロジェクトが配置される前と後にコマンド ライン操作を実行する  
 SharePoint ソリューションの配置時にコマンド ライン操作を実行する場合、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> プロパティと <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> プロパティを設定することができます。  これらのコマンドは、プロジェクトが配置される前と後に Visual Studio によって実行されます。  
  
 場合によっては、配置の競合が発生することがあります。  競合を解決する方法はいくつかあります。  詳細については、「[SharePoint のパッケージ化と配置のトラブルシューティング](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)」を参照してください。  
  
##  <a name="customizing_validation_rules"></a> 検証規則のカスタマイズ  
 ソリューション パッケージ \(.wsp\) を配置する前に、フィーチャーまたはパッケージが有効であることを検証するために、カスタムのフィーチャー検証規則およびパッケージ検証規則を作成できます。  たとえば、検証に関する問題の修正に役立つように、情報、警告、またはエラーを開発者に報告できます。  詳細については、「[How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)」を参照してください。  
  
## 参照  
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  