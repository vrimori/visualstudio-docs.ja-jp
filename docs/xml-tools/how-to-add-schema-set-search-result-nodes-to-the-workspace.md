---
title: XML スキーマ セットの検索結果ノードをワークスペースに追加します。
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e9f004943474f9b1c0fb449c1aec23f70034c3a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875035"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>方法: スキーマ セットの検索結果のノードをワークスペースに追加します。

このトピックで強調表示されているノードを追加する方法について説明、 **XML スキーマ エクスプ ローラー**ワークスペース内のキーワード検索の結果として。

> [!NOTE]
> グローバル ノードだけを追加することができます、[ワークスペース](../xml-tools/xml-schema-designer-workspace.md)します。


 この例は、サンプルを使用して[購買発注書のスキーマ](../xml-tools/sample-xsd-file-purchase-order-schema.md)します。

## <a name="to-add-schema-set-result-nodes"></a>スキーマ セットの検索結果のノードを追加するには

1.  次の手順では、[方法。作成し、XSD スキーマ ファイルを編集する](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)します。

2.  検索 テキスト ボックスに「purchaseOrder」を入力、 [XML エクスプ ローラー](../xml-tools/xml-schema-explorer.md)ツールバーおよび検索ボタンをクリックします。

     ![XML スキーマ エクスプローラー キーワード検索](../xml-tools/media/schemaexplorersearch.gif)

     検索結果が強調表示、 **XML スキーマ エクスプ ローラー**垂直スクロール バーのチックでマークされているとします。

3.  クリックして、ワークスペースに検索結果を追加、**強調表示されたノードをワークスペースに追加**概要結果ペインでボタンをクリックします。

     ![XML スキーマ エクスプローラー検索結果](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder`ノードと`PurchaseOrderType`のデザイン画面で、ノードが互いの横に表示、[グラフ ビュー](../xml-tools/graph-view.md)します。 2 つのノードは関連があるため (`purchaseOrder` 要素は `PurchaseOrderType` 型)、これらの間に矢印が引かれます。