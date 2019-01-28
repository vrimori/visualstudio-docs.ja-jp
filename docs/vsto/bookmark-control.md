---
title: Bookmark コントロール
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 10594bb52ca8bfad14acb162b46d86b3b80fdd31
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873679"
---
# <a name="bookmark-control"></a>Bookmark コントロール
  <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールは、一意の名前を持ち、イベントを公開し、データにバインドできるブックマークです。 ブックマークは、Microsoft Office Word 文書内の項目または位置をマークするためのプレースホルダーとして使用できます。 <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールは、 <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクトと <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを組み合わせたものです。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 ドキュメント レベルのプロジェクトに追加することができます<xref:Microsoft.Office.Tools.Word.Bookmark>デザイン時または実行時にドキュメントにコントロール。 VSTO アドイン プロジェクトに追加することができます<xref:Microsoft.Office.Tools.Word.Bookmark>実行時に開いているドキュメントのコントロール。 詳細については、「[方法 :Word 文書に Bookmark コントロールを追加](../vsto/how-to-add-bookmark-controls-to-word-documents.md)します。

## <a name="bind-data-to-the-control"></a>データをコントロールにバインドします。
 <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールでは、単純データ バインディングがサポートされます。 ブックマークは、 <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> プロパティを使用してデータ ソースにバインドする必要があります。 ブックマークの既定のデータ バインディング プロパティは、 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> プロパティです。

 バインドされたデータセット内のデータが更新された場合、<xref:Microsoft.Office.Tools.Word.Bookmark>コントロールは、変更を示しています。

 ドキュメント レベルのプロジェクトでは、 **[データ ソース]** ウィンドウを使用してブックマークにデータをバインドすることもできます。 詳細については、「[方法 :オブジェクトからのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)します。

## <a name="formatting"></a>書式設定
 <xref:Microsoft.Office.Interop.Word.Bookmark> に適用できる書式設定は、 <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールに適用できます。 この書式設定するには、フォント、インデント、間隔、番号、およびスタイルが含まれます。

## <a name="assign-text-to-the-bookmark"></a>ブックマークにテキストを割り当てる
 <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> オブジェクトと <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> コントロールのもう 1 つの違いに、テキストをブックマークに割り当てる場合の動作があります。 長さゼロの <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>にテキストを割り当てた場合、テキストはブックマークの右側に追加されるため、ブックマークの長さはゼロのままです。 しかし、長さゼロの <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>にテキストを割り当てた場合、テキストはブックマークに挿入されるため、ブックマークの長さは、挿入された文字の合計数に拡張されます。

 <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> コントロールには <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> プロパティもあります。 このプロパティは異なる、<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>で利用可能なプロパティ、<xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType>のプロパティを<xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>コントロール、または<xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType>のプロパティを<xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>オブジェクト。

|Text プロパティ|説明|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|このプロパティは、ブックマーク内にテキストを表示し、そのブックマークを文書上に維持する場合に使用します。 ブックマークにテキストを割り当てると、ブックマークの範囲が拡張され、そのブックマークは削除されません。<br /><br /> たとえば、 `Bookmark1.Text = "Hello world"` の場合、テキストがブックマークに挿入され、ブックマークが失われることはありません。|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|このプロパティは、ブックマークの位置にテキストを表示し、そのブックマークを自動的に削除する場合に使用します。 たとえば、 `Bookmark1.Range.Text = "Hello world"` の場合、テキストがブックマークに挿入され、そのブックマークは削除されます。|

## <a name="rename-the-control-at-design-time"></a>デザイン時にコントロールの名前を変更します。
 ドキュメント レベルのプロジェクトで、 <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを **[ツールボックス]** から文書にドラッグすると、Visual Studio によってコントロールの名前が自動的に生成されます。 コントロールの名前は **[プロパティ]** ウィンドウで変更できます。

## <a name="overlapping-controls"></a>コントロールの重複
 Bookmark コントロールは、互いに重複できます。 同じテキストは、1 つ以上のブックマークで共有できます。 に重複するブックマークの 1 つを新しいテキストを割り当てるときに新しいテキストのみが含まれているし、ブックマークは重複しなくします。 その他のブックマークには、今すぐが元の重複するブックマークの間で共有されるテキストのみが含まれています。

 次の表では、「This is sample text.」という文が 2 つの重複するブックマークで共有されます。

|ブックマーク|テキスト|
|--------------|----------|
|重複するブックマーク|[this is {sample] text.}|
|Bookmark1|This is sample|
|Bookmark2|sample text.|

 Bookmark1 に新しいテキスト「This is replacement.」を割り当てると Bookmark1、するには、ブックマークは重複していない、Bookmark2 は bookmark1 の一部ではない最初のテキストのみを保持します。

|ブックマーク|テキスト|
|--------------|----------|
|2 つの別個のブックマーク|[this is replacement]{ text.}|
|Bookmark1|This is replacement|
|Bookmark2|text.|

別のブックマークを含むブックマークのテキストを変更すると、内部のブックマークは削除されません。 ただし、内部のブックマークは、空のブックマークになり、外側のブックマークの末尾に移動します。

次の表では、「This is sample text.」という文が 別のブックマーク内に含まれるブックマークで共有されます。

|ブックマーク|テキスト|
|--------------|----------|
|重複するブックマーク|[this is {sample} text.]|
|Bookmark1|This is sample text.|
|Bookmark2|サンプル|

 Bookmark1 に新しいテキスト「This is replacement.」を割り当てると 、これらの 2 つのブックマークは重複しなくなり、Bookmark2 は Bookmark1 の末尾にある空のブックマークになります。

|ブックマーク|テキスト|
|--------------|----------|
|2 つの別個のブックマーク|[置換はこれです。]{}|
|Bookmark1|This is replacement.|
|Bookmark2|*\<empty>*|

## <a name="events"></a>イベント

次のイベントは <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールに対して利用できます。

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>

-   <xref:System.ComponentModel.IComponent.Disposed>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>

## <a name="see-also"></a>関連項目

- [拡張オブジェクトを使用して Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)
- [方法: Word 文書に Bookmark コントロールを追加します。](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [チュートリアル: ブックマークのショートカット メニューを作成します。](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)
- [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)