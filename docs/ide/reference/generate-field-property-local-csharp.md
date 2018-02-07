---
title: "フィールド、プロパティ、またはローカルの生成 - コード生成 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 7cc27d498cbc082ad76d47d2326d1ee8fb0ebbb0
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-field-property-or-local-in-c"></a>フィールド、プロパティ、またはローカルの生成 (C#) #
**機能:** まだ宣言されていないフィールド、プロパティ、またはローカルのコードをすぐに生成できます。 

**条件:** 入力中に新しいフィールド、プロパティ、またはローカルを導入して、自動的に適切に宣言したいとき。  

**理由:** フィールド、プロパティ、またはローカルは使用する前に自分で宣言できますが、この機能では宣言および型が自動的に生成されます。 

**方法:**

1. まだ存在しないフィールド、ローカル、またはプロパティを使用したことを示す赤い波線がある行にカーソルを置きます。

   ![強調表示されたコード](media/field-highlight-cs.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[フィールド/プロパティ/ローカルを生成する]** を選択します。
   * **マウス**
     * 右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[フィールド/プロパティ/ローカルを生成する]** を選択します。
     * 赤い波線をポイントし、表示された ![電球](media/bulb-cs.png) アイコンをクリックします。
     * テキスト カーソルが既に赤い波線の行にある場合は、左余白に表示されている ![電球](media/bulb-cs.png) アイコンをクリックします。

   ![フィールド/プロパティ/ローカル生成のプレビュー](media/field-preview-cs.png)

   >[!TIP]
   >プレビュー ウィンドウの下部にある [**[変更のプレビュー]** ](../../ide/preview-changes.md) リンクを使用すると、選択を行う前に、行われるすべての変更を確認できます。

1. フィールド、プロパティ、またはローカルと、その使用から推論された型が、自動的に作成されます。

   ![フィールド/プロパティ/ローカル生成の結果](media/field-result-cs.png)

## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)
