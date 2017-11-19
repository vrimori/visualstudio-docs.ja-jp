---
title: "SharePoint プロジェクト システムの拡張機能内のデータ保存 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
ms.assetid: 903b9da7-2eea-404c-9a7a-7bc15cb90d6c
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3605558fd1fd9263c5dad7ec7bc295b7f095a185
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="saving-data-in-extensions-of-the-sharepoint-project-system"></a>SharePoint プロジェクト システムの拡張機能におけるデータの保存
  SharePoint プロジェクト システムを拡張する場合に、SharePoint プロジェクトが閉じられた後に保持する文字列データを保存できます。 データは、通常、またはプロジェクト自体、特定のプロジェクト アイテムに関連付けられています。  
  
 実装する、SharePoint ツールのオブジェクト モデル内のオブジェクトにデータを追加するには永続化する必要のないデータを使用する場合、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>インターフェイスです。 詳細については、次を参照してください。 [SharePoint ツール拡張機能とカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)です。  
  
## <a name="saving-data-that-is-associated-with-a-project-item"></a>関連付けられているデータを保存するためのプロジェクト項目  
 プロジェクト項目に追加するプロパティの値など、特定の SharePoint プロジェクト アイテムに関連付けられているデータがある場合は、プロジェクト項目の .spdata ファイルにデータを保存できます。 これを行うを使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>オブジェクト。 このプロパティに追加するデータの保存、 **ExtensionData**プロジェクト項目の .spdata ファイル内の要素。 詳細については、次を参照してください。 [ExtensionData 要素](../sharepoint/extensiondata-element.md)です。  
  
 次のコード例を使用する方法を示しています、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>プロパティをカスタム SharePoint プロジェクト項目の種類で定義されている文字列プロパティの値を保存します。 例のコンテキストでは、この例を参照してください[する方法: カスタム SharePoint プロジェクト項目の種類にプロパティを追加](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)です。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="saving-data-that-is-associated-with-a-project"></a>関連付けられているデータを保存するプロジェクト  
 プロジェクト ファイル (.csproj ファイルまたは .vbproj ファイル) またはプロジェクト ユーザー オプション ファイルにデータを保存するには、SharePoint プロジェクトに追加するプロパティの値など、プロジェクト レベルのデータがある場合 (、。 csproj.user ファイルまたは。 vbproj.user ファイル)。 内のデータを保存するファイルは、データを使用する方法によって異なります。  
  
-   SharePoint プロジェクトを開くすべての開発者に使用するデータを表示する場合は、プロジェクト ファイルにデータを保存します。 このファイルは、このファイル内のデータは、プロジェクトをチェック アウトしたその他の開発者が利用できるようにも、常にソース管理データベースにチェックインします。  
  
-   SharePoint プロジェクトを Visual Studio で開きますしている現在の開発者にのみ使用するデータを表示する場合は、プロジェクト ユーザー オプション ファイルにデータを保存します。 このファイルは通常チェックインされませんソース管理データベースにプロジェクトをチェック アウトするその他の開発者にこのファイル内のデータはありません。  
  
### <a name="saving-data-to-the-project-file"></a>プロジェクト ファイルにデータの保存  
 プロジェクト ファイルにデータを保存する変換、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>オブジェクトを<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>オブジェクト、および使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>メソッドです。 次のコード例では、このメソッドを使用して、プロジェクトのプロパティの値をプロジェクト ファイルに保存する方法を示します。 大きなサンプルのコンテキストでは、この例を参照してください[する方法: SharePoint プロジェクトにプロパティを追加](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)です。  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 変換の詳細については<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>、Visual Studio オートメーション オブジェクト モデルまたは統合オブジェクト モデルの他の型のオブジェクトを参照してください[間で SharePoint プロジェクト システムの種類の変換およびその他の Visual Studio プロジェクトの種類](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="saving-data-to-the-project-user-option-file"></a>プロジェクト ユーザー オプション ファイルへのデータの保存  
 プロジェクト ユーザー オプション ファイルにデータを保存するを使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>オブジェクト。 次のコード例では、このプロパティを使用して、プロジェクトのプロパティの値をプロジェクト ユーザー オプション ファイルに保存する方法を示します。 大きなサンプルのコンテキストでは、この例を参照してください[する方法: SharePoint プロジェクトにプロパティを追加](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)です。  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>関連項目  
 [SharePoint プロジェクト システムの拡張](../sharepoint/extending-the-sharepoint-project-system.md)   
 [SharePoint ツール拡張機能とカスタム データの関連付け](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [SharePoint プロジェクト システムと他の Visual Studio プロジェクトの間の型変換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  