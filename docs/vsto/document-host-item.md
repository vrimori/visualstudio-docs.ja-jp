---
title: Document ホスト項目
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 10dabdf0cf2db043a5df1b21f5f780645864ae8c
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2018
---
# <a name="document-host-item"></a>Document ホスト項目
  <xref:Microsoft.Office.Tools.Word.Document> ホスト項目は、Word のプライマリ相互運用機能アセンブリの <xref:Microsoft.Office.Interop.Word.Document> 型を拡張する型です。 <xref:Microsoft.Office.Tools.Word.Document> ホスト項目には、 <xref:Microsoft.Office.Interop.Word.Document> オブジェクトと同じプロパティ、メソッド、イベントがすべて用意されています。また、追加のイベントも公開し、ホスト コントロールおよび Windows フォーム コントロールのコンテナーとしても機能します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ドキュメント レベルのプロジェクトには、プロジェクト内のドキュメントを表す既定の <xref:Microsoft.Office.Tools.Word.Document> ホスト項目があります。 VSTO アドイン プロジェクトでは、実行時に <xref:Microsoft.Office.Tools.Word.Document> ホスト項目を生成できます。  
  
## <a name="understand-the-document-host-item-in-document-level-projects"></a>ドキュメント レベルのプロジェクトの document ホスト項目を理解します。  
 プロジェクトのドキュメントにアクセスするには、 `ThisDocument` クラスを使用します。 ドキュメント レベルのプロジェクトを作成すると、Visual Studio が、Word とカスタマイズ コード間の通信リンクとして機能する `ThisDocument` クラスを生成します。 `ThisDocument` クラスによって、 <xref:Microsoft.Office.Tools.Word.Document> ホスト項目のメンバーにアクセスし、ドキュメントが開かれたり閉じられたりしたときにコードを実行するなど、カスタマイズの基本的なタスクを実行できます。 また、このクラスを使用して、ドキュメントにコントロールを追加することもできます。 さまざまな種類のコントロールを組み合わせ、コードを記述することによって、コントロールのデータへのバインド、ユーザー情報の収集、およびユーザーの操作への応答を実行できます。 詳細については、次を参照してください。[ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)です。  
  
 `ThisDocument` クラスには、プロジェクトでコードの記述を開始できる場所が用意されています。 このクラスには、Word のプライマリ相互運用機能アセンブリの <xref:Microsoft.Office.Interop.Word.Document> オブジェクトと同じプロパティ、メソッド、イベントがすべて用意されているため、 `ThisDocument` を使用して Word のオブジェクト モデルにアクセスすることもできます。 詳細については、次を参照してください。 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)です。  
  
### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>ドキュメント レベルのプロジェクトの document ホスト項目の制限事項  
 ドキュメント レベルのプロジェクトには、1 つの <xref:Microsoft.Office.Tools.Word.Document> ホスト項目のみ (つまり `ThisDocument` クラス) を含めることができます。 新規に追加することはできません<xref:Microsoft.Office.Tools.Word.Document>、デザイン時に項目をプロジェクトにホストし、新規に作成することはできません<xref:Microsoft.Office.Tools.Word.Document>実行時にドキュメント レベルのカスタマイズから項目をホストします。  
  
 実行時に新しい Word 文書を作成する場合、型のことが<xref:Microsoft.Office.Interop.Word.Document>です。 これはホスト項目ではないため、ホスト コントロールや Windows フォーム コントロールを含めることはできません。 実行時にドキュメントの作成の詳細については、次を参照してください。[する方法: プログラムによって新しいドキュメントを作成する](../vsto/how-to-programmatically-create-new-documents.md)です。  
  
## <a name="understand-document-host-items-in-application-level-projects"></a>アプリケーション レベルのプロジェクトのドキュメント ホスト項目を理解します。  
 VSTO アドイン プロジェクトでは、Word で開いている任意のドキュメントで <xref:Microsoft.Office.Tools.Word.Document> ホスト項目を実行時に生成できます。 <xref:Microsoft.Office.Tools.Word.Document> ホスト項目を使用して、関連付けられたドキュメントにコントロールを追加したり、 <xref:Microsoft.Office.Interop.Word.Document> オブジェクトで使用できないイベントを処理したりできます。  
  
 生成する、<xref:Microsoft.Office.Tools.Word.Document>ホスト項目を使用して、`GetVstoObject`メソッドです。 詳細については、次を参照してください。[拡張 Word 文書と実行時に VSTO アドイン内の Excel ブック](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Word 文書と実行時に VSTO アドイン内の Excel ブックを拡張します。](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  