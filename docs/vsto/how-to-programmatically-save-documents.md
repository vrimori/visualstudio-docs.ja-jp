---
title: "方法: プログラムによって文書を保存する"
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
  - "ドキュメント [Visual Studio での Office 開発], 保存"
  - "Word [Visual Studio での Office 開発], 保存 (ドキュメントを)"
ms.assetid: a6225ae9-94f5-421a-9860-5299002d543d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 方法: プログラムによって文書を保存する
  Microsoft Office Word 文書を保存するには、いくつかの方法があります。  名前を変更せずに文書を保存することもできますし、新しい名前を指定して文書を保存することもできます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## 名前を変更せずに文書を保存する  
  
#### ドキュメント レベルのカスタマイズに関連付けられた文書を保存するには  
  
1.  <xref:Microsoft.Office.Tools.Word.Document> クラスの <xref:Microsoft.Office.Tools.Word.Document.Save%2A> メソッドを呼び出します。  このコード例を使用するには、プロジェクトの `ThisDocument` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreWordAutomation#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#7)]  
  
#### アクティブ文書を保存するには  
  
1.  アクティブ文書の <xref:Microsoft.Office.Interop.Word._Document.Save%2A> メソッドを呼び出します。  このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#8)]
     [!code-vb[Trin_VstcoreWordAutomation#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#8)]  
  
 保存しようとしている文書がアクティブ文書かどうか不明な場合は、文書を名前で指定できます。  
  
#### 名前で指定した文書を保存するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Documents> コレクションの引数に文書名を使用します。  このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスから実行します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#9)]
     [!code-vb[Trin_VstcoreWordAutomation#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#9)]  
  
## 新しい名前を指定して文書を保存する  
 新しい名前を指定して文書を保存するには、SaveAs メソッドを使用します。  ドキュメント レベルの Word プロジェクトにある <xref:Microsoft.Office.Tools.Word.Document> ホスト項目のメソッド、または Word プロジェクトにあるネイティブな <xref:Microsoft.Office.Interop.Word.Document> オブジェクトのメソッドを使用できます。  このメソッドでは、新しいファイル名を指定する必要がありますが、他の引数は省略できます。  
  
> [!NOTE]  
>  `ThisDocument` の <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> イベント ハンドラー内で **SaveAs** ダイアログ ボックスを表示し、*Cancel* パラメーターを **false** に設定すると、アプリケーションの予期しない終了が発生することがあります。  *Cancel* パラメーターを **true** に設定すると、自動保存が無効になっているというエラー メッセージが表示されます。  
  
#### 新しい名前を指定して、ドキュメント レベルのカスタマイズに関連付けられた文書を保存するには  
  
1.  絶対パスとファイル名を使用して、プロジェクトの `ThisDocument` クラスの <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> メソッドを呼び出します。  指定された名前のファイルが既にフォルダーに存在する場合は、自動的に上書きされます。  このコード例を使用するには、`ThisDocument` クラスから実行します。  
  
    > [!NOTE]  
    >  ターゲット ディレクトリが存在しない場合や、ファイルを保存するうえで他の問題がある場合は、<xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> メソッドは例外をスローします。  <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> メソッドの周囲または呼び出しメソッドの内部に **try…catch** ブロックを使用することをお勧めします。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#10)]  
  
#### 新しい名前を指定してネイティブな文書を保存するには  
  
1.  絶対パスとファイル名を使用して、保存する <xref:Microsoft.Office.Interop.Word.Document> の <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> メソッドを呼び出します。  指定された名前のファイルが既にフォルダーに存在する場合は、自動的に上書きされます。  
  
     次のコード例では、新しい名前を使用して、アクティブ文書を保存します。  このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスから実行します。  
  
    > [!NOTE]  
    >  ターゲット ディレクトリが存在しない場合や、ファイルを保存するうえで他の問題がある場合は、<xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> メソッドは例外をスローします。  <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> メソッドの周囲または呼び出しメソッドの内部に **try…catch** ブロックを使用することをお勧めします。  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## コードのコンパイル  
 このコード例に必要な条件は次のとおりです。  
  
-   文書を名前で指定して保存するには、ドライブ C の Test というディレクトリに NewDocument.doc という名前の文書が存在する必要があります。  
  
-   文書を新しい名前で保存するには、ドライブ C に Test というディレクトリが存在する必要があります。  
  
## 参照  
 [方法: プログラムによって文書を閉じる](../vsto/how-to-programmatically-close-documents.md)   
 [方法: プログラムによって既存文書を開く](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Document ホスト項目](../vsto/document-host-item.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  