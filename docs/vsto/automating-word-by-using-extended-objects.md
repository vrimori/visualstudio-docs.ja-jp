---
title: "拡張オブジェクトによる Word の自動化"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Word [Visual Studio での Office 開発]、自動化"
  - "拡張オブジェクト [Visual Studio での Office 開発]、Word"
  - "オートメーション [Visual Studio での Office 開発]、Word"
  - "ホスト項目 [Visual Studio での Office 開発]、Word"
  - "自動化 (Word を)"
  - "コントロール [Visual Studio での Office 開発]、Word ホスト コントロール"
  - "ホスト コントロール、Word"
  - "ホスト コントロール [Visual Studio での Office 開発]、Word"
  - "Word [Visual Studio での Office 開発]、ホスト コントロール"
ms.assetid: 3911c7cd-7092-468d-bd82-2fdec53a2d9b
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 拡張オブジェクトによる Word の自動化
  Visual Studio で Word ソリューションを作成する場合、ソリューションで*ホスト項目*および*ホスト コントロール*を使用できます。 これらのオブジェクトは、Word オブジェクト モデル \(つまり Word のプライマリ相互運用機能アセンブリによって公開されるオブジェクト モデル\) 内にある、<xref:Microsoft.Office.Interop.Word.Document> や <xref:Microsoft.Office.Interop.Word.ContentControl> オブジェクトなど、よく使用される特定のオブジェクトを拡張したオブジェクトです。 これらの拡張オブジェクトは、基になる Word オブジェクトと同じように動作しますが、基のオブジェクトにはないイベントとデータ バインディング機能が追加されています。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ホスト項目とホスト コントロールは、VSTO アドインとドキュメント レベルのカスタマイズの両方で使用できます。ただし、使用できるコンテキストはそれおぞれのソリューションの種類で異なります。 詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
## Document ホスト項目  
 Word プロジェクトでは、<xref:Microsoft.Office.Tools.Word.Document> ホスト項目にアクセスできます。<xref:Microsoft.Office.Tools.Word.Document> ホスト項目は、ホスト コントロールや Windows フォーム コントロールなどの他のコントロールを格納するコンテナーの役割も果たし、画面のコントロールに関する情報を保持します。 さらに <xref:Microsoft.Office.Tools.Word.Document> ホスト項目は、<xref:Microsoft.Office.Interop.Word.Document> クラスとほとんど同じメンバーを提供します。このクラスは、Word のオブジェクト モデル内の対応するクラスです。  
  
 詳細については、「[Document ホスト項目](../vsto/document-host-item.md)」を参照してください。  
  
## Word ホスト コントロール  
 Word には、ドキュメントの作成、整理、および自動化に役立つホスト コントロールがいくつかあります。 その機能のほとんどには、データのインポート、表示、および保護が含まれます。 これらのホスト コントロールには、Word のネイティブ オブジェクト モデルの対応するコントロールにはないイベントやデータ バインディング機能が用意されています。  
  
 ドキュメントレベルのプロジェクトでは、デザイン時には文書に任意のホスト コントロールを追加でき、実行時にはコンテンツ コントロールおよびブックマーク コントロールを追加できます。 VSTO アドイン プロジェクトでは、実行時に任意の開いているドキュメントにコンテンツ コントロールおよびブックマーク コントロールを追加できます。  
  
 Word プロジェクトで使用できるホスト コントロールの詳細については、次のトピックを参照してください。  
  
-   [コンテンツ コントロール](../vsto/content-controls.md)  
  
-   [Bookmark コントロール](../vsto/bookmark-control.md)  
  
-   [XMLNode コントロール](../vsto/xmlnode-control.md)  
  
-   [XMLNodes コントロール](../vsto/xmlnodes-control.md)  
  
## 参照  
 [方法 : Word 文書にコンテンツ コントロールを追加する](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [方法 : Word 文書に Bookmark コントロールを追加する](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [方法 : Word 文書に XMLNode コントロールを追加する](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [方法 : Word 文書に XMLNodes コントロールを追加する](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [方法 : Bookmark コントロールのサイズを変更する](../vsto/how-to-resize-bookmark-controls.md)   
 [チュートリアル : コンテンツ コントロールによるテンプレートの作成](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [チュートリアル : カスタム XML 部分へのコンテンツ コントロールのバインド](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [チュートリアル : ブックマークのショートカット メニューの作成](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Word ソリューション](../vsto/word-solutions.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  