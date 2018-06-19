---
title: Bookmark コントロール
ms.date: 02/02/2017
ms.technology: office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 60ab9db37f3ed41de4afcdecbf2c9e83ffb5c2f6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264013"
---
# <a name="bookmark-control"></a>Bookmark コントロール
  <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールは、一意の名前を持ち、イベントを公開し、データにバインドできるブックマークです。 ブックマークは、Microsoft Office Word 文書内の項目または位置をマークするためのプレースホルダーとして使用できます。 <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールは、 <xref:Microsoft.Office.Interop.Word.Bookmark> オブジェクトと <xref:Microsoft.Office.Interop.Word.Range> オブジェクトを組み合わせたものです。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 ドキュメント レベルのプロジェクトに追加することができます<xref:Microsoft.Office.Tools.Word.Bookmark>をデザイン時または実行時にドキュメントにコントロールできます。 追加することができます、VSTO アドイン プロジェクトで<xref:Microsoft.Office.Tools.Word.Bookmark>実行時に開いている文書にコントロールできます。 詳細については、次を参照してください。[する方法: Word 文書にコントロールをブックマークの追加](../vsto/how-to-add-bookmark-controls-to-word-documents.md)です。

## <a name="bind-data-to-the-control"></a>コントロールにデータをバインドします。
 <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールでは、単純データ バインディングがサポートされます。 ブックマークは、 <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> プロパティを使用してデータ ソースにバインドする必要があります。 ブックマークの既定のデータ バインディング プロパティは、 <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> プロパティです。

 バインドされたデータセット内のデータが更新された場合、<xref:Microsoft.Office.Tools.Word.Bookmark>コントロールは、変更を表示します。

 ドキュメント レベルのプロジェクトでは、 **[データ ソース]** ウィンドウを使用してブックマークにデータをバインドすることもできます。 詳細については、次を参照してください。[する方法: オブジェクトからのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)します。

## <a name="formatting"></a>書式設定
 <xref:Microsoft.Office.Interop.Word.Bookmark> に適用できる書式設定は、 <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールに適用できます。 この書式設定するには、フォント、インデント、間隔、番号、およびスタイルが含まれます。

## <a name="assign-text-to-the-bookmark"></a>ブックマークにテキストを割り当てる
 その他の違い、<xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>オブジェクトおよび<xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>コントロールはテキストがブックマークに割り当てられている場合の動作です。 長さ 0 にテキストを割り当てる場合<xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>ブックマークの右側にテキストを追加、およびブックマークは長さ 0 のままです。 ただし、長さ 0 にテキストを割り当てる場合<xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>テキストがブックマークに挿入される、およびブックマークの長さが挿入された文字の合計数に拡張されます。

 <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>コントロールもあります、<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>プロパティです。 このプロパティは異なる、<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>で利用可能なプロパティ、<xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType>のプロパティ、<xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>コントロール、または<xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType>のプロパティ、<xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>オブジェクト。

|Text プロパティ|説明|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|このプロパティは、ブックマーク内にテキストを表示し、そのブックマークを文書上に維持する場合に使用します。 ブックマークにテキストを割り当てると、ブックマークの範囲が拡張され、そのブックマークは削除されません。<br /><br /> たとえば、 `Bookmark1.Text = "Hello world"` の場合、テキストがブックマークに挿入され、ブックマークが失われることはありません。|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|このプロパティは、ブックマークの位置にテキストを表示し、そのブックマークを自動的に削除する場合に使用します。 たとえば、 `Bookmark1.Range.Text = "Hello world"` の場合、テキストがブックマークに挿入され、そのブックマークは削除されます。|

## <a name="rename-the-control-at-design-time"></a>デザイン時にコントロールの名前を変更します。
 ドキュメント レベルのプロジェクトで、 <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを **[ツールボックス]** から文書にドラッグすると、Visual Studio によってコントロールの名前が自動的に生成されます。 コントロールの名前は **[プロパティ]** ウィンドウで変更できます。

## <a name="overlapping-controls"></a>コントロールの重複
 Bookmark コントロールを相互に重複できます。 同じテキストは、複数のブックマークで共有できます。 重複するブックマークのいずれかに新しいテキストを割り当てるし、新しいテキストだけが含まれている、それらのブックマークは重複しなくされます。 これで、他のブックマークには、元の重複するブックマーク間で共有されていないテキストのみが含まれています。

 次の表では、「This is sample text.」という文が 2 つの重複するブックマークで共有されます。

|ブックマーク|テキスト|
|--------------|----------|
|重複するブックマーク|[this is {sample] text.}|
|Bookmark1|This is sample|
|Bookmark2|sample text.|

 Bookmark1 に新しいテキスト「This is replacement.」を割り当てると bookmark1 に、それらのブックマークが重なっていないし、Bookmark2 はもともと bookmark1 していなかったテキストだけが保持されます。

|ブックマーク|テキスト|
|--------------|----------|
|2 つの別個のブックマーク|[this is replacement]{ text.}|
|Bookmark1|This is replacement|
|Bookmark2|text.|

別のブックマークを含むブックマークのテキストを変更する場合、内部のブックマークは削除されません。 ただし、内部のブックマークは、空のブックマークになり、外側のブックマークの末尾に移動します。

次の表では、「This is sample text.」という文が 別のブックマーク内に含まれるブックマークで共有します。

|ブックマーク|テキスト|
|--------------|----------|
|重複するブックマーク|[this is {sample} text.]|
|Bookmark1|This is sample text.|
|Bookmark2|サンプル|

 Bookmark1 に新しいテキスト「This is replacement.」を割り当てると 、これらの 2 つのブックマークは重複しなくなり、Bookmark2 は Bookmark1 の末尾にある空のブックマークになります。

|ブックマーク|テキスト|
|--------------|----------|
|2 つの別個のブックマーク|[これは、置換です] です。{}|
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

## <a name="see-also"></a>関連項目

- [拡張オブジェクトによる Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)
- [方法: Word 文書に Bookmark コントロールを追加します。](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [チュートリアル: ブックマークのショートカット メニューを作成します。](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)
- [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)