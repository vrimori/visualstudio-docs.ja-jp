---
title: '方法: コンテンツ モデル ビューを使用してノードのコンテンツ モデルを調べる. |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 25e47eed752a78caebcbae66a527cc847ac7d8f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533770"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>方法: コンテンツ モデル ビューを使用してノードのコンテンツ モデルを調べる
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: コンテンツ モデル ビューをモデルのノードを使用してコンテンツを調べる](https://docs.microsoft.com/visualstudio/xml-tools/how-to-examine-the-content-model-of-nodes-using-the-content-model-view)します。  
  
  
このトピックを使用してノードを探索する方法を説明します、[コンテンツ モデル ビュー](../xml-tools/content-model-view.md)します。  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>新しい XSD ファイルを作成してコンテンツ モデル ビューにルート要素を表示するには  
  
1.  新しい XML スキーマ ファイルを作成します。  
  
2.  をクリックして**XML エディターを使用して表示および基になる XML スキーマ ファイルを編集して**スタート ビューにします。  
  
3.  XML スキーマのサンプル コードをコピー[サンプルの XML スキーマ: 購買発注書スキーマ](../xml-tools/sample-xsd-file-purchase-order-schema.md)してそれを既定では、新しい XSD ファイルに追加されたコードに置き換えます。  
  
4.  選択、`purchaseOrder`を右クリックし、スキーマ エクスプ ローラー内の要素、`purchaseOrder`要素、XML エディターで選択して**XML エクスプ ローラーで表示する**。  
  
5.  右クリックし、 `purchaseOrder` XML エクスプ ローラーを選び**コンテンツ モデル ビューに表示する**します。  
  
     コンテンツ モデル ビューのデザイン サーフェイスに `purchaseOrder` 要素が表示されます。  
  
6.  `shipTo` ノード、`billTo` ノード、および `items` ノードをダブルクリックするか、各ノードの右側にある二重矢印をクリックして、各ノードを展開します。  
  
     これにより `purchaseOrder` 要素のノードが展開され、要素のコンテンツ モデルを確認できます。  
  
7.  `purchaseOrder` 要素のノードをクリックし、階層リンク バーで選択したノードが存在するスキーマ セットの場所を確認します。  
  
8.  をクリックして、**ドキュメントを表示**ドキュメントを切り替えるには、XSD ツールバーのボタンをクリックします。 デザイン サーフェイスを右クリックして、ドキュメントを切り替えることもできます。  
  
9. 右クリックして、`purchaseOrder`ノード**サンプル XML の生成**に XML インスタンス ドキュメントを参照してください。



