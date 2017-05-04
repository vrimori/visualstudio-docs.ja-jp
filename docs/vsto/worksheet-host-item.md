---
title: "Worksheet ホスト項目 | Microsoft Docs"
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
  - "ホスト項目 [Visual Studio での Office 開発]、ワークシート"
  - "Excel [Visual Studio での Office 開発]、ワークシート"
  - "ワークシート ホスト項目"
  - "ワークシート、イベント"
  - "ワークシート ホスト項目、イベント"
  - "Excel ワークシート"
  - "ワークシート、Excel"
  - "ワークシート"
  - "イベント [Visual Studio での Office 開発]"
ms.assetid: b4f7c501-81f5-409e-aa1b-748f010798b9
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Worksheet ホスト項目
  <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目は、Excel のプライマリ相互運用機能アセンブリの <xref:Microsoft.Office.Interop.Excel.Worksheet> 型を拡張する型です。<xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目は <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトと同一のプロパティ、メソッド、イベントをすべて提供します。また、追加のイベントも公開し、ホスト コントロールおよび Windows フォーム コントロールのコンテナーとしても機能します。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ドキュメント レベルのプロジェクトでは、デザイン時に <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目をプロジェクトに追加できます。 VSTO アドイン プロジェクトでは、実行時に <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目を生成できます。  
  
## ドキュメント レベルのプロジェクトでのワークシートのホスト項目について  
 Excel のドキュメント レベルのプロジェクトを作成すると、Visual Studio によって 3 つの <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目がプロジェクト内に自動的に作成されます。 これらのワークシートの既定の名前は、`Sheet1`、`Sheet2`、`Sheet3` です。 既存のブックに基づいてプロジェクトを作成する場合は、そのブック内のワークシートの数に応じてホスト項目の数が決まります。  
  
 これらのワークシート クラスによって、<xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目のメンバーにアクセスし、ワークシートのコンテンツを変更するなど、カスタマイズの基本的なタスクを実行できます。 また、ワークシートにコントロールを追加するには、これらのクラスを使用できます。 さまざまな種類のコントロールを組み合わせ、コードを記述すると、コントロールをデータにバインドしたり、ユーザーから情報を収集したり、ユーザーの操作に応答したりできます。 詳細については、「[ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)」を参照してください。  
  
 ワークシート クラスには、プロジェクトでコードの記述を開始できる場所が用意されています。 このクラスには、Excel のプライマリ相互運用機能アセンブリの <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトと同じプロパティ、メソッド、イベントがすべて用意されているため、これらのクラスを使用して Excel のオブジェクト モデルにアクセスすることもできます。 詳細については、「[Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)」を参照してください。  
  
 ドキュメント レベルのプロジェクトの場合は、デザイナーで新しいワークシートをブックに追加すると、デザイン時に追加の <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目をプロジェクトに追加できます。  
  
### ワークシートの名前変更  
 ドキュメント レベルのプロジェクトでは、Visual Studio デザイナーでワークシートの名前を変更できますが、この場合はワークシートの表示名だけが変わります。 ワークシートのプログラム上の名前は既定の名前のままです。**\[プロパティ\]** ウィンドウでワークシートの名前を変更すると、プログラム上の名前だけが変更されます。  
  
### ドキュメント レベルのプロジェクトでのワークシートのホスト項目の制限  
 ドキュメント レベルのプロジェクトでは、実行時に新しい <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目を作成することはできません。 実行時に新しい Excel ワークシートを作成すると、そのワークシートは <xref:Microsoft.Office.Interop.Excel.Worksheet> 型になります。 これはホスト項目ではないため、ホスト コントロールや Windows フォーム コントロールを含めることはできません。 実行時に文書を作成する方法について詳しくは、「[方法: プログラムを使用して新しいワークシートをブックに追加する](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)」をご覧ください。  
  
## VSTO アドイン プロジェクトでのワークシートのホスト項目について  
 アプリケーション レベルのプロジェクトでは、Excel で開いている任意のワークシートの <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目を実行時に生成できます。<xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目を使用して、関連付けられたワークシートにコントロールを追加したり、<xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトで使用できないイベントを処理したりできます。  
  
 <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目を生成するには、GetVstoObject メソッドを使用します。 詳細については、「[VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
## 参照  
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Workbook ホスト項目](../vsto/workbook-host-item.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  