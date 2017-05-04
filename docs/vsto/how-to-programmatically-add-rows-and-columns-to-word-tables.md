---
title: "方法: プログラムによって Word の表に行と列を追加する | Microsoft Docs"
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
  - "列 [Visual Studio での Office 開発], 追加 (Word テーブルに)"
  - "行 [Visual Studio での Office 開発], 追加 (Word テーブルに)"
  - "テーブル [Visual Studio での Office 開発], 追加 (行と列を)"
ms.assetid: 01a9b6ca-1373-4a6e-b9e6-2225a1321daf
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# 方法: プログラムによって Word の表に行と列を追加する
  Microsoft Office Word の表では、セルが行と列に編成されます。  表に行を追加するには、<xref:Microsoft.Office.Interop.Word.Rows> オブジェクトの <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> メソッドを使用し、列を追加するには <xref:Microsoft.Office.Interop.Word.Columns> オブジェクトの <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> メソッドを使用します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## ドキュメント レベルのカスタマイズの例  
 次のコード例はドキュメント レベルのカスタマイズで使用できます。  これらの例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。  これらの例は、カスタマイズに関連するドキュメントに、少なくとも 1 つの表が既にあることを前提としています。  
  
> [!IMPORTANT]  
>  このコードは、次のいずれかのプロジェクト テンプレートを使用して作成したプロジェクトでのみ実行されます。  
>   
>  -   Word 2013 ドキュメント  
> -   Word 2013 テンプレート  
> -   Word 2010 ドキュメント  
> -   Word 2010 テンプレート  
>   
>  他の種類のプロジェクトでこのタスクを実行する場合は、**Microsoft.Office.Interop.Word** アセンブリへの参照を追加しなければならず、そのアセンブリのクラスを使用して表に行と列を追加する必要があります。  詳細については、「[方法 : プライマリ相互運用機能アセンブリを利用して Office アプリケーションを使用する](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)」および「[Word 2010 プライマリ相互運用機能アセンブリのリファレンス](http://go.microsoft.com/fwlink/?LinkId=189588)」を参照してください。  
  
#### 表に行を追加するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> メソッドを使用して表に行を追加します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomation#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#95)]  
  
#### 表に列を追加するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> メソッドを使用し、次に <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> メソッドを使用してすべての列を同じ幅にします。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomation#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#96)]  
  
## VSTO アドインの例  
 次のコード例は VSTO アドインで使用できます。  これらの例を使用するには、プロジェクトの `ThisAddIn` クラスからコードを実行します。  これらの例は、作業中のドキュメントに少なくとも 1 つの表が既にあることを想定しています。  
  
> [!IMPORTANT]  
>  このコードは、Word VSTO アドイン テンプレートを使用して作成したプロジェクトでのみ実行されます。  
>   
>  他の種類のプロジェクトでこのタスクを実行する場合は、**Microsoft.Office.Interop.Word** アセンブリへの参照を追加しなければならず、そのアセンブリのクラスを使用して表に行と列を追加する必要があります。  詳細については、「[方法 : プライマリ相互運用機能アセンブリを利用して Office アプリケーションを使用する](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)」および「[Word 2010 プライマリ相互運用機能アセンブリのリファレンス](http://go.microsoft.com/fwlink/?LinkId=189588)」を参照してください。  
  
#### 表に行を追加するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> メソッドを使用して表に行を追加します。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#95)]  
  
#### 表に列を追加するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> メソッドを使用し、次に <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> メソッドを使用してすべての列を同じ幅にします。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#96)]  
  
## 参照  
 [方法: プログラムによって Word の表を作成する](../vsto/how-to-programmatically-create-word-tables.md)   
 [方法: プログラムによって Word の表のセルにテキストと書式設定を追加する](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [方法: プログラムによって Document プロパティを Word の表に読み込む](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  