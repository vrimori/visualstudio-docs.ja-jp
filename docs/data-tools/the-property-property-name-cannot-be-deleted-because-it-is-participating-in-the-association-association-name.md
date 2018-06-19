---
title: プロパティは、関連付けに関与しているために、削除できません。
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 98f95c489758b808ae7a210f7d83332f84571d1f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924140"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>プロパティ&lt;プロパティ名&gt;関連付けに関与しているために、削除できません&lt;association 名&gt;

選択したプロパティとして設定されて、**関連付けプロパティ**クラス間の関連付けのエラー メッセージに示されています。 プロパティがデータ クラス間の関連付けに関与している場合、そのプロパティを削除することはできません。

設定、**関連付けプロパティ**を目的のプロパティが正常に削除を有効にするデータ クラスの別のプロパティです。

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. O/R デザイナーで、エラー メッセージに示されているデータ クラスを接続する関連行を選択します。

2. 開くには行をダブルクリックして、 **[関連付けエディター** ] ダイアログ ボックス。

3. プロパティを削除、**関連付けのプロパティ**です。

4. プロパティの削除を再試行します。

## <a name="see-also"></a>関連項目

- [O/R デザイナーのメッセージ](../data-tools/o-r-designer-messages.md)
- [Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)