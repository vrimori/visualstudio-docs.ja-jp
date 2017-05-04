---
title: "How to: Create a SharePoint Project Extension | Microsoft Docs"
ms.custom: ""
ms.date: "04/28/2017"
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
ms.assetid: ceecb9cb-4a5d-44c9-992f-9624737ac996
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# How to: Create a SharePoint Project Extension
  Visual Studio で開く SharePoint プロジェクトに機能を追加する必要がある場合は、プロジェクトの拡張機能を作成します。  詳細については、「[Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)」を参照してください。  
  
### プロジェクトの拡張機能を作成するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> インターフェイスを実装するクラスを作成します。  
  
4.  クラスに <xref:System.ComponentModel.Composition.ExportAttribute> を追加します。  この属性によって、Visual Studio で <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> の実装を検出し、読み込むことができます。  この属性のコンストラクターに <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 型を渡します。  
  
5.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> メソッドの実装では、*projectService* パラメーターのメンバーを使用して拡張機能の動作を定義します。  このパラメーターは、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> インターフェイスに定義されているイベントにアクセスできるようにする <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> オブジェクトです。  
  
## 例  
 次のコード例は、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> インターフェイスで定義されている SharePoint プロジェクト イベントのほとんどを処理する単純なプロジェクト拡張機能を作成する方法を示します。  コードをテストするには、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で SharePoint プロジェクトを作成してから、ソリューションにさらにプロジェクトを追加したり、プロジェクト プロパティ値の変更や、プロジェクトの削除または除外を行ったりします。  拡張機能は、**\[出力\]** ウィンドウおよび **\[エラー一覧\]** ウィンドウにメッセージを書き込むことで、ユーザーにイベントを通知します。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectextension.cs#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectextension.vb#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/savedatatoprojectfile.vb#3)]  
  
 この例では、SharePoint プロジェクト サービスを使用して、**出力**ウィンドウおよび **\[エラー一覧\]** ウィンドウにメッセージを書き込みます。  詳細については、「[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)」を参照してください。  
  
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> イベントおよび <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> イベントを処理する方法の例については、「[How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)」および「[How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)」を参照してください。  
  
## コードのコンパイル  
 この例は、次のアセンブリへの参照を必要とします。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 拡張機能の配置  
 拡張機能を配置するには、アセンブリと、拡張機能に同梱する必要のあるその他のファイルを提供するための [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)  
  
  