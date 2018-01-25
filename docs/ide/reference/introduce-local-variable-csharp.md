---
title: "ローカル変数の導入 - コード生成 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 6ba9478c09e55df54f94ed93c7a694f798ae76b4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="introduce-a-local-variable-in-c"></a>ローカル変数の導入 (C#) #

**機能:** 既存の式を置換するローカル変数をすぐに生成できます。

**条件:** ローカル変数内で使用されていれば、後で簡単に再利用できるコードがあるとき。

**理由:** コードは複数回コピーして貼り付け、さまざまな場所で使用できるが、一度の実行で、結果を 1 つのローカル変数に格納し、そのローカル変数を全体で使用する方が良いため。

**方法:**

1. 新しいローカル変数に割り当てる式を強調表示します。

   ![強調表示されたコード](media/local-highlight-cs.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **['*expression*' のすべての発生に対してローカルを導入します]** を選択します。ここで、*expression* は強調表示したコードです。
   * **マウス**
     * 右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **['*expression*' のすべての発生に対してローカルを導入します]** を選択します。ここで、*expression* は強調表示したコードです。
     * テキスト カーソルが既に赤い波線の行にある場合は、左余白に表示されている ![電球](media/bulb-cs.png) アイコンをクリックします。

   ![ローカル導入のプレビュー](media/local-preview-cs.png)

   > [!TIP]
   > プレビュー ウィンドウの下部にある [**[変更のプレビュー]** ](../../ide/preview-changes.md) リンクを使用すると、選択を行う前に、行われるすべての変更を確認できます。

1. ローカル変数と、その使用から推論された型が、自動的に作成されます。  入力することで、新しいローカル変数に新しい名前を付けます。

   ![ローカル導入の結果](media/local-result-cs.png)

   > [!NOTE]
   > **[...のすべての発生に対して...]** メニュー オプションを使用すると、実際に強調表示したインスタンスだけではなく、選択した式が見つかったすべてのインスタンスを置換できます。

## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)
