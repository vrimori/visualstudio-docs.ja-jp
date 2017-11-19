---
title: "ホスト項目を文書化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
ms.assetid: 4c1963f2-e88e-4c68-9f3d-13dedebddde4
caps.latest.revision: "47"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de243ee4b36d180b93e1b64f2a08c013a05d5360
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="document-host-item"></a>Document ホスト項目
  <xref:Microsoft.Office.Tools.Word.Document> ホスト項目は、Word のプライマリ相互運用機能アセンブリの <xref:Microsoft.Office.Interop.Word.Document> 型を拡張する型です。 <xref:Microsoft.Office.Tools.Word.Document> ホスト項目には、 <xref:Microsoft.Office.Interop.Word.Document> オブジェクトと同じプロパティ、メソッド、イベントがすべて用意されています。また、追加のイベントも公開し、ホスト コントロールおよび Windows フォーム コントロールのコンテナーとしても機能します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ドキュメント レベルのプロジェクトには、プロジェクト内のドキュメントを表す既定の <xref:Microsoft.Office.Tools.Word.Document> ホスト項目があります。 VSTO アドイン プロジェクトでは、実行時に <xref:Microsoft.Office.Tools.Word.Document> ホスト項目を生成できます。  
  
## <a name="understanding-the-document-host-item-in-document-level-projects"></a>ドキュメント レベルのプロジェクトの Document ホスト項目について  
 プロジェクトのドキュメントにアクセスするには、 `ThisDocument` クラスを使用します。 ドキュメント レベルのプロジェクトを作成すると、Visual Studio が、Word とカスタマイズ コード間の通信リンクとして機能する `ThisDocument` クラスを生成します。 `ThisDocument` クラスによって、 <xref:Microsoft.Office.Tools.Word.Document> ホスト項目のメンバーにアクセスし、ドキュメントが開かれたり閉じられたりしたときにコードを実行するなど、カスタマイズの基本的なタスクを実行できます。 また、このクラスを使用して、ドキュメントにコントロールを追加することもできます。 さまざまな種類のコントロールを組み合わせ、コードを記述することによって、コントロールのデータへのバインド、ユーザー情報の収集、およびユーザーの操作への応答を実行できます。 詳細については、「 [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)」を参照してください。  
  
 `ThisDocument` クラスには、プロジェクトでコードの記述を開始できる場所が用意されています。 このクラスには、Word のプライマリ相互運用機能アセンブリの <xref:Microsoft.Office.Interop.Word.Document> オブジェクトと同じプロパティ、メソッド、イベントがすべて用意されているため、 `ThisDocument` を使用して Word のオブジェクト モデルにアクセスすることもできます。 詳細については、「 [Word Object Model Overview](../vsto/word-object-model-overview.md)」を参照してください。  
  
### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>ドキュメント レベルのプロジェクトの Document ホスト項目に関する制限  
 ドキュメント レベルのプロジェクトには、1 つの <xref:Microsoft.Office.Tools.Word.Document> ホスト項目のみ (つまり `ThisDocument` クラス) を含めることができます。 デザイン時に新しい <xref:Microsoft.Office.Tools.Word.Document> ホスト項目をプロジェクトに追加することはできません。また、実行時にドキュメント レベルのカスタマイズから新しい <xref:Microsoft.Office.Tools.Word.Document> ホスト項目を作成することもできません。  
  
 実行時に新しい Word ドキュメントを作成すると、そのワークシートは <xref:Microsoft.Office.Interop.Word.Document>型になります。 これはホスト項目ではないため、ホスト コントロールや Windows フォーム コントロールを含めることはできません。 実行時にドキュメントの作成の詳細については、次を参照してください。[する方法: プログラムによって新しいのドキュメントを作成](../vsto/how-to-programmatically-create-new-documents.md)です。  
  
## <a name="understanding-document-host-items-in-application-level-projects"></a>アプリケーション レベルのプロジェクトの Document ホスト項目について  
 VSTO アドイン プロジェクトでは、Word で開いている任意のドキュメントで <xref:Microsoft.Office.Tools.Word.Document> ホスト項目を実行時に生成できます。 <xref:Microsoft.Office.Tools.Word.Document> ホスト項目を使用して、関連付けられたドキュメントにコントロールを追加したり、 <xref:Microsoft.Office.Interop.Word.Document> オブジェクトで使用できないイベントを処理したりできます。  
  
 生成する、<xref:Microsoft.Office.Tools.Word.Document>ホスト項目、GetVstoObject メソッドを使用します。 詳細については、「 [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  