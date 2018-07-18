---
title: Visual Studio でローカル変数を導入する
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 05cf2d99f88fcf6d43674d837d62f2e6053470a9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950466"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Visual Studio でローカル変数を導入する

このコード生成は以下に適用されます。

- C#

- Visual Basic

**機能:** 既存の式を置換するローカル変数をすぐに生成できます。

**条件:** ローカル変数内で使用されていれば、後で簡単に再利用できるコードがあるとき。

**理由:** コードは複数回コピーして貼り付け、さまざまな場所で使用できるが、一度の実行で、結果を 1 つのローカル変数に格納し、そのローカル変数を全体で使用する方が良いため。

## <a name="how-to"></a>方法

1. 新しいローカル変数に割り当てる式を強調表示します。

   - C#: 

    ![強調表示された C# のコード](media/local-highlight-cs.png)

   - Visual Basic: 

    ![強調表示された VB のコード](media/local-highlight-vb.png)

1. 次に、以下のいずれかを実行します。

   - **キーボード**
     - 行の任意の場所で **Ctrl**+**.** キーを押すと、 **[クイック アクションとリファクタリング]** メニューをトリガーします。
   - **マウス**
     - 右クリックして **[クイック アクションとリファクタリング]** メニューを選択します。
     - テキスト カーソルが既に赤い波線の行にある場合は、左余白に表示されている ![電球](media/bulb-cs.png) アイコンをクリックします。

   ![ローカル導入のプレビュー](media/local-preview-cs.png)

1. ドロップダウン メニューから **['<*式*>' のすべての発生に対してローカルを導入します]** を選択します。

   > [!TIP]
   > プレビュー ウィンドウの下部にある **[変更のプレビュー]** リンクを使うと、選択する前に、行われる[すべての変更を確認する](../../ide/preview-changes.md)ことができます。

   ローカル変数と、その使用法から推論された型が作成されます。 新しいローカル変数に新しい名前を付けます。

   - C#: 

      ![インターフェイスの実装の結果 (C#)](media/local-result-cs.png)

   - Visual Basic: 

      ![インターフェイスの実装の結果 (VB)](media/local-result-vb.png)

   > [!NOTE]
   > **[...のすべての発生に対して]** メニュー オプションを使うと、明示的に強調表示したインスタンスだけでなく、選択した式のすべてのインスタンスを置換できます。

## <a name="see-also"></a>関連項目

- [コード生成](../code-generation-in-visual-studio.md)
- [変更のプレビュー](../../ide/preview-changes.md)