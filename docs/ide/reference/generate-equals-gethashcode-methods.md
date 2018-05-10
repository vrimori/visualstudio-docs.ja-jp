---
title: Visual Studio で C# Equals および GetHashCode メソッドのオーバーライドを生成する
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: cdbb5273d046be8f11cc2fbc4a03ed6767a31e00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Visual Studio で Equals および GetHashCode メソッドのオーバーライドを生成する

このコード生成は以下に適用されます。

- C#

**概要:** **Equals** メソッドと **GetHashCode** メソッドを生成します。

**タイミング:** これらのオーバーライドは、メモリ内のオブジェクトの場所ではなく、1 つ以上のフィールドによって比較される型がある場合に生成されます。

**理由:**

- 値の型を実装する場合、ValueType の Equals メソッドの既定の実装を上回るパフォーマンスを得るには、**Equals** メソッドのオーバーライドを検討する必要があります。

- 参照型を実装する場合、型が Point、String、BigNumber などの基本データ型に似ているときは、**Equals** メソッドのオーバーライドを検討する必要があります。

- ハッシュ テーブルで型を正しく機能させるには、**GetHashCode** メソッドをオーバーライドします。 詳細については[等値演算子](/dotnet/standard/design-guidelines/equality-operators)のガイドラインをご覧ください。

## <a name="how-to"></a>方法

1. 型宣言にカーソルを置きます。

   ![強調表示されたコード](media/overrides-highlight-cs.png)

1. 次に、以下のいずれかを実行します。

   - **キーボード**
     - 行の任意の場所で **Ctrl**+**.** キーを押すと、 **[クイック アクションとリファクタリング]** メニューをトリガーします。
   - **マウス**
     - 右クリックして **[クイック アクションとリファクタリング]** メニューを選択します。
     - テキスト カーソルが既に赤い波線の行にある場合は、左余白に表示されている ![電球](media/bulb-cs.png) アイコンをクリックします。

   ![上書き生成のプレビュー](media/overrides-preview-cs.png)

1. ドロップダウン メニューから **[Equals(object) を生成する]** または **[Equals および GetHashCode を生成する]** を選択します。

1. **[メンバーの選択]** ダイアログ ボックスで、メソッドを生成するメンバーを選択します。

    ![[上書きを生成する] ダイアログ](media/overrides-dialog-cs.png)

    > [!TIP]
    > メンバーの一覧の下にあるチェックボックスを使って、このダイアログから演算子を生成することもできます。

   Equals と GetHashCode のオーバーライドが、既定の実装で生成されます。

   ![メソッド生成の結果](media/overrides-result-cs.png)

## <a name="see-also"></a>関連項目

- [コード生成](../code-generation-in-visual-studio.md)
- [変更のプレビュー](../../ide/preview-changes.md)