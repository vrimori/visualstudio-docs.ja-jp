---
title: "How to: Add a Property to a Custom SharePoint Project Item Type"
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
ms.assetid: 47e940f6-1779-4530-aea6-c43a370c544f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# How to: Add a Property to a Custom SharePoint Project Item Type
  カスタムの SharePoint プロジェクト項目の種類を定義する場合は、プロジェクト項目にプロパティを追加できます。  プロパティは、**ソリューション エクスプローラー**でプロジェクト項目を選択したときに **\[プロパティ\]** ウィンドウに表示されます。  
  
 次の手順は、独自の SharePoint プロジェクト項目の種類が既に定義されていることを前提としています。  詳細については、「[How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)」を参照してください。  
  
### プロジェクト項目の種類の定義にプロパティを追加するには  
  
1.  カスタム プロジェクト項目の種類に追加するプロパティを表すパブリック プロパティを使用して、クラスを定義します。  複数のプロパティをカスタムのプロジェクト項目の種類に追加する場合は、すべてのプロパティを同じクラスまたは異なるクラスで定義できます。  
  
2.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 実装の <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> メソッドで、*projectItemTypeDefinition* パラメーターの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> イベントを処理します。  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> イベントのイベント ハンドラーで、カスタム プロパティ クラスのインスタンスをイベント引数パラメーターの <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> コレクションに追加します。  
  
## 例  
 次のコード例は、**プロパティ例**というプロパティをカスタムのプロジェクト項目の種類に追加する方法を示します。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#11)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#11)]  
  
### コードについて  
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> イベントが発生するたびに `CustomProperties` クラスの同じインスタンスが使用されるように、このイベントが初めて発生したときにプロジェクト項目の <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> プロパティにプロパティ オブジェクトを保存するコード例を次に示します。  このコードは、このイベントが発生するたびにこのオブジェクトを取得します。  <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> プロパティを使用した、プロジェクト項目を含むデータの保存の詳細については、「[Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)」を参照してください。  
  
 プロパティ値への変更を永続化するために、`ExampleProperty` の **set** アクセサーによって、プロパティが関連付けられている <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> プロパティに新しい値が保存されます。  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> プロパティを使用した、プロジェクト項目を含むデータの永続化の詳細については、「[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)」を参照してください。  
  
### カスタム プロパティの動作の指定  
 **\[プロパティ\]** ウィンドウでカスタム プロパティの外観および動作を定義するには、プロパティ定義に <xref:System.ComponentModel> 名前空間の属性を適用します。  次の属性がさまざまなシナリオで役立ちます。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: **\[プロパティ\]** ウィンドウに表示されるプロパティの名前を指定します。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: プロパティを選択したときに **\[プロパティ\]** ウィンドウの下部に表示される説明文字列を指定します。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: プロパティの既定値を指定します。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: **\[プロパティ\]** ウィンドウに表示される文字列と非文字列のプロパティ値の間のカスタム変換を指定します。  
  
-   <xref:System.ComponentModel.EditorAttribute>: プロパティの変更に使用するカスタム エディターを指定します。  
  
## コードのコンパイル  
 これらのコード例では、次のアセンブリへの参照を含むクラス ライブラリ プロジェクトが必要です。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## プロジェクト項目の配置  
 自分が定義したプロジェクト項目を他の開発者が使用できるようにするには、プロジェクト テンプレートまたはプロジェクト項目テンプレートを作成します。  詳細については、「[Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)」を参照してください。  
  
 プロジェクト項目を配置するには、同梱する必要のあるアセンブリやテンプレート、各種ファイルの [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 拡張機能 \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  