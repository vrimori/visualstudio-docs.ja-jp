---
title: "Visual Studio でメソッドを生成する | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 6fbee2d6ea0a6d95d6d71114dc116cfaa1ede74e
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="generate-a-method-in-visual-studio"></a>Visual Studio でメソッドを生成する

このコード生成は以下に適用されます。

- C#

- Visual Basic

**概要:** クラスにメソッドをすぐに追加できます。

**条件:** 新しいメソッドを導入し、自動的に適切に宣言したいとき。

**理由:** メソッドとパラメーターは使用する前に自分でも宣言できるが、この機能では自動的に宣言が生成されるため。

## <a name="how-to"></a>方法

1. 赤い波線が表示されている行にカーソルを置きます。 赤い波線は、まだ存在していないメソッドを示します。

   - C#: 

    ![強調表示された C# のコード](media/method-highlight-cs.png)

   - Visual Basic: 

    ![強調表示された VB のコード](media/method-highlight-vb.png)

1. 次に、以下のいずれかを実行します。

   - **キーボード**
     - **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーします。
   - **マウス**
     - 右クリックして **[クイック アクションとリファクタリング]** メニューを選択します。
     - 赤い波線をポイントし、表示された ![電球](media/bulb-cs.png) アイコンをクリックします。
     - テキスト カーソルが既に赤い波線の行にある場合は、左余白に表示されている ![電球](media/bulb-cs.png) アイコンをクリックします。

    ![メソッド生成のプレビュー](media/method-preview-cs.png)

1. ドロップダウン メニューから **[メソッドの生成]** を選択します。

   > [!TIP]
   > プレビュー ウィンドウの下部にある **[変更のプレビュー]** リンクを使うと、選択する前に、行われる[すべての変更を確認する](../../ide/preview-changes.md)ことができます。

   メソッドと、その使用法から推論されるすべてのパラメーターが作成されます。

   - C#: 

      ![C# のメソッド生成結果](media/method-result-cs.png)

   - Visual Basic: 

      ![VB のメソッド生成結果](media/method-result-vb.png)

## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)
