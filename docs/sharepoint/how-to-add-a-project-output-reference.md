---
title: "方法: プロジェクト出力参照の追加 |Microsoft ドキュメント"
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
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
ms.assetid: 9d6bc25e-bf0d-4483-a691-2ad7a796fa80
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: faf46489be0b9a56485fc93c2138a7f6702c4778
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-project-output-reference"></a>方法: プロジェクト出力参照を追加する
  以外の SharePoint プロジェクトのアセンブリ (または Silverlight プロジェクトでの .xap ファイル) を SharePoint を展開するには、それらをプロジェクト出力参照として追加します。  
  
 このプロセスでは、2 つのプロジェクト間ソリューション ビルドの依存関係を作成します。 SharePoint プロジェクトをビルドおよび配置する前に、プロジェクト出力参照に関連付けられているプロジェクトが構築されます。  
  
### <a name="to-add-a-project-output-reference"></a>プロジェクト出力参照を追加するには  
  
1.  少なくとも 1 つの SharePoint プロジェクトと 1 つ以外の SharePoint プロジェクトを含むソリューションを読み込みます。  
  
2.  **ソリューション エクスプ ローラー**項目、SharePoint プロジェクト ノードを選択します。  
  
3.  **プロパティ**ウィンドウで、選択、**プロジェクト出力参照**プロパティを選択し、省略記号 (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP です。NET モバイル デザイナー楕円")) ボタンをクリックします。  
  
4.  **プロジェクト出力参照** ダイアログ ボックスで、選択、**追加**ボタンをクリックします。  
  
5.  プロパティ ウィンドウを選択 の横に矢印、**展開の種類**プロパティ以外の SharePoint アイテムを参照しているなどの適切な値を選択し**ElementFile**です。  
  
6.  横の矢印を選択**プロジェクト名**、以外の SharePoint プロジェクト項目の名前を選択し、、 **OK**ボタンをクリックします。  
  
## <a name="see-also"></a>関連項目  
 [パッケージとプロジェクト アイテムの展開情報を提供します。](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [方法: 安全なコントロールとしてマークの制御](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  