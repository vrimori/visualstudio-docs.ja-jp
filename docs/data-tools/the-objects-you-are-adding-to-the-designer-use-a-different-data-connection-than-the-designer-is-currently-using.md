---
title: デザイナーに追加する対象のオブジェクトは、デザイナーが現在使用しているのとは異なるデータ接続を使用しています
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 639c1c259426ec27358b4b611165d7ca55c0adde
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54994554"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>デザイナーに追加するオブジェクトを使用して、デザイナーのさまざまなデータ接続

デザイナーに追加する対象のオブジェクトは、デザイナーが現在使用しているのとは異なるデータ接続を使用しています。 デザイナーが使用している接続に置き換えますか?

項目を追加すると、**オブジェクト リレーショナル デザイナー** (**O/R デザイナー**)、すべての項目が 1 つの共有データ接続を使用します。 デザイン サーフェイスは、サーフェイス上のすべてのオブジェクトに対して単一の接続を使用する <xref:System.Data.Linq.DataContext> を表します。デザイナーで現在使用されているデータ接続とは異なるデータ接続を使用するオブジェクトをデザイナーに追加すると、このメッセージが表示されます。 このエラーを解決するために、既存の接続を維持するように選択できます。 その場合、選択したオブジェクトは追加されません。 別の方法として、オブジェクトを追加し、<xref:System.Data.Linq.DataContext> 接続を新しい接続にリセットすることもできます。

## <a name="connection-options"></a>接続オプション

- 選択したオブジェクトによって使用される接続で、既存の接続を置き換えるにはクリックして**はい**します。

   選択したオブジェクトに追加されます、 **O/R デザイナー**、および*DataContext.Connection*が新しい接続に設定します。

   > [!NOTE]
   > クリックすると**はい**、上のすべてのエンティティ クラス、 **O/R デザイナー**新しい接続にマップされます。

- クリックすると、既存の接続と、選択したオブジェクトを追加する [キャンセル] を使用する続行**いいえ**します。

   操作がキャンセルされます。 *DataContext.Connection* は、既存の接続に設定されたままになります。

## <a name="see-also"></a>関連項目

- [O/R デザイナーのメッセージ](../data-tools/o-r-designer-messages.md)
- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
