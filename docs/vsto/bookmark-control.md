---
title: "Bookmark コントロール |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
ms.assetid: 940bf165-18c9-4db8-a46c-aad786b8bbad
caps.latest.revision: "55"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a946c190197b40dbc51fe2ddbcff434a21d84c11
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="bookmark-control"></a>Bookmark コントロール
  <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールは、一意の名前を持ち、イベントを公開し、データにバインドできるブックマークです。 ブックマークは、Microsoft Office Word 文書内の項目または位置をマークするためのプレースホルダーとして使用できます。 <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールは、 <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクトと <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを組み合わせたものです。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ドキュメント レベルのプロジェクトでは、デザイン時または実行時に、文書に <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを追加できます。 VSTO アドイン プロジェクトでは、実行時に、開いている任意の文書に <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを追加できます。 詳細については、「 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)」を参照してください。  
  
## <a name="binding-data-to-the-control"></a>コントロールへのデータのバインド  
 <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールでは、単純データ バインディングがサポートされます。 ブックマークは、 <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> プロパティを使用してデータ ソースにバインドする必要があります。 ブックマークの既定のデータ バインディング プロパティは、 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> プロパティです。  
  
 バインドされたデータセット内のデータが更新されると、 <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールがその変更を反映させます。  
  
 ドキュメント レベルのプロジェクトでは、 **[データ ソース]** ウィンドウを使用してブックマークにデータをバインドすることもできます。 詳細については、「 [How to: Populate Documents with Data from Objects](../vsto/how-to-populate-documents-with-data-from-objects.md)」を参照してください。  
  
## <a name="formatting"></a>書式設定  
 <xref:Microsoft.Office.Interop.Word.Bookmark> に適用できる書式設定は、 <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールに適用できます。 この書式設定には、フォント、インデント、間隔、番号付け、およびスタイルが含まれます。  
  
## <a name="assigning-text-to-the-bookmark"></a>ブックマークへのテキストの割り当て  
 <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクトと <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールのもう 1 つの違いに、テキストをブックマークに割り当てる場合の動作があります。 長さゼロの <xref:Microsoft.Office.Interop.Word.Bookmark>にテキストを割り当てた場合、テキストはブックマークの右側に追加されるため、ブックマークの長さはゼロのままです。 しかし、長さゼロの <xref:Microsoft.Office.Tools.Word.Bookmark>にテキストを割り当てた場合、テキストはブックマークに挿入されるため、ブックマークの長さは、挿入された文字の合計数に拡張されます。  
  
 <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールには <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> プロパティもあります。 このプロパティは、 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> コントロールの <xref:Microsoft.Office.Tools.Word.Bookmark.Range%2A> プロパティ、または <xref:Microsoft.Office.Tools.Word.Bookmark> オブジェクトの <xref:Microsoft.Office.Interop.Word.Bookmark.Range%2A> プロパティで使用できる <xref:Microsoft.Office.Interop.Word.Bookmark> プロパティとは異なります。  
  
|Text プロパティ|説明|  
|-------------------|-----------------|  
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>|このプロパティは、ブックマーク内にテキストを表示し、そのブックマークを文書上に維持する場合に使用します。 ブックマークにテキストを割り当てると、ブックマークの範囲が拡張され、そのブックマークは削除されません。<br /><br /> たとえば、 `Bookmark1.Text = "Hello world"` の場合、テキストがブックマークに挿入され、ブックマークが失われることはありません。|  
|<xref:Microsoft.Office.Interop.Word.Range.Text%2A>|このプロパティは、ブックマークの位置にテキストを表示し、そのブックマークを自動的に削除する場合に使用します。 たとえば、 `Bookmark1.Range.Text = "Hello world"` の場合、テキストがブックマークに挿入され、そのブックマークは削除されます。|  
  
## <a name="renaming-the-control-at-design-time"></a>デザイン時のコントロールの名前変更  
 ドキュメント レベルのプロジェクトで、 <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを **[ツールボックス]** から文書にドラッグすると、Visual Studio によってコントロールの名前が自動的に生成されます。 コントロールの名前は **[プロパティ]** ウィンドウで変更できます。  
  
## <a name="overlapping-controls"></a>コントロールの重複  
 Bookmark コントロールは互いに重複できます。つまり、同じテキストを複数のブックマークで共有できます。 重複しているブックマークの 1 つに新しいテキストを割り当てると、そのブックマークには新しいテキストだけが含まれるようになり、それらのブックマークは重複しなくなります。 他のブックマークには、元の重複していたブックマーク間で共有されていなかったテキストだけが含まれるようになります。  
  
 次の表では、「This is sample text.」という文が 2 つの重複するブックマークでどのように共有されるかが示されています。  
  
|ブックマーク|テキスト|  
|--------------|----------|  
|重複するブックマーク|[this is {sample] text.}|  
|Bookmark1|This is sample|  
|Bookmark2|sample text.|  
  
 Bookmark1 に新しいテキスト「This is replacement.」を割り当てると 、これらの 2 つのブックマークは重複しなくなり、Bookmark2 にはもともと Bookmark1 と重複していなかったテキストだけが維持されます。  
  
|ブックマーク|テキスト|  
|--------------|----------|  
|2 つの別個のブックマーク|[this is replacement]{ text.}|  
|Bookmark1|This is replacement|  
|Bookmark2|text.|  
  
 あるブックマークが別のブックマーク内に完全に含まれている場合は、外側のブックマークのテキストを変更しても、内部のブックマークは削除されません。 ただし、内部のブックマークは、外側のブックマークの末尾に移動された空のブックマークになります。 次の表では、「This is sample text.」という文が 別のブックマーク内に含まれているブックマークによってどのように共有されるかが示されています。  
  
|ブックマーク|テキスト|  
|--------------|----------|  
|重複するブックマーク|[this is {sample} text.]|  
|Bookmark1|This is sample text.|  
|Bookmark2|サンプル|  
  
 Bookmark1 に新しいテキスト「This is replacement.」を割り当てると 、これらの 2 つのブックマークは重複しなくなり、Bookmark2 は Bookmark1 の末尾にある空のブックマークになります。  
  
|ブックマーク|テキスト|  
|--------------|----------|  
|2 つの別個のブックマーク|[this is replacement.]{}|  
|Bookmark1|This is replacement.|  
|Bookmark2|*\<空 >*|  
  
## <a name="events"></a>イベント  
 次のイベントは <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールに対して利用できます。  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>  
  
## <a name="see-also"></a>参照  
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [チュートリアル: ブックマークのショートカット メニューを作成します。](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  