---
title: "抽象クラスの実装 - コード生成 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cfed7f-f090-4369-8a85-2dcd4c7cf12b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: f089ffbe33d4a36e84d6d39abb3b3db3c4b2aeb7
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2018
---
# <a name="implement-an-abstract-class-in-c"></a>抽象クラスの実装 (C#) #
**機能:** 抽象クラスを実装するために必要なコードをすぐに生成できます。 

**条件:** 抽象クラスから継承したいとき。  

**理由:** すべての抽象メンバーは 1 つずつ 手動で実装できますが、この機能ではすべてのメソッド シグネチャが自動的に生成されます。 

**方法:**

1. 抽象クラスを継承しているが、必要なすべてのメンバーを実装していないことを示す赤い波線がある行にカーソルを置きます。

   ![強調表示されたコード](media/abstract-highlight-cs.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[抽象クラスの実装]** を選択します。
   * **マウス**
     * 右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[抽象クラスの実装]** を選択します。
     * 赤い波線をポイントし、表示された ![電球](media/bulb-cs.png) アイコンをクリックします。
     * テキスト カーソルが既に赤い波線の行にある場合は、左余白に表示されている ![電球](media/bulb-cs.png) アイコンをクリックします。

   ![クラス実装のプレビュー](media/abstract-preview-cs.png)

   >[!TIP]
   >プレビュー ウィンドウの下部にある [**[変更のプレビュー]** ](../../ide/preview-changes.md) リンクを使用すると、選択を行う前に、行われるすべての変更を確認できます。
   >
   >また、[プレビュー] ウィンドウ下部にある **[ドキュメント]** リンク、**[プロジェクト]** リンク、および **[ソリューション]** リンクを使用して、抽象クラスから継承する複数のクラスにまたがる適切なメソッド シグネチャを作成できます。

1. 抽象メソッドのシグネチャが自動的に作成され、実装する準備が整います。

   ![クラス実装の結果](media/abstract-result-cs.png)

## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)
