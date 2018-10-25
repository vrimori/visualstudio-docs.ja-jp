---
title: '方法: スキーマ セットの検索結果のノードをワークスペースに追加します |。Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 75f254a8f64c3750a3c89e10016a0520d3760847
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210367"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>方法: スキーマ セットの検索結果のノードをワークスペースに追加する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
このトピックでは、キーワード検索の結果、XML スキーマ エクスプローラーに強調表示されたノードをワークスペースに追加する方法について説明します。  
  
> [!NOTE]
>  グローバル ノードだけを追加することができます、[ワークスペース](../xml-tools/xml-schema-designer-workspace.md)します。  
  
 この例は、サンプルを使用して[購買発注書スキーマ](../xml-tools/sample-xsd-file-purchase-order-schema.md)します。  
  
### <a name="to-add-schema-set-result-nodes"></a>スキーマ セットの検索結果のノードを追加するには  
  
1.  次の手順では、[方法: を作成し、XSD スキーマ ファイルを編集する](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)します。  
  
2.  検索 テキスト ボックスに「purchaseOrder」を入力、 [XML エクスプ ローラー](../xml-tools/xml-schema-explorer.md)ツールバーおよび検索ボタンをクリックします。  
  
     ![XML スキーマ エクスプ ローラー キーワード検索](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     検索結果が XML スキーマ エクスプローラーで強調表示され、垂直スクロール バーのチックでマークされます。  
  
3.  クリックして、ワークスペースに検索結果を追加、**強調表示されたノードをワークスペースに追加**概要結果ペインでボタンをクリックします。  
  
     ![XML スキーマ エクスプ ローラーの検索結果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     `purchaseOrder`ノードと`PurchaseOrderType`のデザイン画面で、ノードが互いの横に表示、[グラフ ビュー](../xml-tools/graph-view.md)します。 2 つのノードは関連があるため (`purchaseOrder` 要素は `PurchaseOrderType` 型)、これらの間に矢印が引かれます。



