---
title: プロパティ&lt;プロパティ名&gt;削除することはできません |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98b065500c9c881a7190b59c4d70a0433eb8864c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186525"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>プロパティ&lt;プロパティ名&gt;を削除できません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
プロパティ\<プロパティ名 > の間の継承に対する識別子のプロパティとして設定されているために削除できません\<クラス名 > と\<クラス名 >  
  
 選択したプロパティとして設定されて、**識別子のプロパティ**クラス間の継承には、エラー メッセージに示されています。 プロパティがデータ クラス間の継承構成に関与している場合、そのプロパティを削除することはできません。  
  
 設定、**識別子プロパティ**を目的のプロパティが正常に削除を有効にするデータ クラスの別のプロパティ。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  O/R デザイナーで、エラー メッセージに示されているデータ クラスを接続する継承線を選択します。  
  
2.  設定、**識別子**を別のプロパティのプロパティ。  
  
3.  プロパティの削除を再試行します。  
  
## <a name="see-also"></a>関連項目  
 [方法: O/R デザイナーを使用して継承を構成します。](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [データ クラスの継承 (O/R デザイナー)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [チュートリアル: 単一テーブル継承を使用した LINQ to SQL クラスの作成 (O/R デザイナー)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)

