---
title: "How to: Add a Shortcut Menu Item to SharePoint Projects | Microsoft Docs"
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
ms.assetid: bb251fe9-f1bf-4ddd-9359-4b7f78fbd50f
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# How to: Add a Shortcut Menu Item to SharePoint Projects
  ショートカット メニュー項目を任意の SharePoint プロジェクトに追加できます。  このメニュー項目は、ユーザーが**ソリューション エクスプローラー**でプロジェクト ノードを右クリックすると表示されます。  
  
 次の手順は、プロジェクトの拡張機能が既に作成されていることを前提としています。  詳細については、「[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)」を参照してください。  
  
### ショートカット メニュー項目を SharePoint プロジェクトに追加するには  
  
1.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 実装の <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> メソッドで、*projectService* パラメーターの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> イベントを処理します。  
  
2.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> イベントのイベント ハンドラーで、新しい <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> オブジェクトをイベント引数パラメーターの <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> コレクションまたは <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> コレクションに追加します。  
  
3.  新しい <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> イベント ハンドラーで、ユーザーがショートカット メニュー項目をクリックしたときに実行するタスクを実行します。  
  
## 例  
 **ソリューション エクスプローラー**の SharePoint プロジェクト ノードにショートカット メニュー項目を追加する方法を次のコード例に示します。  ユーザーがプロジェクト ノードを右クリックし、**\[出力ウィンドウへのメッセージの書き込み\]** メニュー項目をクリックすると、Visual Studio の **\[出力\]** ウィンドウにメッセージが表示されます。  この例では、SharePoint プロジェクト サービスを使用して、メッセージを表示します。  詳細については、「[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)」を参照してください。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/vb/extension/projectitemextensionmenu.vb#1)]  
  
## コードのコンパイル  
 この例では、次のアセンブリへの参照を含むクラス ライブラリ プロジェクトが必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 拡張機能の配置  
 拡張機能を配置するには、アセンブリと、拡張機能に同梱する必要のあるその他のファイルを提供するための [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  