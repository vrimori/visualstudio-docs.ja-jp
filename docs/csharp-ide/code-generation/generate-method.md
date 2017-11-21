---
title: "Generate メソッドのコード生成 (c#) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 626db0d9c62fc606539fc9d72fc14c3651dca7ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-method-in-c"></a>メソッドを生成する (C#) #
**新機能:**クラスにメソッドをすぐに追加することができます。 

****新しいメソッドを導入して、自動的に正しく宣言します。  

**理由:**でしたを宣言するメソッドとパラメーターを使用する前に、この機能は、宣言を自動的に生成されます。 

**どう：**

1. 行にカーソルを置いてがまだ存在しないメソッドを使用したことを示す赤い波線がある場合。

   ![強調表示されたコード](media/method_highlight.png)

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + です。** トリガーを**クイック アクションとリファクタリング**メニュー**メソッドを生成**プレビュー ウィンドウのポップアップからです。
   * **マウス**
     * 右クリックし、選択、**クイック アクションとリファクタリング**メニュー**メソッドを生成**プレビュー ウィンドウのポップアップからです。
     * 赤の波線をポイントし、をクリックします ![電球](media/bulb.png) 表示されるアイコン。
     * をクリックします ![電球](media/bulb.png) テキストのカーソルは赤の波線では、行に既に存在する場合、左余白に表示されるアイコン。

   ![メソッドのプレビューを生成します。](media/method_preview.png)

   >[!TIP]
   >使用して、 [**変更のプレビュー** ](../../ide/preview-changes.md)をすべての選択内容を確定する前に行われる変更を表示するプレビュー ウィンドウの下部にあるリンクします。

1. メソッドは、その使用法から推論しようとするすべてのパラメーターで自動的に作成されます。

   ![メソッドの結果を生成します。](media/method_result.png)

## <a name="see-also"></a>関連項目  
[コード生成 (C#)](../code-generation-csharp.md)  
[変更のプレビュー](../../ide/preview-changes.md)
