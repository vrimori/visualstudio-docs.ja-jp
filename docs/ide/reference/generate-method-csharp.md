---
title: "メソッドの生成 - コード生成 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: e4caf80bec38305613111f290b80eafb74547598
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-method-in-c"></a>メソッドの生成 (C#) #
**機能:** クラスにメソッドをすぐに追加できます。 

**条件:** 新しいメソッドを導入し、自動的に適切に宣言したいとき。  

**理由:** メソッドとパラメーターは使用する前に自分でも宣言できるが、この機能では自動的に宣言が生成されるため。 

**方法:**

1. 赤い波線がある行にカーソルを移動します。この波線は、使用したメソッドがまだ存在しないものであることを示しています。

   ![強調表示されたコード](media/method-highlight-cs.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[メソッドの生成]** を選択します。
   * **マウス**
     * 右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[メソッドの生成]** を選択します。
     * 赤い波線をポイントし、表示された ![電球](media/bulb-cs.png) アイコンをクリックします。
     * テキスト カーソルが既に赤い波線の行にある場合は、左余白に表示されている ![電球](media/bulb-cs.png) アイコンをクリックします。

   ![メソッド生成のプレビュー](media/method-preview-cs.png)

   >[!TIP]
   >プレビュー ウィンドウの下部にある [**[変更のプレビュー]** ](../../ide/preview-changes.md) リンクを使用すると、選択を行う前に、行われるすべての変更を確認できます。

1. メソッドと、その使用から推論されたすべてのパラメーターが、自動的に作成されます。

   ![メソッド生成の結果](media/method-result-cs.png)

## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)
