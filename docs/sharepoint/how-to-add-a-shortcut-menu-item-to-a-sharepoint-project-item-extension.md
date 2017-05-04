---
title: "How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension | Microsoft Docs"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: d00513a6-d66d-4fbe-9efa-ef3b08c9a73a
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension
  既存の SharePoint プロジェクト項目にショートカット メニュー項目を追加するには、プロジェクト項目の拡張機能を使用します。  このメニュー項目は、ユーザーが**ソリューション エクスプローラー**でプロジェクト項目を右クリックすると表示されます。  
  
 次の手順は、プロジェクト項目の拡張機能が既に作成されていることを前提としています。  詳細については、「[How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)」を参照してください。  
  
### ショートカット メニュー項目をプロジェクト項目の拡張機能に追加するには  
  
1.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 実装の <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> メソッドで、*projectItemType* パラメーターの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> イベントを処理します。  
  
2.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> イベントのイベント ハンドラーで、新しい <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> オブジェクトをイベント引数パラメーターの <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> コレクションまたは <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> コレクションに追加します。  
  
3.  新しい <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> イベント ハンドラーで、ユーザーがショートカット メニュー項目をクリックしたときに実行するタスクを実行します。  
  
## 例  
 ショートカット メニュー項目をイベント レシーバー プロジェクト項目に追加する方法を次のコード例に示します。  ユーザーが**ソリューション エクスプローラー**でプロジェクト項目を右クリックし、**\[出力ウィンドウへのメッセージの書き込み\]** メニュー項目をクリックすると、Visual Studio の **\[出力\]** ウィンドウにメッセージが表示されます。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionmenu.vb#1)]  
  
 この例では、SharePoint プロジェクト サービスを使用して、**出力**ウィンドウにメッセージを書き込みます。  詳細については、「[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)」を参照してください。  
  
## コードのコンパイル  
 この例では、次のアセンブリへの参照を含むクラス ライブラリ プロジェクトが必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 拡張機能の配置  
 拡張機能を配置するには、アセンブリと、拡張機能に同梱する必要のあるその他のファイルを提供するための [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  