---
title: XML スキーマ デザイナーのコンテンツ モデル ビューを使用して、ノードのコンテンツ モデルを調べる
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 650478a92ea2dabc9aeef239a68bdff428429cd7
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548597"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>方法: コンテンツ モデル ビューを使用して、ノードのコンテンツ モデルを調べる

このトピックを使用してノードを調べる方法について説明、[コンテンツ モデル ビュー](../xml-tools/content-model-view.md)です。

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>新しい XSD ファイルを作成してコンテンツ モデル ビューにルート要素を表示するには

1.  新しい XML スキーマ ファイルを作成します。

2.  をクリックして**を表示および基になる XML スキーマ ファイルを編集する XML エディターを使用して**スタート ビューにします。

3.  XML スキーマのサンプル コードをコピー[サンプルの XML スキーマ: 購買発注書のスキーマ](../xml-tools/sample-xsd-file-purchase-order-schema.md)し、既定では、新しい XSD ファイルに追加されたコードの代わりに貼り付けます。

4.  選択、`purchaseOrder`を右クリックして、スキーマ エクスプ ローラー内の要素、 `purchaseOrder` XML エディターでの要素を選択して**XML エクスプ ローラーで表示**です。

5.  右クリックし、`purchaseOrder`クリックし、XML エクスプ ローラーで**コンテンツ モデル ビューに表示する**です。

     コンテンツ モデル ビューのデザイン サーフェイスに `purchaseOrder` 要素が表示されます。

6.  `shipTo` ノード、`billTo` ノード、および `items` ノードをダブルクリックするか、各ノードの右側にある二重矢印をクリックして、各ノードを展開します。

     これにより `purchaseOrder` 要素のノードが展開され、要素のコンテンツ モデルを確認できます。

7.  `purchaseOrder` 要素のノードをクリックし、階層リンク バーで選択したノードが存在するスキーマ セットの場所を確認します。

8.  クリックして、**ドキュメントを表示**ドキュメントを切り替えるに XSD ツールバーのボタンをクリックします。 デザイン サーフェイスを右クリックして、ドキュメントを切り替えることもできます。

9. クリック、`purchaseOrder`ノード**サンプル XML の生成**に XML インスタンス ドキュメントを参照してください。