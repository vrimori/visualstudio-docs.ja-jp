---
title: 関連付けを作成できません - プロパティが 2 回リストされています
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: db36f6e15a219109fa60ffaed13a01890833ea82
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910858"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>関連付け &lt;関連付けの名前&gt; を作成できません - プロパティが 2 回リストされています

関連付け \<関連付けの名前> を作成できません。 同じプロパティが複数リストされています: "\<property name>"。

関連付けは、**[関連付けエディター]** ダイアログ ボックスで選択された **[関連付けのプロパティ]** によって定義されます。 プロパティは、関連付けのクラスごとに 1 回のみリストできます。

メッセージに示されているプロパティは、Parent クラスまたは Child クラスの **[関連付けのプロパティ]** に複数回表示されます。

## <a name="to-resolve-this-condition"></a>この状況の解決方法

- メッセージを確認し、メッセージで指定されているプロパティに注目します。

- **[OK]** をクリックしてメッセージ ボックスを閉じます。

- **[関連付けのプロパティ]** を調べて、重複エントリを削除します。

- **[OK]** をクリックします。

## <a name="see-also"></a>関連項目

- [O/R デザイナーのメッセージ](../data-tools/o-r-designer-messages.md)
- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [方法: LINQ to SQL クラス (O/R デザイナー) 間のアソシエーションを作成します。](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)