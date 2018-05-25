---
title: XML スキーマ セットの検索結果ノードをワークスペースに追加します。
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f6629aef7549a78f7cfdb73bb6d7ee0be3ac7412
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>方法: スキーマ セットの検索結果のノードをワークスペースに追加します。

ここで強調表示されているノードを追加する方法について説明、 **XML スキーマ エクスプ ローラー**  ワークスペースで、キーワード検索の結果として。

> [!NOTE]
> グローバル ノードだけに追加することができます、[ワークスペース](../xml-tools/xml-schema-designer-workspace.md)です。


 この例は、サンプルを使用して[購買発注書のスキーマ](../xml-tools/sample-xsd-file-purchase-order-schema.md)です。

## <a name="to-add-schema-set-result-nodes"></a>スキーマ セットの検索結果のノードを追加するには

1.  手順に従います[する方法: を作成し、XSD スキーマ ファイルを編集](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)です。

2.  検索 ボックスに「purchaseOrder」を入力、 [XML エクスプ ローラー](../xml-tools/xml-schema-explorer.md)ツールバーや検索ボタンをクリックします。

     ![XML スキーマ エクスプ ローラー キーワード検索](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     検索結果が強調表示されて、 **XML スキーマ エクスプ ローラー**垂直スクロール バーのチックでマークされています。

3.  クリックして、ワークスペースに検索結果を追加、**強調表示されたノードをワークスペースに追加**概要結果ペインでボタンをクリックします。

     ![XML スキーマ エクスプ ローラー検索結果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     `purchaseOrder`ノードおよび`PurchaseOrderType`ノードがのデザイン サーフェイスに並べて表示されます、[グラフ ビュー](../xml-tools/graph-view.md)です。 2 つのノードは関連があるため (`purchaseOrder` 要素は `PurchaseOrderType` 型)、これらの間に矢印が引かれます。