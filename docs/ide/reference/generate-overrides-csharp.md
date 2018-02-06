---
title: "Equals および GetHashCode メソッドの上書きの生成 - コード生成 (C#) | Microsoft Docs"
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
ms.workload: dotnet
ms.openlocfilehash: 56b1753dbdcfbf8ce318e964a16879f02b1482c4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>Equals および GetHashCode メソッドの上書きの生成 (C#) #

**概要:** **Equals** メソッドと **GetHashCode** メソッドを生成します。

**タイミング:** これらの上書きは、メモリ内のオブジェクトの場所ではなく、フィールドによって比較される「値」を表す型がある場合に生成します。

**理由:** 値の型を実装する場合、Equals メソッドの上書きは、ValueType の Equals メソッドの既定の実装を上回るパフォーマンスを得ることを目的として検討してください。

参照型を実装する場合、Equals メソッドの上書きは、型がポイント、文字列、BigNumber などの基本データ型に似ている場合に検討してください。

GetHashCode メソッドの上書きは、ハッシュ テーブル内で型を正常に機能させることを目的として行います。 詳細については[等値演算子](/dotnet/standard/design-guidelines/equality-operators)のガイドラインをご覧ください。

**方法:**

1. 型宣言にカーソルを置きます。

   ![強調表示されたコード](media/overrides-highlight-cs.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[Equals(object) を生成する ]** または **[Equals および GetHashCode を生成する]** を選択します。
   * **マウス**
     * 右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[Equals(object) を生成する ]** または **[Equals および GetHashCode を生成する]** を選択します。
     * テキスト カーソルが既に赤い波線の行にある場合は、左余白に表示されている ![電球](media/bulb-cs.png) アイコンをクリックします。

   ![上書き生成のプレビュー](media/overrides-preview-cs.png)

1. 上書きメソッドを生成するメソッドを選択します。

    ![[上書きを生成する] ダイアログ](media/overrides-dialog-cs.png)

    > [!TIP]
    > メンバーの一覧の下にあるチェックボックスを使って、このダイアログから演算子を生成することもできます。

1. Equals の上書きと GetHashCode の上書きが、自動の既定の実装で生成されます。

   ![メソッド生成の結果](media/overrides-result-cs.png)

## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)
