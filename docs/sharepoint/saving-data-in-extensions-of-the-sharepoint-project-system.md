---
title: "Saving Data in Extensions of the SharePoint Project System"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint project items, saving string data"
  - "project items [SharePoint development in Visual Studio], saving string data"
  - "projects [SharePoint development in Visual Studio], saving string data"
  - "SharePoint projects, saving string data"
ms.assetid: 903b9da7-2eea-404c-9a7a-7bc15cb90d6c
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Saving Data in Extensions of the SharePoint Project System
  SharePoint プロジェクト システムを拡張した場合、SharePoint プロジェクトを閉じた後も保持される文字列データを保存できます。  通常、データは、特定のプロジェクト項目またはプロジェクト自体に関連付けられています。  
  
 保持する必要のないデータがある場合は、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> インターフェイスを実装する SharePoint ツールのオブジェクト モデル内の任意のオブジェクトにそのデータを追加できます。  詳細については、「[Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)」を参照してください。  
  
## プロジェクト項目に関連付けられているデータの保存  
 プロジェクト項目に追加したプロパティの値など、特定の SharePoint プロジェクト項目に関連付けられているデータがある場合は、そのデータをプロジェクト項目の .spdata ファイルに保存できます。  これを行うには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> プロパティを使用します。  このプロパティに追加するデータは、プロジェクト項目の .spdata ファイルの **ExtensionData** 要素に保存されます。  詳細については、「[ExtensionData Element](../sharepoint/extensiondata-element.md)」を参照してください。  
  
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> プロパティを使用してカスタムの SharePoint プロジェクト項目の種類で定義されている文字列プロパティの値を保存する方法を次のコード例に示します。  この例のコンテキストを確認するには、「[How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)」を参照してください。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#14)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#14)]  
  
## プロジェクトに関連付けられているデータの保存  
 SharePoint プロジェクトに追加したプロパティの値など、プロジェクト レベルのデータがある場合は、そのデータをプロジェクト ファイル \(.csproj ファイルか .vbproj ファイル\) またはプロジェクト ユーザー オプション ファイル \(.csproj.user ファイルか .vbproj.user ファイル\) に保存できます。  データを保存するために選択するファイルは、データの使用方法によって異なります。  
  
-   SharePoint プロジェクトを開くすべての開発者がデータを使用できるようにする場合は、データをプロジェクト ファイルに保存します。  このファイルは、常にソース管理データベースにチェックインされるため、このファイルに含まれるデータは、プロジェクトをチェックアウトする他の開発者が使用できます。  
  
-   Visual Studio で SharePoint プロジェクトを開いている現在の開発者だけがデータを使用できるようにするには、データをプロジェクト ユーザー オプション ファイルに保存します。  通常、このファイルはソース管理データベースにチェックインされないため、このファイルに含まれるデータは、プロジェクトをチェックアウトする他の開発者には使用できません。  
  
### プロジェクト ファイルへのデータの保存  
 プロジェクト ファイルにデータを保存するには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> オブジェクトを <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> オブジェクトに変換して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> メソッドを使用します。  このメソッドを使用して、プロジェクト プロパティの値をプロジェクト ファイルに保存する方法を次のコード例に示します。  この例のコンテキストを確認するには、「[How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)」を参照してください。  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#3)]
 [!code-vb[SpExt_SPCustomPrjProperty#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#3)]  
  
 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> オブジェクトを Visual Studio のオートメーション オブジェクト モデルまたは Visual Studio の統合オブジェクト モデルの他の種類のオブジェクトに変換する方法の詳細については、「[Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)」を参照してください。  
  
### プロジェクト ユーザー オプション ファイルへのデータの保存  
 プロジェクト ユーザー オプション ファイルにデータを保存するには、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> オブジェクトの <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> プロパティを使用します。  このプロパティを使用して、プロジェクト プロパティの値をプロジェクト ユーザー オプション ファイルに保存する方法を次のコード例に示します。  この例のコンテキストを確認するには、「[How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)」を参照してください。  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#2)]
 [!code-vb[SpExt_SPCustomPrjProperty#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#2)]  
  
## 参照  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  