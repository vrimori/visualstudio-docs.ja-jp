---
title: "方法 : Bookmark コントロールのサイズを変更する"
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
  - "コントロール [Visual Studio での Office 開発]、サイズ変更"
  - "Bookmark コントロール、サイズ変更"
ms.assetid: 3de1c774-921a-4113-a54a-e3b8d4a65d53
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# 方法 : Bookmark コントロールのサイズを変更する
  <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールのサイズは、Microsoft Office Word ドキュメントに追加するときに設定します。 サイズは後から変更することもできます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ブックマークのサイズは、次の 3 通りの方法で変更できます。  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark> コントロール内でテキストを追加または削除する。  
  
     ブックマークのテキストを追加するたびに、ブックマークのサイズは自動的に、新しいテキスト分だけ大きくなります。 テキストを削除すると、ブックマークのサイズは自動的に小さくなります。  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールの <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> および <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> プロパティを変更する。  
  
     これは、数文字分だけサイズを変更する場合に役立ちます。  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを作成し直す。  
  
     これは、ブックマークのサイズや場所に大幅な変更がある場合に便利です。  
  
 ドキュメント レベルのプロジェクトでは、デザイン時または実行時にプロジェクトの文書に <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを追加できます。 VSTO アドイン プロジェクトでは、実行時に、開いている任意の文書に <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを追加できます。 詳細については、「[方法 : Word 文書に Bookmark コントロールを追加する](../vsto/how-to-add-bookmark-controls-to-word-documents.md)」を参照してください。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Start および End プロパティの変更  
  
#### デザイン時にドキュメント レベルのプロジェクト内のブックマークのサイズを変更するには  
  
1.  **\[プロパティ\]** ウィンドウでブックマークを選択します。  
  
2.  <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> プロパティの値を増減させます。  
  
3.  <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> プロパティの値を増減させます。  
  
#### 実行時にドキュメント レベルのプロジェクト内のブックマークのサイズを変更するには  
  
1.  実行時またはデザイン時に作成した <xref:Microsoft.Office.Tools.Word.Bookmark> の <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> および <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> プロパティを変更します。  
  
     次のコード例では、`SampleBookmark` という名前のブックマークの先頭に 5 文字を追加します。 このコードでは、ブックマークの前に 5 文字以上のテキストがあることを前提としています。  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#2)]  
  
     次のコード例では、同じブックマークの末尾に 5 文字を追加します。 このコードでは、ブックマークの後に 5 文字以上のテキストがあることを前提としています。  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#3)]  
  
#### 実行時に VSTO アドイン プロジェクト内のブックマークのサイズを変更するには  
  
1.  実行時またはデザイン時に作成した <xref:Microsoft.Office.Tools.Word.Bookmark> の <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> および <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> プロパティを変更します。  
  
     次のコード例では、アクティブなドキュメントの最初の段落のテキストを含む <xref:Microsoft.Office.Tools.Word.Bookmark> を作成した後、<xref:Microsoft.Office.Tools.Word.Bookmark> の先頭と末尾から 5 文字を削除します。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#16)]
     [!code-vb[Trin_WordAddInDynamicControls#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#16)]  
  
## ブックマークの再作成  
 ドキュメント レベルのプロジェクト内のブックマークのサイズを変更するには、既存のブックマークと同じ名前の新しいブックマークを別のサイズで作成します。  
  
#### デザイン時にドキュメント レベルのプロジェクト内のブックマークを再作成するには  
  
1.  新しい <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールに含めるテキストを選択します。  
  
2.  **\[挿入\]** メニューで **\[ブックマーク\]** をクリックします。  
  
3.  **\[ブックマーク\]** ダイアログ ボックスで、サイズを変更するブックマークの名前を選択し、**\[追加\]** をクリックします。  
  
## 参照  
 [方法 : Word 文書に Bookmark コントロールを追加する](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [方法 : NamedRange コントロールのサイズを変更する](../vsto/how-to-resize-namedrange-controls.md)   
 [方法 : ListObject コントロールのサイズを変更する](../vsto/how-to-resize-listobject-controls.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  