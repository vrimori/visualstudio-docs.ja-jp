---
title: "インターフェイスの実装 - コード生成 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 990f87cd0f1abf9d4f62ecd321ef038d689b75f4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2018
---
# <a name="implement-an-interface-in-visual-basic"></a>インターフェイスの実装 (Visual Basic)
**機能:** インターフェイスを実装するために必要なコードをすぐに生成できます。 

**条件:** インターフェイスから継承したいとき。  

**理由:** すべてのインターフェイスは 1 つずつ 手動で実装できますが、この機能ではすべてのメソッド シグネチャが自動的に生成されます。 

**方法:**

1. インターフェイスを参照しているが、必要なすべてのメンバーを実装していないことを示す赤い波線がある行にカーソルを置きます。

   ![強調表示されたコード](media/interface-highlight-vb.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[インターフェイスの実装 (明示的)]** を選択します。
   * **マウス**
     * 右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[インターフェイスの実装 (明示的)]** を選択します。
     * 赤い波線をポイントし、表示された ![電球](media/bulb-vb.png) アイコンをクリックします。
     * テキスト カーソルが既に赤い波線の行にある場合は、左余白に表示されている ![電球](media/bulb-vb.png) アイコンをクリックします。

   ![クラス実装のプレビュー](media/interface-preview-vb.png)

   >[!TIP]
   >プレビュー ウィンドウの下部にある [**[変更のプレビュー]** ](../../ide/preview-changes.md) リンクを使用すると、選択を行う前に、行われるすべての変更を確認できます。
   >
   >また、[プレビュー] ウィンドウ下部にある **[ドキュメント]** リンク、**[プロジェクト]** リンク、および **[ソリューション]** リンクを使用して、インターフェイスを実装する複数のクラスにまたがる適切なメソッド シグネチャを作成できます。

1. インターフェイスのメソッド シグネチャが自動的に作成され、実装する準備が整います。

   ![クラス実装の結果](media/interface-result-vb.png)

## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)