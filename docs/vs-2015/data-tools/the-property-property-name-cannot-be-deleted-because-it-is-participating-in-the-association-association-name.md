---
title: プロパティ&lt;プロパティ名&gt;関連付けに関与しているために削除できません&lt;アソシエーション名&gt;|Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6983d52615219c386b049eea33f9f911956c6d59
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537176"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>プロパティ&lt;プロパティ名&gt;関連付けに関与しているために削除できません&lt;関連付けの名前&gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロパティ&lt;プロパティ名&gt;関連付けに関与しているために削除できません&lt;アソシエーション名&gt;](https://docs.microsoft.com/visualstudio/data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name)します。  
  
  
選択したプロパティとして設定されて、**関連付けプロパティ**クラス間の関連付けには、エラー メッセージに示されています。 プロパティがデータ クラス間の関連付けに関与している場合、そのプロパティを削除することはできません。  
  
 設定、**関連付けプロパティ**を目的のプロパティが正常に削除を有効にするデータ クラスの別のプロパティ。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  O/R デザイナーで、エラー メッセージに示されているデータ クラスを接続する関連行を選択します。  
  
2.  開く行をダブルクリックして、**関連付けエディター**  ダイアログ ボックス。  
  
3.  プロパティを削除、**関連プロパティ**します。  
  
4.  プロパティの削除を再試行します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [方法: LINQ to SQL クラス (O/R デザイナー) の間の関連付け (リレーションシップ) の作成](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成します。](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

