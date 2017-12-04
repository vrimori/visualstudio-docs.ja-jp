---
title: "Equals や GetHashCode メソッド オーバーライドしますコード生成 (c#) 生成 |。Microsoft ドキュメント"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.openlocfilehash: 88ebbeed4af1d0ea79a27ff21f7ae38ec8c252c1
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/29/2017
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>Equals を生成し、c# で GetHashCode メソッドのオーバーライド #

**新機能:**を生成できます**Equals**と**GetHashCode**メソッドです。

**と比較**するいくつかのフィールドでの代わりに、メモリ内のオブジェクトの場所を「値」を表す型がある場合は、これらのオーバーライドを生成します。

**理由:**値の型を実装している場合は、値型で Equals メソッドの既定の実装でパフォーマンスの向上を取得するために Equals メソッドのオーバーライドを検討してください。

参照型を実装している場合は、Equals メソッドのオーバーライドの種類は、ポイント、文字列、BigNumber などの基本型のように見える場合を検討してください。

ハッシュ テーブルに正常に機能する型を許可する GetHashCode メソッドをオーバーライドします。 よりのガイダンスを読み取る[等値演算子](/dotnet/standard/design-guidelines/equality-operators)です。

**どう：**

1. 型の宣言でカーソルを置きます。

   ![強調表示されたコード](media/overrides_highlight.png)

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + です。** トリガーに、**クイック アクションとリファクタリング**メニュー**生成 Equals(object)**または**生成 Equals や GetHashCode**プレビュー ウィンドウのポップアップからです。
   * **マウス**
     * 右クリックし、選択、**クイック アクションとリファクタリング**メニュー**生成 Equals(object)**または**生成 Equals や GetHashCode**のプレビュー ウィンドウからポップアップ。
     * をクリックします ![電球](media/bulb.png) テキストのカーソルは、型宣言では、行に既に存在する場合、左余白に表示されるアイコン。

   ![上書きのプレビューを生成します。](media/overrides_preview.png)

1. オーバーライド メソッドを生成するメンバーを選択してください。

    ![ダイアログの上書きを生成します。](media/overrides_dialog.png)

    > [!TIP]
    > メンバーの一覧の下にあるチェック ボックスを使用して、このダイアログ ボックスから演算子を生成することもできます。

1. Equals や GetHashCode 自動の既定の実装によってオーバーライドが生成されます。

   ![メソッドの結果を生成します。](media/overrides_result.png)

## <a name="see-also"></a>参照

[コード生成 (C#)](../code-generation-csharp.md)  
[変更のプレビュー](../../ide/preview-changes.md)
