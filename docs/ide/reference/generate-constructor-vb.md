---
title: "コンストラクターの生成 - コード生成 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 891a33b74927d45434c4614dc4c5d7f1533ba4c0
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-constructor-in-visual-basic"></a>コンストラクターの生成 (Visual Basic)
**機能:** クラスの新しいコンストラクターのコードをすぐに生成できます。 

**条件:** 新しいコンストラクターを導入し、自動的に適切に宣言したいとき。  

**理由:** コンストラクターは使用する前に自分で宣言できますが、この機能ではコンストラクターと適切なパラメーターが自動的に生成されます。 

**方法:**

1. まだ存在しないコンストラクターを使用したことを示す赤い波線がある行にカーソルを置きます。

   ![強調表示されたコード](media/constructor-highlight-vb.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **['*TypeName*' にコンストラクターを生成します]** を選択します。
   * **マウス**
     * 右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **['*TypeName*' にコンストラクターを生成します]** を選択します。
     * 赤い波線をポイントし、表示された ![電球](media/bulb-vb.png) アイコンをクリックします。
     * テキスト カーソルが既に赤い波線の行にある場合は、左余白に表示されている ![電球](media/bulb-vb.png) アイコンをクリックします。

   ![コンストラクター生成のプレビュー](media/constructor-preview-vb.png)

   >[!TIP]
   >プレビュー ウィンドウの下部にある [**[変更のプレビュー]** ](../../ide/preview-changes.md) リンクを使用すると、選択を行う前に、行われるすべての変更を確認できます。

1. コンストラクターと、その使用から推論されたすべてのパラメーターが、自動的に作成されます。

   ![コンストラクター生成の結果](media/constructor-result-vb.png)
 
## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)