---
title: "How to: Add a Property to a SharePoint Project Item Extension | Microsoft Docs"
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
ms.assetid: 4fd97ef2-86e7-4d92-8e34-5b0ec3cc43a0
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# How to: Add a Property to a SharePoint Project Item Extension
  プロジェクト項目の拡張機能を使用して、既に Visual Studio にインストールされている任意の SharePoint プロジェクト項目にプロパティを追加できます。  プロパティは、**ソリューション エクスプローラー**でプロジェクト項目を選択したときに **\[プロパティ\]** ウィンドウに表示されます。  
  
 次の手順は、プロジェクト項目の拡張機能が既に作成されていることを前提としています。  詳細については、「[How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)」を参照してください。  
  
### プロジェクト項目の拡張機能にプロパティを追加するには  
  
1.  プロジェクト項目の種類に追加するプロパティを表すパブリック プロパティを使用して、クラスを定義します。  複数のプロパティをプロジェクト項目の種類に追加する場合は、すべてのプロパティを同じクラスまたは異なるクラスで定義できます。  
  
2.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 実装の <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> メソッドで、*projectItemType* パラメーターの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> イベントを処理します。  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> イベントのイベント ハンドラーで、プロパティ クラスのインスタンスをイベント引数パラメーターの <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> コレクションに追加します。  
  
## 例  
 次のコード例は、**\[Example Property\]** というプロパティをイベント レシーバー プロジェクト項目に追加する方法を示します。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionproperty.vb#8)]  
  
### コードについて  
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> イベントが発生するたびに `CustomProperties` クラスの同じインスタンスが使用されるように、このイベントが初めて発生したときにプロジェクト項目の <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> プロパティにプロパティ オブジェクトを追加するコード例を次に示します。  このコードは、このイベントが発生するたびにこのオブジェクトを取得します。  <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> プロパティを使用したデータとプロジェクト項目の関連付けの詳細については、「[Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)」を参照してください。  
  
 プロパティ値への変更を永続化するために、`ExampleProperty` の **set** アクセサーによって、プロパティが関連付けられている <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> プロパティに新しい値が保存されます。  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> プロパティを使用した、プロジェクト項目を含むデータの永続化の詳細については、「[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)」を参照してください。  
  
### カスタム プロパティの動作の指定  
 **\[プロパティ\]** ウィンドウでカスタム プロパティの外観および動作を定義するには、プロパティ定義に <xref:System.ComponentModel> 名前空間の属性を適用します。  次の属性がさまざまなシナリオで役立ちます。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: **\[プロパティ\]** ウィンドウに表示されるプロパティの名前を指定します。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: プロパティを選択したときに **\[プロパティ\]** ウィンドウの下部に表示される説明文字列を指定します。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: プロパティの既定値を指定します。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: **\[プロパティ\]** ウィンドウに表示される文字列と非文字列のプロパティ値の間のカスタム変換を指定します。  
  
-   <xref:System.ComponentModel.EditorAttribute>: プロパティの変更に使用するカスタム エディターを指定します。  
  
## コードのコンパイル  
 これらの例では、次のアセンブリへの参照を含むクラス ライブラリ プロジェクトが必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## 拡張機能の配置  
 拡張機能を配置するには、アセンブリと、拡張機能に同梱する必要のあるその他のファイルを提供するための [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  