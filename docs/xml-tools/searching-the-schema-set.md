---
title: "スキーマ セットの検索 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# スキーマ セットの検索
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML スキーマ エクスプローラーでは、次の方法でスキーマ セットを検索できます。  
  
-   キーワード検索  
  
-   スキーマ固有の検索  
  
## キーワード検索  
 キーワード検索を実行するには、XML スキーマ エクスプローラーのツール バーにある **\[スキーマ セットの検索\]** テキスト ボックスに部分文字列を入力します。  
  
 ![XML スキーマ エクスプローラー キーワード検索](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 XML スキーマ エクスプローラーは、次のようにスキーマ セットを検索します。  
  
-   指定したキーワードに一致する `name` 属性または `ref` 属性。これを使用すると、要素、属性、型などを名前で検索することができます。  
  
-   include ステートメントの `schemaLocation` 属性。  
  
-   import ステートメントの `namespace` 属性。  
  
## スキーマ固有の検索  
 XML スキーマ エクスプローラーには、XML スキーマ エクスプローラーのコンテキスト メニューを使用してアクセスできる組み込みの検索機能もあります。使用できるコンテキスト メニューの詳細については、「[コンテキスト メニュー](../xml-tools/context-menus-xml-schema-explorer.md)」を参照してください。スタート ビューからもスキーマ固有の検索を実行できます。詳細については、「[スタート ビュー](../xml-tools/start-view.md)」トピックの「スキーマ セットの詳細」セクションを参照してください。  
  
## 検索結果の表示および移動  
 検索が終了すると、ツール バーに概要結果ペインが追加され、検索結果が表示されます。検索結果は XML スキーマ エクスプローラーでも強調表示され、垂直スクロール バーの目盛りでマークされます。各検索結果を表示するには、XML スキーマ エクスプローラーのツール バーの検索結果ペインにある **\[次の検索結果に移動\]** ボタンおよび **\[前の検索結果に移動\]** ボタンを使用するか、キーボードの F3 キーおよび Shift \+ F3 キーを使用するか、スクロール バーの目盛りをクリックします。  
  
 概要結果ペインの **\[強調表示されたノードをワークスペースに追加\]** ボタンをクリックして、ワークスペースに検索結果を追加できます。  
  
 ![XML スキーマ エクスプローラー検索結果](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## 検索結果のクリア  
 検索結果をクリアするには、XML スキーマ エクスプローラーの検索ツール バーの概要結果ペインにある **\[x\]** ボタンをクリックします。  
  
## 参照  
 [XML スキーマ エクスプローラー](../xml-tools/xml-schema-explorer.md)