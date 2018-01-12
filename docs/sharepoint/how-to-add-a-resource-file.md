---
title: "方法: リソース ファイルを追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: 47cae5fac3ddbcbc34535176701d0293ae4f66ba
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-resource-file"></a>方法: リソース ファイルを追加する
  リソース ファイルを追加するためのコマンドは、ソリューション エクスプ ローラー内の機能のノード、ソリューション ノードのショートカット メニューでです。 詳細については、次を参照してください。 [SharePoint ソリューションのローカライズ](../sharepoint/localizing-sharepoint-solutions.md)です。  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>SharePoint ソリューションにグローバル リソース ファイルを追加するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、SharePoint ソリューションを開きます。  
  
2.  **ソリューション エクスプ ローラー**、SharePoint プロジェクト ノードを選択し、メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
3.  **新しい項目の追加** ダイアログ ボックスで、選択、**グローバル リソース ファイル**テンプレートを選択し、**追加**ボタンをクリックします。  
  
    > [!NOTE]  
    >  グローバル リソース ファイル プロジェクト項目テンプレートは、SharePoint プロジェクト項目が選択されている場合にのみ表示されます。  
  
4.  **リソースの追加** ダイアログ ボックスで、英語 (米国) など、リソース ファイル用のカルチャを選択します。  
  
     この手順にグローバル リソース ファイルの形式で、リソース、ソリューションを追加*x***.***カルチャ***.**resx、Resource1.en US.resx などです。  
  
5.  ときに、**リソース エディター**で開きます[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、リソース ファイルにリソースを追加します。  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>フィーチャー リソース ファイルを SharePoint フィーチャーに追加するには  
  
1.  SharePoint ソリューションがで開いていない場合[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ソリューションを開きます。  
  
2.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、[機能の名前、**機能**] ノードを選択し**フィーチャー リソースの追加**です。  
  
     この手順にリソース ファイルの形式で、機能を追加*ResourceFileName***.***カルチャ***.**resx、Feature1.en US.resx などです。  
  
3.  ときに、**リソース エディター**で開きます[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、リソース ファイルにリソースを追加します。  
  
## <a name="see-also"></a>参照  
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  
  