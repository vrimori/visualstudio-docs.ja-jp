---
title: "How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: f6ec47a7-e7d9-4e26-810b-77943a1ab04c
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type
  カスタムの SharePoint プロジェクト項目の種類を定義する場合は、ショートカット メニュー項目にプロパティを追加できます。  このメニュー項目は、ユーザーが**ソリューション エクスプローラー**でプロジェクト項目を右クリックすると表示されます。  
  
 次の手順は、独自の SharePoint プロジェクト項目の種類が既に定義されていることを前提としています。  詳細については、「[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)」を参照してください。  
  
### ショートカット メニュー項目をカスタム プロジェクト項目の種類に追加するには  
  
1.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 実装の <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> メソッドで、*projectItemTypeDefinition* パラメーターの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> イベントを処理します。  
  
2.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> イベントのイベント ハンドラーで、新しい <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> オブジェクトをイベント引数パラメーターの <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> コレクションまたは <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> コレクションに追加します。  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> の新しいオブジェクトの <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> のイベント ハンドラーで、userがショートカット メニュー項目を選択したときに実行するタスクを実行します。  
  
## 例  
 コンテキスト メニュー項目をカスタムのプロジェクト項目の種類に追加する方法を次のコード例に示します。  userが **\[ソリューション エクスプローラー\]** プロジェクト項目からショートカット メニューを開き、**\[Write Message to Output Window\]** のメニュー項目を選択すると、Visual Studioは、**\[出力\]** のウィンドウのメッセージを表示します。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypemenu.vb#4)]  
  
 この例では、SharePoint プロジェクト サービスを使用して、**出力**ウィンドウにメッセージを書き込みます。  詳細については、「[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)」を参照してください。  
  
## コードのコンパイル  
 この例では、次のアセンブリへの参照を含むクラス ライブラリ プロジェクトが必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## プロジェクト項目の配置  
 自分が定義したプロジェクト項目を他の開発者が使用できるようにするには、プロジェクト テンプレートまたはプロジェクト項目テンプレートを作成します。  詳細については、「[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)」を参照してください。  
  
 プロジェクト項目を配置するには、同梱する必要のあるアセンブリやテンプレート、各種ファイルの [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 拡張機能 \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  