---
title: '方法: XML スキーマ エクスプ ローラーからワークスペースにノードを追加 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 58bad7de0b907881b4fe6f21fd5c7957e692d33a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534752"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>方法: XML スキーマ エクスプローラーからワークスペースにノードを追加する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: XML スキーマ エクスプ ローラーからワークスペースにノードの追加](https://docs.microsoft.com/visualstudio/xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer)します。  
  
  
このトピックでは、ノードを追加する方法を説明します、 [XML スキーマ デザイナーのワークスペース](../xml-tools/xml-schema-designer-workspace.md)XML スキーマ エクスプ ローラーから。 これは、XML スキーマ エクスプローラーから XSD デザイナーのビューにノードをドラッグ アンド ドロップするか、XML スキーマ エクスプローラーのコンテキスト メニューを使用することによって行うことができます。 さらに、XML スキーマ エクスプローラーの検索結果で強調表示されたノードを追加することができます。 詳細については、次を参照してください。[方法: スキーマ セット検索結果ノードを追加するワークスペース](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md)します。  
  
> [!NOTE]
>  グローバル ノードだけを追加することができます、 [XML スキーマ デザイナーのワークスペース](../xml-tools/xml-schema-designer-workspace.md)します。  
  
### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>XML スキーマ エクスプローラーのコンテキスト メニューからノードを追加するには  
  
1.  次の手順では、[方法: を作成し、XSD スキーマ ファイルを編集する](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)します。  
  
2.  XSD エクスプローラーで `PurchaseOrderType` ノードを右クリックします。 選択**グラフ ビューで表示**します。  
  
     `purchaseOrderType` ノードがグラフ ビューのデザイン サーフェイスに表示されます。  
  
### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>ビューにノードをドラッグ アンド ドロップするには  
  
1.  グラフ ビューで `PurchaseOrderType` ノードを右クリックします。 選択**XML スキーマ エクスプ ローラーで表示する**します。  
  
     XML スキーマ エクスプローラーにノードが強調表示されます。  
  
2.  右クリックして、`PurchaseOrderType`クリックし、XML スキーマ エクスプ ローラーでノード**すべての参照**します。  
  
     `purchaseOrder` ノードが強調表示されます。  
  
3.  `purchaseOrder` ノードをグラフ ビューにドラッグします。  
  
     `purchaseOrder` ノードおよび `PurchaseOrderType` ノードがグラフ ビューのデザイン サーフェイスに並べて表示されます。 2 つのノードは関連があるため (`purchaseOrder` 要素は `PurchaseOrderType` 型)、これらの間に矢印が引かれます。  
  
### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>スキーマ エクスプローラーの検索機能を使用してノードを追加するには  
  
1.  検索 テキスト ボックスに「purchaseOrder」を入力、 [XML エクスプ ローラー](../xml-tools/xml-schema-explorer.md)ツールバーおよび検索ボタンをクリックします。  
  
     ![XML スキーマ エクスプ ローラー キーワード検索](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     検索結果が XML スキーマ エクスプローラーで強調表示され、垂直スクロール バーのチックでマークされます。  
  
2.  クリックして、ワークスペースに検索結果を追加、**強調表示されたノードをワークスペースに追加**概要結果ペインでボタンをクリックします。  
  
     ![XML スキーマ エクスプ ローラーの検索結果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     `purchaseOrder`ノードと`PurchaseOrderType`のデザイン画面で、ノードが互いの横に表示、[グラフ ビュー](../xml-tools/graph-view.md)します。 2 つのノードは関連があるため (`purchaseOrder` 要素は `PurchaseOrderType` 型)、これらの間に矢印が引かれます。  
  
## <a name="see-also"></a>関連項目  
 [XML スキーマ エクスプローラー](../xml-tools/xml-schema-explorer.md)



