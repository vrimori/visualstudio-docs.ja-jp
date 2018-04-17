---
title: 拡張オブジェクトを使用して Word を自動化 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d639f1916799341c749164b32559b2ea3ba82428
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="automating-word-by-using-extended-objects"></a>拡張オブジェクトによる Word の自動化
  Visual Studio で Word ソリューションを作成する場合、ソリューションで *ホスト項目* および *ホスト コントロール*を使用できます。 これらのオブジェクトは、Word オブジェクト モデル (つまり Word のプライマリ相互運用機能アセンブリによって公開されるオブジェクト モデル) 内にある、 <xref:Microsoft.Office.Interop.Word.Document> や <xref:Microsoft.Office.Interop.Word.ContentControl> オブジェクトなど、よく使用される特定のオブジェクトを拡張したオブジェクトです。 これらの拡張オブジェクトは、基になる Word オブジェクトと同じように動作しますが、基のオブジェクトにはないイベントとデータ バインディング機能が追加されています。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ホスト項目とホスト コントロールは、VSTO アドインとドキュメント レベルのカスタマイズの両方で使用できます。ただし、使用できるコンテキストはそれおぞれのソリューションの種類で異なります。 詳細については、「 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
## <a name="document-host-item"></a>Document ホスト項目  
 Word プロジェクトでは、 <xref:Microsoft.Office.Tools.Word.Document> ホスト項目にアクセスできます。 <xref:Microsoft.Office.Tools.Word.Document> ホスト項目は、ホスト コントロールや Windows フォーム コントロールなどの他のコントロールを格納するコンテナーの役割も果たし、画面のコントロールに関する情報を保持します。 さらに <xref:Microsoft.Office.Tools.Word.Document> ホスト項目は、 <xref:Microsoft.Office.Interop.Word.Document> クラスとほとんど同じメンバーを提供します。このクラスは、Word のオブジェクト モデル内の対応するクラスです。  
  
 詳細については、「 [Document Host Item](../vsto/document-host-item.md)」を参照してください。  
  
## <a name="word-host-controls"></a>Word ホスト コントロール  
 Word には、ドキュメントの作成、整理、および自動化に役立つホスト コントロールがいくつかあります。 その機能のほとんどには、データのインポート、表示、および保護が含まれます。 これらのホスト コントロールには、Word のネイティブ オブジェクト モデルの対応するコントロールにはないイベントやデータ バインディング機能が用意されています。  
  
 ドキュメントレベルのプロジェクトでは、デザイン時には文書に任意のホスト コントロールを追加でき、実行時にはコンテンツ コントロールおよびブックマーク コントロールを追加できます。 VSTO アドイン プロジェクトでは、実行時に任意の開いているドキュメントにコンテンツ コントロールおよびブックマーク コントロールを追加できます。  
  
 Word プロジェクトで使用できるホスト コントロールの詳細については、次のトピックを参照してください。  
  
-   [コンテンツ コントロール](../vsto/content-controls.md)  
  
-   [Bookmark コントロール](../vsto/bookmark-control.md)  
  
-   [XMLNode コントロール](../vsto/xmlnode-control.md)  
  
-   [XMLNodes コントロール](../vsto/xmlnodes-control.md)  
  
## <a name="see-also"></a>関連項目  
 [方法: Word 文書にコンテンツ コントロールを追加](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [方法 : Word 文書に Bookmark コントロールを追加する](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [方法: Word 文書に XMLNode コントロールを追加します。](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [方法: Word 文書に XMLNodes コントロールを追加します。](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [方法: Bookmark コントロールのサイズを変更します。](../vsto/how-to-resize-bookmark-controls.md)   
 [チュートリアル: コンテンツ コントロールによるテンプレートの作成](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [チュートリアル: カスタム XML 部分へのコンテンツ コントロールのバインド](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [チュートリアル: ブックマークのショートカット メニューを作成します。](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Word ソリューション](../vsto/word-solutions.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  