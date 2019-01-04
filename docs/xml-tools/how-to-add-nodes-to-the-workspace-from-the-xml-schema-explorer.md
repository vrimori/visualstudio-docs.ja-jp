---
title: '方法: XML スキーマ エクスプローラーからワークスペースにノードを追加する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a65decc0ba965f27579c746dc5763c2e9aa8d3be
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960512"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>方法: XML スキーマ エクスプ ローラーからワークスペースにノードを追加します。

このトピックでは、ノードを追加する方法を説明します、 [XML スキーマ デザイナーのワークスペース](../xml-tools/xml-schema-designer-workspace.md)から、 **XML スキーマ エクスプ ローラー**します。 これは、ドラッグ アンド ドロップのノードで実現できます、 **XML スキーマ エクスプ ローラー** XSD デザイナーのビュー、またはを使用して、 **XML スキーマ エクスプ ローラーの**コンテキスト メニュー。 実行された検索の結果として強調表示されているノードを追加することも、 **XML スキーマ エクスプ ローラー**します。 詳細については、「[方法 :スキーマ セットの検索結果のノードをワークスペースに追加](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md)します。

> [!NOTE]
> グローバル ノードだけを追加することができます、 [XML スキーマ デザイナーのワークスペース](../xml-tools/xml-schema-designer-workspace.md)します。

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>XML のエクスプ ローラーのコンテキスト メニューからノードを追加するには

1.  次の手順では、[方法。作成し、XSD スキーマ ファイルを編集する](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)します。

2.  右クリックして、 `PurchaseOrderType` XSD エクスプ ローラーでノード。 選択**グラフ ビューで表示**します。

     `purchaseOrderType` ノードがグラフ ビューのデザイン サーフェイスに表示されます。

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>ビューにノードをドラッグ アンド ドロップするには

1.  右クリックし、`PurchaseOrderType`グラフ ビュー内のノード。 選択**XML スキーマ エクスプ ローラーで表示する**します。

     ノードが強調表示、 **XML スキーマ エクスプ ローラー**します。

2.  右クリックして、`PurchaseOrderType`内のノード、 **XML スキーマ エクスプ ローラー**選択**すべての参照**します。

     `purchaseOrder` ノードが強調表示されます。

3.  `purchaseOrder` ノードをグラフ ビューにドラッグします。

     `purchaseOrder` ノードおよび `PurchaseOrderType` ノードがグラフ ビューのデザイン サーフェイスに並べて表示されます。 2 つのノードは関連があるため (`purchaseOrder` 要素は `PurchaseOrderType` 型)、これらの間に矢印が引かれます。

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>スキーマ エクスプローラーの検索機能を使用してノードを追加するには

1.  検索 テキスト ボックスに「purchaseOrder」を入力、 [XML エクスプ ローラー](../xml-tools/xml-schema-explorer.md)ツールバーおよび検索ボタンをクリックします。

     ![XML スキーマ エクスプローラー キーワード検索](../xml-tools/media/schemaexplorersearch.gif)

     検索結果が強調表示、 **XML スキーマ エクスプ ローラー**垂直スクロール バーのチックでマークされているとします。

2.  クリックして、ワークスペースに検索結果を追加、**強調表示されたノードをワークスペースに追加**概要結果ペインでボタンをクリックします。

     ![XML スキーマ エクスプローラー検索結果](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder`ノードと`PurchaseOrderType`のデザイン画面で、ノードが互いの横に表示、[グラフ ビュー](../xml-tools/graph-view.md)します。 2 つのノードは関連があるため (`purchaseOrder` 要素は `PurchaseOrderType` 型)、これらの間に矢印が引かれます。

## <a name="see-also"></a>関連項目

- [XML スキーマ エクスプローラー](../xml-tools/xml-schema-explorer.md)