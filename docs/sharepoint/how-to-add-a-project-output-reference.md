---
title: '方法: プロジェクト出力参照の追加 |Microsoft ドキュメント'
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
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97bfe044ef89691afdb1a8e845867ce2e177dbb9
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767963"
---
# <a name="how-to-add-a-project-output-reference"></a>方法: プロジェクト出力参照の追加
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
  
  