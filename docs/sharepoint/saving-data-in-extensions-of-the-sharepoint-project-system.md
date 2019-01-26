---
title: SharePoint プロジェクト システムの拡張機能におけるデータの保存 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 373f031795238c599d15eec92f1730289662c3a0
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866543"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>SharePoint プロジェクト システムの拡張機能でデータを保存します。
  SharePoint プロジェクト システムを拡張するときは、SharePoint プロジェクトを閉じた後に保持される文字列データを保存できます。 データは、通常、またはプロジェクト自体と特定のプロジェクト項目と関連付けられています。  
  
 実装する SharePoint ツールのオブジェクト モデル内のオブジェクトにデータを追加するには永続化する必要のないデータがあれば、<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>インターフェイス。 詳細については、次を参照してください。[ツールの拡張機能を SharePoint でカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)します。  
  
## <a name="save-data-that-is-associated-with-a-project-item"></a>プロジェクト項目に関連付けられているデータを保存します。
 データを保存するには、プロジェクト項目に追加するプロパティの値など、特定の SharePoint プロジェクト アイテムに関連付けられているデータがある場合、 *.spdata*プロジェクト項目のファイル。 これを行うには、使用、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>オブジェクト。 このプロパティを追加するデータの保存、 **ExtensionData**内の要素、 *.spdata*プロジェクト項目のファイル。 詳細については、次を参照してください。 [ExtensionData 要素](../sharepoint/extensiondata-element.md)します。  
  
 次のコード例は、使用する方法を示します、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>プロパティをカスタム SharePoint プロジェクト項目の種類で定義されている文字列プロパティの値を保存します。 例のコンテキストでは、この例を確認するには、次を参照してください。[方法。カスタム SharePoint プロジェクト項目の種類にプロパティを追加](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)します。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="save-data-that-is-associated-with-a-project"></a>プロジェクトに関連付けられているデータを保存します。
 プロジェクト ファイルにデータを保存するには、SharePoint プロジェクトに追加するプロパティの値など、プロジェクト レベルのデータがある場合 (、 *.csproj*ファイルまたは *.vbproj*ファイル) またはプロジェクト ユーザー オプションファイル (、 *. csproj.user*ファイルまたは *. vbproj.user*ファイル)。 内のデータを保存するファイルは、データを使用する方法によって異なります。  
  
-   SharePoint プロジェクトを開くすべての開発者が利用できるデータを表示する場合は、プロジェクト ファイルにデータを保存します。 このファイルが、このファイル内のデータは、プロジェクトをチェック アウトしたその他の開発者が利用できるようにも、常に、ソース管理データベースにチェックインします。  
  
-   SharePoint プロジェクトを Visual Studio で開いている現在の開発者にのみ使用できるデータを表示する場合は、プロジェクト ユーザー オプション ファイルにデータを保存します。 このファイルは通常チェックインされない、ソース管理データベースにこのファイル内のデータをプロジェクトをチェック アウトするその他の開発者にご利用いただけませんので。  
  
### <a name="save-data-to-the-project-file"></a>プロジェクト ファイルにデータを保存します。
 プロジェクト ファイルにデータを保存する変換、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>オブジェクトを<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>オブジェクトし、を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>メソッド。 次のコード例では、このメソッドを使用して、プロジェクト プロパティの値をプロジェクト ファイルに保存する方法を示します。 大規模なサンプルのコンテキストでは、この例を確認するには、次を参照してください。[方法。SharePoint プロジェクトにプロパティを追加](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)します。  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 変換の詳細については<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>Visual Studio オートメーション オブジェクト モデルまたは統合オブジェクト モデルでは、他の型にオブジェクトを参照してください[SharePoint プロジェクト システムの種類とその他の Visual Studio プロジェクトの種類間の変換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="save-data-to-the-project-user-option-file"></a>プロジェクト ユーザー オプション ファイルにデータを保存します。
 プロジェクト ユーザー オプション ファイルにデータを保存するには、使用、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A>のプロパティ、<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>オブジェクト。 次のコード例では、このプロパティを使用して、プロジェクト ユーザー オプション ファイルをプロジェクト プロパティの値を保存する方法を示します。 大規模なサンプルのコンテキストでは、この例を確認するには、次を参照してください。[方法。SharePoint プロジェクトにプロパティを追加](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)します。  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>関連項目
 [SharePoint プロジェクト システムを拡張します。](../sharepoint/extending-the-sharepoint-project-system.md)   
 [SharePoint ツール拡張機能とカスタム データを関連付ける](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [SharePoint プロジェクト システムの種類とその他の Visual Studio プロジェクトの種類間の変換します。](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
