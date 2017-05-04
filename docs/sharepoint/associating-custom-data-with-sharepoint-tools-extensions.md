---
title: "Associating Custom Data with SharePoint Tools Extensions | Microsoft Docs"
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
  - "projects [SharePoint development in Visual Studio], associating custom data"
  - "project items [SharePoint development in Visual Studio], associating custom data"
  - "SharePoint project items, associating custom data"
  - "SharePoint projects, associating custom data"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: cfc87272-85a1-4c36-89e4-2662417d59ea
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Associating Custom Data with SharePoint Tools Extensions
  SharePoint ツールの拡張機能に含まれる特定のオブジェクトにカスタム データを追加できます。  これは、拡張機能の他のコードから後でアクセスするデータが拡張機能の一部にある場合に役立ちます。  データを格納したりデータにアクセスしたりする方法をカスタマイズして実装する代わりに、データを拡張機能のオブジェクトに関連付けることで、後で同じオブジェクトからデータを取得できます。  
  
 オブジェクトにカスタム データを追加すると、Visual Studio の特定の項目に関連するデータを保持する場合にも役立ちます。  Visual Studio に SharePoint ツールの拡張機能が読み込まれるのは 1 回だけであるため、拡張機能は、いつでも、複数の異なる項目 \(プロジェクト、プロジェクト項目、**Server Explorer** のノードなど\) を処理している可能性があります。  特定の項目だけに関連するカスタム データを使用する場合は、その項目を表すオブジェクトにカスタム データを追加できます。  
  
 SharePoint ツールの拡張機能に含まれるオブジェクトにカスタム データを追加した場合、データは保持されません。  データは、オブジェクトの有効期間中にのみ使用できます。  ガベージ コレクションでオブジェクトがクリアされると、データは失われます。  
  
 SharePoint プロジェクト システムの拡張機能では、拡張機能のアンロード後も保持される文字列データを保存することもできます。  詳細については、「[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)」を参照してください。  
  
## カスタム データを格納できるオブジェクト  
 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> インターフェイスを実装する SharePoint ツールのオブジェクト モデルのすべてのオブジェクトにカスタム データを追加できます。  このインターフェイスは、カスタム データ オブジェクトのコレクションである 1 つのプロパティ <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> だけを定義します。  以下の型は <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> を実装します。  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## カスタム データの追加および取得  
 カスタム データを SharePoint ツールの拡張機能のオブジェクトに追加するには、カスタム データを追加するオブジェクトの <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> プロパティを取得してから、<xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> メソッドを使用してカスタム データをオブジェクトに追加します。  
  
 SharePoint ツール拡張機能でオブジェクトからカスタム データを取得するには、オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> を取得し、次のいずれかのメソッドを使用します。  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>.  このメソッドは、データ オブジェクトが存在する場合は **true** を返し、データ オブジェクトが存在しない場合は **false** を返します。  このメソッドを使用すると、値の型または参照型のインスタンスを取得できます。  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>.  このメソッドは、データ オブジェクトが存在する場合にはデータ オブジェクトを返し、データ オブジェクトが存在しない場合には **null** を返します。  このメソッドは、参照型のインスタンスを取得する場合のみ使用できます。  
  
 特定のデータ オブジェクトが既にプロジェクト項目に関連付けられているかどうかを確認する方法を次のコード例に示します。  データ オブジェクトがプロジェクト項目にまだ関連付けられていない場合は、プロジェクト項目の <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> プロパティにデータ オブジェクトを追加します。  この例のコンテキストを確認するには、「[How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)」を参照してください。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#13)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#13)]  
  
## 参照  
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)  
  
  