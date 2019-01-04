---
title: XML スキーマ デザイナーで、コンテンツ モデル ビューを使用してノードのコンテンツ モデルを調べる
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f698ab9c26b417c8f88a993863f50e0c3df574d2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936101"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>方法: コンテンツ モデル ビューを使用してノードのコンテンツ モデルを調べる

このトピックを使用してノードを探索する方法を説明します、[コンテンツ モデル ビュー](../xml-tools/content-model-view.md)します。

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>新しい XSD ファイルを作成してコンテンツ モデル ビューにルート要素を表示するには

1.  新しい XML スキーマ ファイルを作成します。

2.  をクリックして**XML エディターを使用して表示および基になる XML スキーマ ファイルを編集して**スタート ビューにします。

3.  XML スキーマのサンプル コードをコピー[サンプルの XML スキーマ: 購買発注書のスキーマ](../xml-tools/sample-xsd-file-purchase-order-schema.md)してそれを既定では、新しい XSD ファイルに追加されたコードに置き換えます。

4.  選択、`purchaseOrder`を右クリックし、スキーマ エクスプ ローラー内の要素、`purchaseOrder`要素、XML エディターで選択して**XML エクスプ ローラーで表示する**。

5.  右クリックし、 `purchaseOrder` XML エクスプ ローラーを選び**コンテンツ モデル ビューに表示する**します。

     コンテンツ モデル ビューのデザイン サーフェイスに `purchaseOrder` 要素が表示されます。

6.  `shipTo` ノード、`billTo` ノード、および `items` ノードをダブルクリックするか、各ノードの右側にある二重矢印をクリックして、各ノードを展開します。

     これにより `purchaseOrder` 要素のノードが展開され、要素のコンテンツ モデルを確認できます。

7.  `purchaseOrder` 要素のノードをクリックし、階層リンク バーで選択したノードが存在するスキーマ セットの場所を確認します。

8.  をクリックして、**ドキュメントを表示**ドキュメントを切り替えるには、XSD ツールバーのボタンをクリックします。 デザイン サーフェイスを右クリックして、ドキュメントを切り替えることもできます。

9. 右クリックして、`purchaseOrder`ノード**サンプル XML の生成**に XML インスタンス ドキュメントを参照してください。