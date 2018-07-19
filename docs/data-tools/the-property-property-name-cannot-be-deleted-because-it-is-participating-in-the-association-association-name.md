---
title: プロパティは、アソシエーションに参加しているために削除できません。
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
ms.openlocfilehash: 6ed6b14f64d16d1f18d4b358761169c3d424cee8
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174063"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>プロパティ&lt;プロパティ名&gt;関連付けに関与しているために削除できません&lt;関連付けの名前&gt;

選択したプロパティとして設定されて、**関連付けプロパティ**クラス間の関連付けには、エラー メッセージに示されています。 プロパティがデータ クラス間の関連付けに関与している場合、そのプロパティを削除することはできません。

設定、**関連付けプロパティ**を目的のプロパティが正常に削除を有効にするデータ クラスの別のプロパティ。

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. 関連行を選択、 **O/R デザイナー**エラー メッセージに示されているデータ クラスを接続します。

2. 開く行をダブルクリックして、**関連付けエディター**  ダイアログ ボックス。

3. プロパティを削除、**関連プロパティ**します。

4. プロパティの削除を再試行します。

## <a name="see-also"></a>関連項目

- [O/R デザイナーのメッセージ](../data-tools/o-r-designer-messages.md)
- [Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)