---
title: "How to: Add a Property to SharePoint Projects"
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
ms.assetid: c5eb4900-c35f-490a-b856-bf167da2d293
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Property to SharePoint Projects
  プロジェクトの拡張機能を使用して任意の SharePoint プロジェクトにプロパティを追加できます。  プロパティは、**ソリューション エクスプローラー**でプロジェクトを選択したときに **\[プロパティ\]** ウィンドウに表示されます。  
  
 次の手順は、プロジェクトの拡張機能が既に作成されていることを前提としています。  詳細については、「[How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)」を参照してください。  
  
### SharePoint プロジェクトにプロパティを追加するには  
  
1.  SharePoint プロジェクトに追加するプロパティを表すパブリック プロパティを使用して、クラスを定義します。  複数のプロパティを追加する場合は、すべてのプロパティを同じクラスで定義することも、異なるクラスで定義することもできます。  
  
2.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 実装の <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> メソッドで、*projectService* パラメーターの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> イベントを処理します。  
  
3.  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> イベントのイベント ハンドラーで、プロパティ クラスのインスタンスをイベント引数パラメーターの <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> コレクションに追加します。  
  
## 例  
 2 つのプロパティを SharePoint プロジェクトに追加する方法を次のコード例に示します。  一方のプロパティは、そのデータをプロジェクト ユーザー オプション ファイル \(.csproj.user ファイルまたは .vbproj.user ファイル\) で保持します。  もう一方のプロパティは、そのデータをプロジェクト ファイル \(.csproj ファイルまたは .vbproj ファイル\) で保持します。  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#1)]
 [!code-vb[SpExt_SPCustomPrjProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#1)]  
  
### コードについて  
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> イベントが発生するたびに `CustomProjectProperties` クラスの同じインスタンスが使用されるように、このイベントが初めて発生したときにプロジェクトの <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> プロパティにプロパティ オブジェクトを追加するコード例を次に示します。  このコードは、このイベントが発生するたびにこのオブジェクトを取得します。  <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> プロパティを使用してデータとプロジェクトを関連付ける方法については、「[Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)」を参照してください。  
  
 プロパティ値の変更を保持するために、プロパティの **set** アクセサーで次の API が使用されます。  
  
-   `CustomUserFileProperty` は <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> プロパティを使用して、その値をプロジェクト ユーザー オプション ファイルに保存します。  
  
-   `CustomProjectFileProperty` は <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> メソッドを使用して、その値をプロジェクト ファイルに保存します。  
  
 これらのファイルでデータを保持する方法の詳細については、「[Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)」を参照してください。  
  
### カスタム プロパティの動作の指定  
 **\[プロパティ\]** ウィンドウでカスタム プロパティの外観および動作を定義するには、プロパティ定義に <xref:System.ComponentModel> 名前空間の属性を適用します。  次の属性がさまざまなシナリオで役立ちます。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: **\[プロパティ\]** ウィンドウに表示されるプロパティの名前を指定します。  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: プロパティを選択したときに **\[プロパティ\]** ウィンドウの下部に表示される説明文字列を指定します。  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: プロパティの既定値を指定します。  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: **\[プロパティ\]** ウィンドウに表示される文字列と非文字列のプロパティ値の間のカスタム変換を指定します。  
  
-   <xref:System.ComponentModel.EditorAttribute>: プロパティの変更に使用するカスタム エディターを指定します。  
  
## コードのコンパイル  
 この例は、次のアセンブリへの参照を必要とします。  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## 拡張機能の配置  
 拡張機能を配置するには、アセンブリと、拡張機能に同梱する必要のあるその他のファイルを提供するための [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) パッケージを作成します。  詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  