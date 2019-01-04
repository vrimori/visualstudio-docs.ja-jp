---
title: '方法: プログラムによってブックマークのテキストを更新します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cdbecf7ea507fdf630ebd3cc4bf50092826292dc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864337"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>方法: プログラムによってブックマークのテキストを更新します。
  Microsoft Office Word 文書のプレースホルダー ブックマークにテキストを挿入することにより、そのテキストを後で取得したり、ブックマーク内のテキストを置き換えたりすることができます。 ドキュメント レベルのカスタマイズを開発している場合は、データにバインドされた <xref:Microsoft.Office.Tools.Word.Bookmark> コントロール内のテキストを更新することもできます。 詳細については、次を参照してください。 [Office ソリューションでのコントロールにデータをバインド](../vsto/binding-data-to-controls-in-office-solutions.md)します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ブックマーク オブジェクトには次の 2 種類があります。  
  
- <xref:Microsoft.Office.Tools.Word.Bookmark> ホスト コントロール。  
  
   <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールは、ネイティブ <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクトを拡張したもので、データのバインドとイベントの公開が可能になります。 ホスト コントロールの詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)します。  
  
- ネイティブ <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクト。  
  
   <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクトには、イベントや、データのバインド機能はありません。  
  
  ブックマークにテキストを割り当てる場合、<xref:Microsoft.Office.Interop.Word.Bookmark> と <xref:Microsoft.Office.Tools.Word.Bookmark> の動作は異なります。 詳細については、次を参照してください。 [Bookmark コントロール](../vsto/bookmark-control.md)します。  
  
## <a name="use-host-controls"></a>ホスト コントロールを使用します。  
  
### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Bookmark コントロールを使用してブックマークの内容を更新するには  
  
1.  ブックマークの名前を指定する引数 `bookmark` と <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> プロパティに割り当てる文字列を指定する引数 `newText` を受け取るプロシージャを作成します。  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールの <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> または <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> プロパティにテキストを割り当てても、ブックマークは削除されません。  
  
     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]  
  
2.  割り当てる、 *newText*する文字列、<xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>のプロパティ、<xref:Microsoft.Office.Tools.Word.Bookmark>します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]  
  
## <a name="use-word-objects"></a>Word オブジェクトを使用して、  
  
### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Word の Bookmark オブジェクトを使用してブックマークの内容を更新するには  
  
1.  <xref:Microsoft.Office.Interop.Word.Bookmark> の名前を指定する引数 `bookmark` とブックマークの <xref:Microsoft.Office.Interop.Word.Range.Text%2A> プロパティに割り当てる文字列を指定する引数 `newText` を受け取るプロシージャを作成します。  
  
    > [!NOTE]  
    >  Word のネイティブ <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクトにテキストを割り当てると、ブックマークは削除されます。  
  
     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]  
  
2.  割り当てる、 *newText*する文字列、<xref:Microsoft.Office.Interop.Word.Range.Text%2A>ブックマークを自動的に削除すると、ブックマークのプロパティ。 その後、<xref:Microsoft.Office.Interop.Word.Bookmarks> コレクションにブックマークを再び追加します。  
  
     次のコード例はドキュメント レベルのカスタマイズで使用できます。  
  
     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]  
  
     次のコード例は VSTO アドインで使用できます。 この例ではアクティブ ドキュメントを使用します。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによって Word 文書にテキストを挿入します。](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [Bookmark コントロール](../vsto/bookmark-control.md)  
