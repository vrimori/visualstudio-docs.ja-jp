---
title: "コード生成 (c#) のインターフェイスを実装 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e37cda45519062564e45127f8b8f329b75caa9a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="implement-an-interface-in-c"></a>C# でのインターフェイスを実装します。 #
**新機能:**直ちにインターフェイスを実装するために必要なコードを生成することができます。 

****インターフェイスから継承します。  

**理由:**でした手動でインターフェイスを実装するすべて 1 つずつ、ただし、この機能では、すべてのメソッド署名を自動的に作成されます。 

**どう：**

1. 行にカーソルを置きますが、インターフェイスを参照しているが、必要なすべてのメンバーを実装していないことを示す赤い波線がある場合。

   ![強調表示されたコード](media/interface_highlight.png)

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + です。** トリガーを**クイック アクションとリファクタリング**メニュー **(明示的) インターフェイスを実装**プレビュー ウィンドウのポップアップからです。
   * **マウス**
     * 右クリックし、選択、**クイック アクションとリファクタリング**メニュー **(明示的) インターフェイスを実装して**プレビュー ウィンドウのポップアップからです。
     * 赤の波線をポイントし、をクリックします ![電球](media/bulb.png) 表示されるアイコン。
     * をクリックします ![電球](media/bulb.png) テキストのカーソルは赤の波線では、行に既に存在する場合、左余白に表示されるアイコン。

   ![実装クラスのプレビュー](media/interface_preview.png)

   >[!TIP]
   >使用して、 [**変更のプレビュー** ](../../ide/preview-changes.md)をすべての選択内容を確定する前に行われる変更を表示するプレビュー ウィンドウの下部にあるリンクします。
   >
   >また、使用することができます、**ドキュメント**、**プロジェクト**、および**ソリューション**を適切なメソッドのシグネチャを複数作成するプレビュー ウィンドウの下部にあるリンクインターフェイスを実装するクラス。

1. インターフェイスのメソッドのシグネチャは、自動的に作成された、実装する準備完了になります。

   ![クラスの結果を実装します。](media/interface_result.png)

   >[!TIP]
   >使用して、**インターフェイスを明示的に実装**生成された名前の衝突を避けるためにインターフェイス名とメソッドのそれぞれの先頭にはオプションです。
   >
   >![明示的に発生するインターフェイスの実装](media/interface_explicitresult.png); 

## <a name="see-also"></a>関連項目  
[コード生成 (C#)](../code-generation-csharp.md)  
[変更のプレビュー](../../ide/preview-changes.md)  
