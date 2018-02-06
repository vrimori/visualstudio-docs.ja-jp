---
title: "フィールド、プロパティ、またはローカルの生成 - コード生成 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 766311f0ba165c87e61bb873baa3ab2f0b2d1402
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-field-property-or-local-in-visual-basic"></a>フィールド、プロパティ、またはローカルの生成 (Visual Basic)
**機能:** まだ宣言されていないフィールド、プロパティ、またはローカルのコードをすぐに生成できます。 

**条件:** 入力中に新しいフィールド、プロパティ、またはローカルを導入して、自動的に適切に宣言したいとき。  

**理由:** フィールド、プロパティ、またはローカルは使用する前に自分で宣言できますが、この機能では宣言および型が自動的に生成されます。 

**方法:**

1. まだ存在しないフィールド、ローカル、またはプロパティを使用したことを示す赤い波線がある行にカーソルを置きます。

   ![強調表示されたコード](media/field-highlight-vb.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[変数 '*Name*' を生成する] > [フィールド/プロパティ/ローカルを生成する]** の順に選択します。
   * **マウス**
     * 右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[変数 '*Name*' を生成する] > [フィールド/プロパティ/ローカルを生成する]** の順に選択します。
     * 赤い波線をポイントし、表示された ![電球](media/bulb-vb.png) アイコンをクリックします。
     * テキスト カーソルが既に赤の波線が表示されている行にある場合は、左余白に表示されている ![電球](media/bulb-vb.png) アイコンをクリックします。

   ![フィールド/プロパティ/ローカル生成のプレビュー](media/field-preview-vb.png)

   >[!TIP]
   >プレビュー ウィンドウの下部にある [**[変更のプレビュー]** ](../../ide/preview-changes.md) リンクを使用すると、選択を行う前に、行われるすべての変更を確認できます。

1. フィールド、プロパティ、またはローカルと、その使用から推論された型が、自動的に作成されます。

   ![フィールド/プロパティ/ローカル生成の結果](media/field-result-vb.png)

## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)