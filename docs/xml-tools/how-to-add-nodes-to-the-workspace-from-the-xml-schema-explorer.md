---
title: "方法: XML スキーマ エクスプ ローラーからワークスペースにノードを追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 37da28d4c5db1e008af29c03997943720dcfbada
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>方法: XML スキーマ エクスプローラーからワークスペースにノードを追加する
このトピックにノードを追加する方法について説明、 [XML スキーマ デザイナーのワークスぺース](../xml-tools/xml-schema-designer-workspace.md)XML スキーマ エクスプ ローラーからです。 これは、XML スキーマ エクスプローラーから XSD デザイナーのビューにノードをドラッグ アンド ドロップするか、XML スキーマ エクスプローラーのコンテキスト メニューを使用することによって行うことができます。 さらに、XML スキーマ エクスプローラーの検索結果で強調表示されたノードを追加することができます。 詳細については、次を参照してください。[する方法: スキーマ セット検索結果ノードを追加、ワークスペース](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md)です。  
  
> [!NOTE]
>  グローバル ノードだけに追加することができます、 [XML スキーマ デザイナーのワークスぺース](../xml-tools/xml-schema-designer-workspace.md)です。  
  
### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>XML スキーマ エクスプローラーのコンテキスト メニューからノードを追加するには  
  
1.  手順に従います[する方法: を作成し、XSD スキーマ ファイルを編集](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)です。  
  
2.  XSD エクスプローラーで `PurchaseOrderType` ノードを右クリックします。 選択**グラフ ビューで表示**です。  
  
     `purchaseOrderType` ノードがグラフ ビューのデザイン サーフェイスに表示されます。  
  
### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>ビューにノードをドラッグ アンド ドロップするには  
  
1.  グラフ ビューで `PurchaseOrderType` ノードを右クリックします。 選択**XML スキーマ エクスプ ローラーで表示**です。  
  
     XML スキーマ エクスプローラーにノードが強調表示されます。  
  
2.  右クリックして、`PurchaseOrderType`クリックし、XML スキーマ エクスプ ローラーでノード**すべての参照**です。  
  
     `purchaseOrder` ノードが強調表示されます。  
  
3.  `purchaseOrder` ノードをグラフ ビューにドラッグします。  
  
     `purchaseOrder` ノードおよび `PurchaseOrderType` ノードがグラフ ビューのデザイン サーフェイスに並べて表示されます。 2 つのノードは関連があるため (`purchaseOrder` 要素は `PurchaseOrderType` 型)、これらの間に矢印が引かれます。  
  
### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>スキーマ エクスプローラーの検索機能を使用してノードを追加するには  
  
1.  検索 ボックスに「purchaseOrder」を入力、 [XML エクスプ ローラー](../xml-tools/xml-schema-explorer.md)ツールバーや検索ボタンをクリックします。  
  
     ![XML スキーマ エクスプ ローラー キーワード検索](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     検索結果が XML スキーマ エクスプローラーで強調表示され、垂直スクロール バーのチックでマークされます。  
  
2.  クリックして、ワークスペースに検索結果を追加、**強調表示されたノードをワークスペースに追加**概要結果ペインでボタンをクリックします。  
  
     ![XML スキーマ エクスプ ローラー検索結果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     `purchaseOrder`ノードおよび`PurchaseOrderType`ノードがのデザイン サーフェイスに並べて表示されます、[グラフ ビュー](../xml-tools/graph-view.md)です。 2 つのノードは関連があるため (`purchaseOrder` 要素は `PurchaseOrderType` 型)、これらの間に矢印が引かれます。  
  
## <a name="see-also"></a>参照  
 [XML スキーマ エクスプローラー](../xml-tools/xml-schema-explorer.md)