---
title: "Extending SharePoint Projects | Microsoft Docs"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 4643012b-6e6c-4b7c-bb92-b04b34f6c715
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Extending SharePoint Projects
  SharePoint プロジェクトのプロジェクト レベルの機能をカスタマイズするには、プロジェクトの拡張機能を作成します。  たとえば、カスタム プロジェクト プロパティを追加したり、ユーザーが Visual Studio で SharePoint ソリューションを開発したときに発生するプロジェクト レベルのイベントに応答したりすることができます。  
  
## プロジェクトの拡張機能の作成  
 プロジェクト項目を拡張するには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> インターフェイスを実装する Visual Studio 拡張機能アセンブリを構築します。  詳細については、「[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)」を参照してください。  
  
 プロジェクト拡張機能を作成するときに、SharePoint プロジェクトに次の機能も追加できます。  
  
-   ショートカット メニュー項目の追加。  メニュー項目は、ノードを右クリックするか、選択し、Shift \+ F10キーの選択して **\[ソリューション エクスプローラー\]** のSharePointプロジェクト ノードのショートカット メニューを開いたときに表示されます。  詳細については、「[How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)」を参照してください。  
  
-   カスタム プロパティの追加。  プロパティは **\[プロパティ\]** のウィンドウで **\[ソリューション エクスプローラー\]**でSharePointプロジェクトを選択するときに表示されます。  詳細については、「[How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)」を参照してください。  
  
 プロジェクトの拡張機能の作成、配置、およびテストの方法を示すチュートリアルについては、「[Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)」を参照してください。  
  
## プロジェクト拡張機能とプロジェクト インスタンスとの関係について  
 プロジェクトの拡張機能を作成するとき、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で任意の種類の SharePoint プロジェクトが開かれると、拡張機能が読み込まれます。[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] には、リスト定義、コンテンツ タイプ、イベント レシーバーなど、いくつかの SharePoint プロジェクト テンプレートが含まれます。  ただし、SharePoint プロジェクトの種類は 1 つだけです。  **\[新しいプロジェクト\]** ダイアログ ボックスに表示されるプロジェクトの種類は、1 つ以上の SharePoint プロジェクト項目を 1 つのバンドルにまとめるテンプレートだけです。  SharePoint プロジェクトの種類が 1 つしかないため、1 つのプロジェクトに対して作成される拡張機能がすべての SharePoint プロジェクトに適用されます。  たとえば、**コンテンツ タイプ** プロジェクトにのみ適用される拡張機能を作成することはできません。  
  
 特定のプロジェクト インスタンスにアクセスするには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> メソッドの実装で、*projectService* パラメーターの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> イベントの 1 つを処理します。  たとえば、SharePoint プロジェクトがいつソリューションに追加されるかを決定するには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> イベントを処理します。  詳細については、「[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)」を参照してください。  
  
## 参照  
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  