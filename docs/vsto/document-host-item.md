---
title: "Document ホスト項目"
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
  - "ドキュメント [Visual Studio での Office 開発]"
  - "ドキュメント [Visual Studio での Office 開発]、ドキュメント ホスト項目"
  - "ドキュメント ホスト項目"
  - "Word [Visual Studio での Office 開発]、Word ドキュメント"
  - "Word [Visual Studio での Office 開発]"
  - "Word ドキュメント"
  - "ホスト項目 [Visual Studio での Office 開発]、ドキュメント"
ms.assetid: 4c1963f2-e88e-4c68-9f3d-13dedebddde4
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Document ホスト項目
  <xref:Microsoft.Office.Tools.Word.Document> ホスト項目は、Word のプライマリ相互運用機能アセンブリの <xref:Microsoft.Office.Interop.Word.Document> 型を拡張する型です。<xref:Microsoft.Office.Tools.Word.Document> ホスト項目には、<xref:Microsoft.Office.Interop.Word.Document> オブジェクトと同じプロパティ、メソッド、イベントがすべて用意されています。また、追加のイベントも公開し、ホスト コントロールおよび Windows フォーム コントロールのコンテナーとしても機能します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ドキュメント レベルのプロジェクトには、プロジェクト内のドキュメントを表す既定の <xref:Microsoft.Office.Tools.Word.Document> ホスト項目があります。 VSTO アドイン プロジェクトでは、実行時に <xref:Microsoft.Office.Tools.Word.Document> ホスト項目を生成できます。  
  
## ドキュメント レベルのプロジェクトの Document ホスト項目について  
 プロジェクトのドキュメントにアクセスするには、`ThisDocument` クラスを使用します。 ドキュメント レベルのプロジェクトを作成すると、Visual Studio が、Word とカスタマイズ コード間の通信リンクとして機能する `ThisDocument` クラスを生成します。`ThisDocument` クラスによって、<xref:Microsoft.Office.Tools.Word.Document> ホスト項目のメンバーにアクセスし、ドキュメントが開かれたり閉じられたりしたときにコードを実行するなど、カスタマイズの基本的なタスクを実行できます。 また、このクラスを使用して、ドキュメントにコントロールを追加することもできます。 さまざまな種類のコントロールを組み合わせ、コードを記述することによって、コントロールのデータへのバインド、ユーザー情報の収集、およびユーザーの操作への応答を実行できます。 詳細については、「[ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)」を参照してください。  
  
 `ThisDocument` クラスには、プロジェクトでコードの記述を開始できる場所が用意されています。 このクラスには、Word のプライマリ相互運用機能アセンブリの <xref:Microsoft.Office.Interop.Word.Document> オブジェクトと同じプロパティ、メソッド、イベントがすべて用意されているため、`ThisDocument` を使用して Word のオブジェクト モデルにアクセスすることもできます。 詳細については、「[Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)」を参照してください。  
  
### ドキュメント レベルのプロジェクトの Document ホスト項目に関する制限  
 ドキュメント レベルのプロジェクトには、1 つの <xref:Microsoft.Office.Tools.Word.Document> ホスト項目のみ \(つまり `ThisDocument` クラス\) を含めることができます。 デザイン時に新しい <xref:Microsoft.Office.Tools.Word.Document> ホスト項目をプロジェクトに追加することはできません。また、実行時にドキュメント レベルのカスタマイズから新しい <xref:Microsoft.Office.Tools.Word.Document> ホスト項目を作成することもできません。  
  
 実行時に新しい Word ドキュメントを作成すると、そのワークシートは <xref:Microsoft.Office.Interop.Word.Document> 型になります。 これはホスト項目ではないため、ホスト コントロールや Windows フォーム コントロールを含めることはできません。 実行時に文書を作成する方法について詳しくは、「[方法: プログラムによって新しい文書を作成する](../vsto/how-to-programmatically-create-new-documents.md)」を参照してください。  
  
## アプリケーション レベルのプロジェクトの Document ホスト項目について  
 VSTO アドイン プロジェクトでは、Word で開いている任意のドキュメントで <xref:Microsoft.Office.Tools.Word.Document> ホスト項目を実行時に生成できます。<xref:Microsoft.Office.Tools.Word.Document> ホスト項目を使用して、関連付けられたドキュメントにコントロールを追加したり、<xref:Microsoft.Office.Interop.Word.Document> オブジェクトで使用できないイベントを処理したりできます。  
  
 <xref:Microsoft.Office.Tools.Word.Document> ホスト項目を生成するには、GetVstoObject メソッドを使用します。 詳細については、「[VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
## 参照  
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  