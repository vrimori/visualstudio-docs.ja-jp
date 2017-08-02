---
title: "XML エディターとの統合 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# XML エディターとの統合
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML スキーマ デザイナーは、XML エディターと統合されています。XML エディターで XSD ファイルを変更すると、[XML スキーマ エクスプローラー](../xml-tools/xml-schema-explorer.md) にもその変更が反映されます。[グラフ ビュー](../xml-tools/graph-view.md)または[コンテンツ モデル ビュー](../xml-tools/content-model-view.md)が開いている場合には、これらにも変更が反映されます。次の方法を使用して XML スキーマ デザイナーと XML エディターの間を移動できます。  
  
-   XML エディターでノードを右クリックし、**\[XML スキーマ エクスプローラーで表示\]** をクリックします。  
  
-   グラフ ビューと XML スキーマ エクスプローラーでは、ノードをダブルクリックするか、ノードを右クリックして **\[コードの表示\]** をクリックします。コンテンツ モデル ビューでは、ノードを右クリックして **\[コードの表示\]** をクリックします。  
  
 次のスクリーン ショットは、XML スキーマが表示されている XML スキーマ エクスプローラーを示しています。XML スキーマ エクスプローラーでは、スキーマ セットがツリー ビューに表示されます。XML エディターには、XML スキーマ エクスプローラーで現在アクティブになっているノードのテキスト ビューが表示されます。  
  
 ![XSDDesignerWithXMLEditor](~/xml-tools/media/xsddesignerwithxmleditor.gif "XSDDesignerWithXMLEditor")  
  
 場合によっては、XML エディターとグラフィカルなデザイナーのコードを並べて表示すると便利です。2 つのファイルを同時に表示するには、XML エディター内を右クリックし、**\[デザイナーの表示\]** をクリックします。Visual Studio Windows メニューで、**\[水平 \(または垂直\) タブ グループの新規作成\]** を選択します。  
  
 ![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif "XSDDesignerWithXMLEditorAndCMV")  
  
## 参照  
 [XML スキーマ エクスプローラー](../xml-tools/xml-schema-explorer.md)