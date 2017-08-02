---
title: "方法: スキーマ セットの検索結果のノードをワークスペースに追加する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# 方法: スキーマ セットの検索結果のノードをワークスペースに追加する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このトピックでは、キーワード検索の結果、XML スキーマ エクスプローラーに強調表示されたノードをワークスペースに追加する方法について説明します。  
  
> [!NOTE]
>  [ワークスペース](../xml-tools/xml-schema-designer-workspace.md)に追加できるのは、グローバル ノードだけです。  
  
 この例では、サンプルの[購買発注書のスキーマ](../Topic/Sample%20XSD%20File:%20Purchase%20Order%20Schema.md)を使用します。  
  
### スキーマ セットの検索結果のノードを追加するには  
  
1.  「[方法: XSD スキーマ ファイルを作成して編集する](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)」の手順に従います。  
  
2.  [XML スキーマ エクスプローラー](../xml-tools/xml-schema-explorer.md)のツール バーの検索テキスト ボックスに「purchaseOrder」と入力して検索ボタンをクリックします。  
  
     ![XML スキーマ エクスプローラー キーワード検索](~/xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     検索結果が XML スキーマ エクスプローラーで強調表示され、垂直スクロール バーのチックでマークされます。  
  
3.  概要結果ペインの **\[強調表示されたノードをワークスペースに追加\]** ボタンをクリックして、ワークスペースに検索結果を追加します。  
  
     ![XML スキーマ エクスプローラー検索結果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     `purchaseOrder` ノードおよび `PurchaseOrderType` ノードが[グラフ ビュー](../xml-tools/graph-view.md)のデザイン サーフェイスに並べて表示されます。2 つのノードは関連があるため \(`purchaseOrder` 要素は `PurchaseOrderType` 型\)、これらの間に矢印が引かれます。