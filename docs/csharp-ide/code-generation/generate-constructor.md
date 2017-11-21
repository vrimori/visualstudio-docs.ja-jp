---
title: "コンス トラクターのコード生成 (c#) を生成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31b0a187e0640a94d9401a1e20fd03d81ff5b920
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-constructor-in-c"></a>C# の場合、コンス トラクターを生成します。 #
**新機能:**すぐに、クラスの新しいコンス トラクターのコードを生成することができます。 

****する新しいコンス トラクターを紹介し、自動的に正しく宣言します。  

**理由:**が、この機能は、適切なパラメーターを自動的に生成を使用する前に、コンス トラクターを宣言することです。 

**どう：**

1. 行にカーソルを置いてがまだ存在しないコンス トラクターを使用していることを示す赤い波線がある場合。

   ![強調表示されたコード](media/constructor_highlight.png)

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + です。** トリガーを**クイック アクションとリファクタリング**メニュー **のコンス トラクターは生成 '*TypeName*' * * プレビュー ウィンドウのポップアップからです。
   * **マウス**
     * 右クリックし、選択、**クイック アクションとリファクタリング**メニュー **のコンス トラクターは生成 '*TypeName*' * * プレビュー ウィンドウのポップアップからです。
     * 赤の波線をポイントし、をクリックします ![電球](media/bulb.png) 表示されるアイコン。
     * をクリックします ![電球](media/bulb.png) テキストのカーソルは赤の波線では、行に既に存在する場合、左余白に表示されるアイコン。

   ![コンス トラクターのプレビューを生成します。](media/constructor_preview.png)

   >[!TIP]
   >使用して、 [**変更のプレビュー** ](../../ide/preview-changes.md)をすべての選択内容を確定する前に行われる変更を表示するプレビュー ウィンドウの下部にあるリンクします。

1. コンス トラクターは、その使用法から推論しようとするすべてのパラメーターで自動的に作成されます。

   ![コンス トラクターの結果を生成します。](media/constructor_result.png)
  
## <a name="see-also"></a>関連項目  
[コード生成 (C#)](../code-generation-csharp.md)  
[変更のプレビュー](../../ide/preview-changes.md)