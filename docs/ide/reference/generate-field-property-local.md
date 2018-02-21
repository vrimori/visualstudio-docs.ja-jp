---
title: "Visual Studio でフィールド、プロパティ、またはローカル変数を生成する | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 8de048928286017d4e6f79bda6aff804b49d3150
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Visual Studio でフィールド、プロパティ、またはローカル変数を生成する

このコード生成は以下に適用されます。

- C#

- Visual Basic

**機能:** まだ宣言されていないフィールド、プロパティ、またはローカルのコードをすぐに生成できます。

**条件:** 入力中に新しいフィールド、プロパティ、またはローカルを導入して、自動的に適切に宣言したいとき。

**理由:** フィールド、プロパティ、またはローカルは使用する前に自分で宣言できますが、この機能では宣言および型が自動的に生成されます。

## <a name="how-to"></a>方法

1. 赤い波線が表示されている行にカーソルを置きます。 赤い波線は、フィールド、ローカル変数、またはプロパティがまだ存在していないことを示します。

   - C#: 

    ![強調表示された C# のコード](media/field-highlight-cs.png)

   - Visual Basic: 

    ![強調表示された VB のコード](media/field-highlight-vb.png)

1. 次に、以下のいずれかを実行します。

   - **キーボード**
     - **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーします。
   - **マウス**
     - 右クリックして **[クイック アクションとリファクタリング]** メニューを選択します。
     - 赤い波線をポイントし、表示された ![電球](media/bulb-cs.png) アイコンをクリックします。
     - テキスト カーソルが既に赤い波線の行にある場合は、左余白に表示されている ![電球](media/bulb-cs.png) アイコンをクリックします。

    ![フィールド/プロパティ/ローカル生成のプレビュー](media/field-preview-cs.png)

1. ドロップダウン メニューからいずれかの生成オプションを選択します。

   > [!TIP]
   > プレビュー ウィンドウの下部にある **[変更のプレビュー]** リンクを使うと、選択する前に、行われる[すべての変更を確認する](../../ide/preview-changes.md)ことができます。

   フィールド、プロパティ、またはローカル変数と、その使用法から推論された型が作成されます。

   - C#: 

      ![C# のメソッド生成結果](media/field-result-cs.png)

   - Visual Basic: 

      ![VB のメソッド生成結果](media/field-result-vb.png)

## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)
