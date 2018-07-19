---
title: '方法: リソース ファイルの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3406e65ad96b93cd21890d61270c0ed989ad496c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756572"
---
# <a name="how-to-add-a-resource-file"></a>方法: リソース ファイルを追加
  リソース ファイルを追加するためのコマンドは、ソリューション エクスプ ローラー内のノードの機能、ソリューション ノードのショートカット メニューでです。 詳細については、次を参照してください。[をローカライズする SharePoint ソリューション](../sharepoint/localizing-sharepoint-solutions.md)します。  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>SharePoint ソリューションにグローバル リソース ファイルを追加するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、SharePoint ソリューションを開きます。  
  
2.  **ソリューション エクスプ ローラー**を SharePoint プロジェクト ノードを選択し、メニュー バーで、次のように選択します。**プロジェクト** > **新しい項目の追加**します。  
  
3.  **新しい項目の追加** ダイアログ ボックスで、選択、**グローバル リソース ファイル**テンプレートを選択し、**追加**ボタン。  
  
    > [!NOTE]  
    >  グローバル リソース ファイル プロジェクト項目テンプレートは、SharePoint プロジェクト アイテムが選択されている場合にのみ表示されます。  
  
4.  **リソースの追加** ダイアログ ボックスで、英語 (米国) など、リソース ファイル用のカルチャを選択します。  
  
     この手順は、グローバル リソース ファイルをリソースの形式でソリューションに追加します * x ***。*** 。カルチャ ***.** resx、次のように、 *Resource1.en US.resx*します。  
  
5.  ときに、**リソース エディター**で開きます[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、リソース ファイルにリソースを追加します。  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>フィーチャー リソース ファイルを SharePoint フィーチャーに追加するには  
  
1.  SharePoint ソリューションがで開いていない場合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ソリューションを開きます。  
  
2.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、機能の名前、**機能**ノードを選び、**フィーチャー リソースの追加**します。  
  
     この手順は、の形式で機能するリソース ファイルを追加します * ResourceFileName ***.*** カルチャ ***.** resx、次のように、 *Feature1.en US.resx*します。  
  
3.  ときに、**リソース エディター**で開きます[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、リソース ファイルにリソースを追加します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint ソリューションを開発します。](../sharepoint/developing-sharepoint-solutions.md)  
  
 
