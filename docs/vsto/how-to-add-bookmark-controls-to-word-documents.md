---
title: '方法: Word 文書に Bookmark コントロールを追加します。'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5c89e922f41104be880d598354440a4c6665a39e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904813"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>方法: Word 文書に Bookmark コントロールを追加します。
  ドキュメント レベルのプロジェクトに追加することができます<xref:Microsoft.Office.Tools.Word.Bookmark>デザイン時または実行時に、プロジェクトのドキュメントにコントロール。 VSTO アドイン プロジェクトに追加することができます<xref:Microsoft.Office.Tools.Word.Bookmark>実行時に開いているドキュメントのコントロール。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 このトピックでは、次のタスクについて説明します。  
  
- [デザイン時に Bookmark コントロールを追加します。](#designtime)  
  
- [ドキュメント レベルのプロジェクトの実行時に Bookmark コントロールを追加します。](#runtimedoclevel)  
  
- [VSTO アドイン プロジェクトでの実行時に Bookmark コントロールを追加します。](#runtimeaddin)  
  
  詳細については<xref:Microsoft.Office.Tools.Word.Bookmark>コントロールを参照してください[Bookmark コントロール](../vsto/bookmark-control.md)します。  
  
##  <a name="designtime"></a> デザイン時に Bookmark コントロールを追加します。  
 デザイン時にドキュメント レベルのプロジェクトの文書に <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを追加する方法はいくつかあります。  
  
- Visual Studio の **[ツールボックス]** を使用する方法。  
  
   <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールは、 **[ツールボックス]** から文書にドラッグできます。 既に **[ツールボックス]** を使用して Windows フォーム コントロールを文書に追加している場合は、この方法を選択できます。  
  
- Word 内から実行する方法。  
  
   ネイティブのブックマークを追加する場合と同じ方法で、文書に <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを追加できます。 この方法で追加すると、コントロールの作成時にコントロールの名前を指定できるという利点があります。  
  
- **[データ ソース]** ウィンドウから実行する方法。  
  
   <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを **[データ ソース]** ウィンドウから文書にドラッグできます。 これは、同時にコントロールをデータにバインドする場合に役立ちます。 Windows フォーム コントロールを追加するのと同じ方法で、 **[データ ソース]** ウィンドウからホスト コントロールを追加できます。 詳細については、次を参照してください。[データ連結と Windows フォーム](/dotnet/framework/winforms/data-binding-and-windows-forms)します。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>ツールボックスから文書に Bookmark コントロールを追加するには  
  
1.  **[ツールボックス]** を開き、 **[Word コントロール]** タブをクリックします。  
  
2.  <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを文書にドラッグします。  
  
     **[ブックマークの追加]** ダイアログ ボックスが表示されます。  
  
3.  ブックマークに含めるテキストまたはその他の項目を選択します。  
  
4.  **[OK]** をクリックします。  
  
     ブックマーク名を既定のままにしない場合は、 **[プロパティ]** ウィンドウで名前を変更します。  
  
#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Word で文書に Bookmark コントロールを追加するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デザイナーでホストされている文書で、ブックマークを追加する位置にカーソルを置くか、ブックマークで囲むテキストを選択します。  
  
2.  リボンの **[挿入]** タブで、 **[リンク]** グループの **[ブックマーク]** ボタンをクリックします。  
  
3.  **[ブックマーク]** ダイアログ ボックスで、新しいブックマークの名前を入力し、 **[追加]** をクリックします。  
  
##  <a name="runtimedoclevel"></a> ドキュメント レベルのプロジェクトの実行時に Bookmark コントロールを追加します。  
 追加することができます<xref:Microsoft.Office.Tools.Word.Bookmark>のメソッドを使用して実行時にドキュメントにコントロールをプログラムによって、<xref:Microsoft.Office.Tools.Word.Document.Controls%2A>のプロパティ、`ThisDocument`プロジェクト内のクラス。 2 つのメソッド オーバーロードを使用して、次の方法で <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを追加できます。  
  
- 指定した範囲に <xref:Microsoft.Office.Tools.Word.Bookmark> を追加する。  
  
- 文書のネイティブなブックマーク (つまり、 <xref:Microsoft.Office.Tools.Word.Bookmark> ) に基づいて <xref:Microsoft.Office.Interop.Word.Bookmark>を追加する。  
  
  動的に作成された <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールは、文書を閉じるときに文書に残りません。 ただし、ネイティブな <xref:Microsoft.Office.Interop.Word.Bookmark> は文書に残ります。 ネイティブなブックマークに基づく <xref:Microsoft.Office.Tools.Word.Bookmark> は、次に文書を開いた時点で再作成できます。 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)します。  
  
#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>プログラムによって文書に Bookmark コントロールを追加するには  
  
1.  文書内の最初の段落に `ThisDocument_Startup` コントロールを追加するには、次のコードをプロジェクトの <xref:Microsoft.Office.Tools.Word.Bookmark> イベント ハンドラーに挿入します。  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  既存の <xref:Microsoft.Office.Tools.Word.Bookmark> から <xref:Microsoft.Office.Interop.Word.Bookmark>コントロールを作成する場合は、 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> メソッドを使用し、既存の <xref:Microsoft.Office.Interop.Word.Bookmark>を渡します。  
  
##  <a name="runtimeaddin"></a> VSTO アドイン プロジェクトでの実行時に Bookmark コントロールを追加します。  
 追加することができます<xref:Microsoft.Office.Tools.Word.Bookmark>VSTO アドインを使用して実行時に開いている文書をプログラムで制御します。 そのためには、開いている文書に基づいた <xref:Microsoft.Office.Tools.Word.Document> ホスト項目を生成し、このホスト項目の <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> プロパティのメソッドを使用します。 2 つのメソッド オーバーロードを使用して、次の方法で <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを追加できます。  
  
- 指定した範囲に <xref:Microsoft.Office.Tools.Word.Bookmark> を追加する。  
  
- 文書のネイティブなブックマーク (つまり、 <xref:Microsoft.Office.Tools.Word.Bookmark> ) に基づいて <xref:Microsoft.Office.Interop.Word.Bookmark>を追加する。  
  
  動的に作成された <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールは、文書を閉じるときに文書に残りません。 ただし、ネイティブな <xref:Microsoft.Office.Interop.Word.Bookmark> は文書に残ります。 ネイティブなブックマークに基づく <xref:Microsoft.Office.Tools.Word.Bookmark> は、次に文書を開いた時点で再作成できます。 詳細については、次を参照してください。 [Office ドキュメントでのダイナミック コントロールを永続化](../vsto/persisting-dynamic-controls-in-office-documents.md)します。  
  
  VSTO アドイン プロジェクトでホスト項目の生成の詳細については、次を参照してください。[拡張 Word 文書や Excel ブックを実行時に VSTO アドインで](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)します。  
  
#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>指定した範囲に Bookmark コントロールを追加するには  
  
1.  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> メソッドを使用し、 <xref:Microsoft.Office.Interop.Word.Range> を追加する <xref:Microsoft.Office.Tools.Word.Bookmark>を渡します。  
  
     作業中の文書の先頭に新しい <xref:Microsoft.Office.Tools.Word.Bookmark> を追加するコード例を次に示します。 この例を使用するには、Word VSTO アドイン プロジェクトの `ThisAddIn_Startup` イベント ハンドラーからコードを実行します。  
  
     [!code-vb[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#4)]  
  
#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>ネイティブなブックマーク コントロールに基づく Bookmark コントロールを追加するには  
  
1.  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> メソッドを使用し、新しい <xref:Microsoft.Office.Interop.Word.Bookmark> の基として使用する既存の <xref:Microsoft.Office.Tools.Word.Bookmark>を渡します。  
  
     作業中の文書の最初の <xref:Microsoft.Office.Tools.Word.Bookmark> に基づく新しい <xref:Microsoft.Office.Interop.Word.Bookmark> を作成するコード例を次に示します。 この例を使用するには、Word VSTO アドイン プロジェクトの `ThisAddIn_Startup` イベント ハンドラーからコードを実行します。  
  
     [!code-vb[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#5)]  
  
## <a name="see-also"></a>関連項目  
 [拡張オブジェクトを使用して Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)   
 [プログラムのドキュメント レベルのカスタマイズ](../vsto/programming-document-level-customizations.md)   
 [方法: ブックマーク コントロールをサイズ変更します。](../vsto/how-to-resize-bookmark-controls.md)  
