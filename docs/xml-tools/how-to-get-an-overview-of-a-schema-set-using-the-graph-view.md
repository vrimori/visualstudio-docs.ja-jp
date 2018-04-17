---
title: '方法: グラフ ビューを使用してスキーマ セットの概要を説明 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 145a55312d042811b0d51d46136078657d10fee1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>方法: グラフ ビューを使用してスキーマ セットの概要を表示する
このトピックを使用する方法について説明、[グラフ ビュー](../xml-tools/graph-view.md)スキーマ セットと、ノード間のリレーションシップ内のノードの高度なビューを表示します。  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>新しい XSD ファイルを作成してコンテンツ モデル ビューにルート要素を表示するには  
  
1.  新しい XML スキーマ ファイルを作成して、Relationships.xsd という名前でファイルを保存します。  
  
2.  クリックして、**を表示および基になる XML スキーマ ファイルを編集する XML エディターを使用して**スタート ビューにリンクします。  
  
3.  XML スキーマのサンプル コードをコピー[サンプル XML スキーマ: リレーションシップ](../xml-tools/sample-xsd-file-relationships.md)し、既定では、新しい XSD ファイルに追加されたコードの代わりに貼り付けます。  
  
4.  XML エディター内を右クリックし、選択**ビュー デザイナー**です。  
  
5.  XSD ツール バーからグラフ ビューを選択します。  
  
6.  選択**スキーマ セット**グラフ ビューのデザイン サーフェイスには、XML スキーマ エクスプ ローラーとドラッグ ノード内のノードです。 すべてのグローバル ノードが表示され、リレーションシップを持つノード間に矢印が引かれます。  
  
     ![グラフ ビュー](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7.  デザイン サーフェイスでノードをクリックし、階層リンク バーで選択したノードが存在するスキーマ セットの場所を確認します。  
  
8.  要素ノードを右クリックし、画面のデザイン上のクリック**サンプル XML の生成**に XML インスタンス ドキュメントを参照してください。