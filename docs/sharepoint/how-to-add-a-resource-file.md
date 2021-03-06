---
title: '方法: リソース ファイルの追加 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 928a306640c449db4fa168ffcdbdd7efaeea0ae1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862877"
---
# <a name="how-to-add-a-resource-file"></a>方法: リソース ファイルを追加します。
  リソース ファイルを追加するためのコマンドは、ソリューション エクスプ ローラー内のノードの機能、ソリューション ノードのショートカット メニューでです。 詳細については、次を参照してください。[をローカライズする SharePoint ソリューション](../sharepoint/localizing-sharepoint-solutions.md)します。  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>SharePoint ソリューションにグローバル リソース ファイルを追加するには  
  
1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、SharePoint ソリューションを開きます。  
  
2. **ソリューション エクスプ ローラー**を SharePoint プロジェクト ノードを選択し、メニュー バーで、次のように選択します。**プロジェクト** > **新しい項目の追加**します。  
  
3. **新しい項目の追加** ダイアログ ボックスで、選択、**グローバル リソース ファイル**テンプレートを選択し、**追加**ボタン。  
  
   > [!NOTE]  
   >  グローバル リソース ファイル プロジェクト項目テンプレートは、SharePoint プロジェクト アイテムが選択されている場合にのみ表示されます。  
  
4. **リソースの追加** ダイアログ ボックスで、英語 (米国) など、リソース ファイル用のカルチャを選択します。  
  
    この手順は、グローバル リソース ファイルを Resource_x_ の形式でソリューションに追加します **。** 。<em>カルチャ</em><strong>.</strong>resx、次のように、 *Resource1.en US.resx*します。  
  
5. ときに、**リソース エディター**で開きます[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、リソース ファイルにリソースを追加します。  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>フィーチャー リソース ファイルを SharePoint フィーチャーに追加するには  
  
1.  SharePoint ソリューションがで開いていない場合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ソリューションを開きます。  
  
2.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、機能の名前、**機能**ノードを選び、**フィーチャー リソースの追加**します。  
  
     この手順では、リソース ファイルを追加の形式で機能する_ResourceFileName_**.**_カルチャ_**.resx**、次のように、 *Feature1.en US.resx*します。  
  
3.  ときに、**リソース エディター**で開きます[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、リソース ファイルにリソースを追加します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
