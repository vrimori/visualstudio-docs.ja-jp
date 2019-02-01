---
title: プロパティは関連付けに関与しているため、削除できません
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 32eeef65eaf8cfebbce0458b90f954bf491f718a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997963"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>プロパティ &lt;プロパティ名&gt; は関連付け &lt;関連付けの名前&gt; に関与しているため、削除できません

選択されたプロパティは、エラー メッセージに示されているクラス間の関連付けに対する**関連付けプロパティ**として設定されています。 プロパティがデータ クラス間の関連付けに関与している場合、そのプロパティを削除することはできません。

**関連付けプロパティ**をデータ クラスの別のプロパティに設定して、目的のプロパティが正常に削除されるようにします。

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. **O/R デザイナー**で、エラー メッセージに示されているデータ クラスを接続する関連行を選択します。

2. 行をダブルクリックして、**[関連付けエディター]** ダイアログ ボックスを開きます。

3. **[関連付けのプロパティ]** からプロパティを削除します。

4. プロパティの削除を再試行します。

## <a name="see-also"></a>関連項目

- [O/R デザイナーのメッセージ](../data-tools/o-r-designer-messages.md)
- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)