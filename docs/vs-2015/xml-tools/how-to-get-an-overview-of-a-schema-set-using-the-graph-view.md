---
title: '方法: グラフ ビューを使用してスキーマ セットの概要を説明 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0b7c3d1d9f351e496469e5b13552ec78e1548f5c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547942"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>方法: グラフ ビューを使用してスキーマ セットの概要を表示する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: グラフ ビューの設定を使用してスキーマの概要を把握](https://docs.microsoft.com/visualstudio/xml-tools/how-to-get-an-overview-of-a-schema-set-using-the-graph-view)します。  
  
  
このトピックでは、使用する方法を説明します、[グラフ ビュー](../xml-tools/graph-view.md)スキーマ セットと、ノード間のリレーションシップ内のノードの高度なビューを表示します。  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>新しい XSD ファイルを作成してコンテンツ モデル ビューにルート要素を表示するには  
  
1.  新しい XML スキーマ ファイルを作成して、Relationships.xsd という名前でファイルを保存します。  
  
2.  をクリックして、 **XML エディターを使用して表示および基になる XML スキーマ ファイルを編集して**スタート ビューにリンクします。  
  
3.  XML スキーマのサンプル コードをコピー[サンプルの XML スキーマ: リレーションシップ](../xml-tools/sample-xsd-file-relationships.md)してそれを既定では、新しい XSD ファイルに追加されたコードに置き換えます。  
  
4.  XML エディター内を右クリックし、選択**ビュー デザイナー**します。  
  
5.  XSD ツール バーからグラフ ビューを選択します。  
  
6.  選択**スキーマ セット**グラフ ビューのデザイン サーフェイスには、XML スキーマ エクスプ ローラーとドラッグ、ノード内のノード。 すべてのグローバル ノードが表示され、リレーションシップを持つノード間に矢印が引かれます。  
  
     ![グラフ ビュー](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7.  デザイン サーフェイスでノードをクリックし、階層リンク バーで選択したノードが存在するスキーマ セットの場所を確認します。  
  
8.  選択し、画面のデザイン上の任意の要素ノードを右クリック**サンプル XML の生成**に XML インスタンス ドキュメントを参照してください。



