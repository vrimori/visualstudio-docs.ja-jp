---
title: "方法: コンテンツ モデル ビューを使用して、ノードのコンテンツ モデルを調べる |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4856554b92f5689e17141004b7d4e0ffe5e781cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>方法: コンテンツ モデル ビューを使用してノードのコンテンツ モデルを調べる
このトピックを使用してノードを調べる方法について説明、[コンテンツ モデル ビュー](../xml-tools/content-model-view.md)です。  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>新しい XSD ファイルを作成してコンテンツ モデル ビューにルート要素を表示するには  
  
1.  新しい XML スキーマ ファイルを作成します。  
  
2.  をクリックして**を表示および基になる XML スキーマ ファイルを編集する XML エディターを使用して**スタート ビューにします。  
  
3.  XML スキーマのサンプル コードをコピー[サンプル XML スキーマ: 購買発注書スキーマ](../xml-tools/sample-xsd-file-purchase-order-schema.md)し、既定では、新しい XSD ファイルに追加されたコードの代わりに貼り付けます。  
  
4.  選択、`purchaseOrder`を右クリックして、スキーマ エクスプ ローラー内の要素、 `purchaseOrder` XML エディターでの要素を選択して**XML エクスプ ローラーで表示**です。  
  
5.  右クリックし、`purchaseOrder`クリックし、XML エクスプ ローラーで**コンテンツ モデル ビューに表示する**です。  
  
     コンテンツ モデル ビューのデザイン サーフェイスに `purchaseOrder` 要素が表示されます。  
  
6.  `shipTo` ノード、`billTo` ノード、および `items` ノードをダブルクリックするか、各ノードの右側にある二重矢印をクリックして、各ノードを展開します。  
  
     これにより `purchaseOrder` 要素のノードが展開され、要素のコンテンツ モデルを確認できます。  
  
7.  `purchaseOrder` 要素のノードをクリックし、階層リンク バーで選択したノードが存在するスキーマ セットの場所を確認します。  
  
8.  クリックして、**ドキュメントを表示**ドキュメントを切り替えるに XSD ツールバーのボタンをクリックします。 デザイン サーフェイスを右クリックして、ドキュメントを切り替えることもできます。  
  
9. クリック、`purchaseOrder`ノード**サンプル XML の生成**に XML インスタンス ドキュメントを参照してください。