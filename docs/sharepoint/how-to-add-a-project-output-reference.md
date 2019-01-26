---
title: '方法: プロジェクト出力参照の追加 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7a26f6b2abdf0e24d4179986acc56335fb36d002
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868785"
---
# <a name="how-to-add-a-project-output-reference"></a>方法: プロジェクト出力参照を追加します。
  SharePoint 以外のプロジェクト アセンブリ (または Silverlight プロジェクトの .xap ファイル) を SharePoint に展開するには、それらをプロジェクト出力参照として追加します。  
  
 このプロセスは、2 つのプロジェクト間ソリューション ビルドの依存関係を作成します。 SharePoint プロジェクトをビルドおよび配置する前に、プロジェクト出力参照に関連付けられているプロジェクトが構築されます。  
  
### <a name="to-add-a-project-output-reference"></a>プロジェクト出力参照を追加するには
  
1.  少なくとも 1 つの SharePoint プロジェクトと 1 つの SharePoint 以外のプロジェクトを含むソリューションを読み込みます。  
  
2.  **ソリューション エクスプ ローラー**、SharePoint プロジェクト ノードから項目をクリックします。  
  
3.  **プロパティ**ウィンドウで、選択、**プロジェクト出力参照**プロパティ、省略記号を選択し (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP します。NET モバイル デザイナー楕円")) ボタンをクリックします。  
  
4.  **プロジェクト出力参照** ダイアログ ボックスで、選択、**追加**ボタンをクリックします。  
  
5.  プロパティ ペインでに横に矢印を選択、**展開の種類**プロパティなど、参照は、SharePoint 以外の項目に対して適切な値を選択し、 **ElementFile**します。  
  
6.  横にある矢印を選択**プロジェクト名**、非 SharePoint プロジェクト項目の名前を選択し、、 **OK**ボタンをクリックします。  
  
## <a name="see-also"></a>関連項目
 [プロジェクト項目でパッケージ化と配置の情報を提供します。](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [方法: 安全なコントロールとしてマーク コントロール](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [パッケージ化し、SharePoint ソリューションのデプロイ](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
