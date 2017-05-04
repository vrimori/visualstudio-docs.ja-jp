---
title: "How to: Create a SharePoint Project Item Extension | Microsoft Docs"
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
ms.assetid: 163738b9-e25a-49c9-8f33-4b57a2da6b07
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# How to: Create a SharePoint Project Item Extension
  既に Visual Studio にインストールされている SharePoint プロジェクト項目に機能を追加する必要がある場合は、プロジェクト項目の拡張機能を作成します。  詳細については、「[Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)」を参照してください。  
  
### プロジェクト項目の拡張機能を作成するには  
  
1.  クラス ライブラリ プロジェクトを作成します。  
  
2.  次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> インターフェイスを実装するクラスを作成します。  
  
4.  クラスに次の属性を追加します。  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Visual Studio は、この属性を頼りに <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> の実装を発見し、読み込みます。  この属性のコンストラクターには <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 型を渡します。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  プロジェクト項目の拡張機能では、拡張の対象となるプロジェクト項目がこの属性によって識別されます。  プロジェクト項目の ID を属性コンストラクターに渡します。  Visual Studio に含まれるプロジェクト項目の ID の一覧については、 " " を参照してください。 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)  
  
5.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> メソッドの実装では、*projectItemType* パラメーターのメンバーを使用して拡張機能の動作を定義します。  このパラメーターは、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> インターフェイスおよび <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> インターフェイスに定義されているイベントにアクセスできる <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> オブジェクトです。  拡張しているプロジェクト項目の種類の特定インスタンスにアクセスするには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> などの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> イベントを処理します。  
  
## 例  
 次のコード例に、イベント レシーバー プロジェクト項目の単純な拡張機能の作成方法を示します。  SharePoint プロジェクトにイベント レシーバー プロジェクト項目をユーザーが追加するたびに、この拡張機能によって **\[出力\]** ウィンドウと **\[エラー一覧\]** ウィンドウにメッセージが書き込まれます。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemextension.vb#1)]  
  
 この例では、SharePoint プロジェクト サービスを使用して、**出力**ウィンドウおよび **\[エラー一覧\]** ウィンドウにメッセージを書き込みます。  詳細については、「[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)」を参照してください。  
  
## コードのコンパイル  
 この例は、次のアセンブリへの参照を必要とします。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 拡張機能の配置  
 拡張機能を配置するには、アセンブリと、拡張機能に同梱する必要のあるその他のファイルを提供するための [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  