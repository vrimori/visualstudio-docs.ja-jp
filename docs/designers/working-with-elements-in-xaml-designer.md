---
title: XAML デザイナーでの要素の操作
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 02d3a9dfa6496b30e7438e53754f6d3d1720e6df
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078928"
---
# <a name="working-with-elements-in-xaml-designer"></a>XAML デザイナーでの要素の操作
アプリに、コントロール、レイアウト、図形などの要素を追加するには、XAML、コード、または XAML デザイナーを使用します。 このトピックでは、Visual Studio または Blend for Visual Studio で XAML デザイナーを使用して要素を操作する方法について説明します。

## <a name="adding-an-element-to-a-layout"></a>レイアウトに要素を追加する
 *レイアウト*とは、UI に要素を配置してサイズ変更するプロセスです。 ビジュアル要素を配置するには、それらを [Panel](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.panel.aspx) レイアウトに配置する必要があります。 `Panel` には、[FrameworkElement](http://msdn.microsoft.com/library/windows/apps/br208706.aspx) 型のコレクションである子プロパティがあります。 `Panel` のさまざまな子要素 ([Canvas](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.canvas.aspx)、[StackPanel](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx)、[Grid](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) など) をレイアウト コンテナーとして利用し、ページに要素を配置して整列することができます。

 既定では、`Grid` パネルをページまたはフォーム内の最上位のレイアウト コンテナーとして使用します。 最上位のページ レイアウト内に、レイアウト パネル、コントロール、その他の要素を追加していきます。

#### <a name="to-add-an-element-to-a-layout"></a>レイアウトに要素を追加するには

-   XAML デザイナーで、次のいずれかの操作を行います。

    -   **[ツールボックス]** にある要素をダブルクリックします (または、ツールボックスにある要素を選択して **Enter** キーを押します)。

    -   要素を **[ツールボックス]** からアートボードにドラッグします。

    -   **[ツールボックス]** で、いずれかの描画ツール ([[楕円]](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.ellipse.aspx) や [[四角形]](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx) など) を選択し、アクティブなパネルに要素を描画します。

## <a name="changing-the-layering-order-of-elements"></a>要素の重ね順の変更
 XAML デザイナーのアートボード上に 2 つの要素がある場合、1 つの要素はもう一方の要素より重ね順が前に表示されます。 [ドキュメント アウトライン] ウィンドウで要素の一覧の最下位にある要素が最前面の要素です (要素の **[ZIndex]** プロパティが設定されている場合を除く)。 ページ、フォーム、またはレイアウト コンテナーに要素を挿入するとき、自動的に要素はアクティブなコンテナー要素内の他の要素より前面に配置されます。 要素の順序を変更するには、**[順序]** コマンドを使用するか、[ドキュメント アウトライン] ウィンドウのオブジェクト ツリーで要素をドラッグします。

#### <a name="to-change-the-layering-order"></a>重ね順を変更するには

-   次のいずれかの操作を行います。

    -   **[ドキュメント アウトライン]** ウィンドウで要素を上下にドラッグして目的の重ね順を作成します。

    -   重ね順を変更する要素を [ドキュメント アウトライン] ウィンドウまたはアートボードで右クリックし、**[順序]** をポイントした後、次のいずれかをクリックします。

        -   **[最前面へ移動]**: 要素を重ね順の一番前に移動します。

        -   **[前面へ移動]**: 要素を重ね順の 1 つ前に移動します。

        -   **[背面へ移動]**: 要素を重ね順の 1 つ後ろに移動します。

        -   **[最背面へ移動]**: 要素を重ね順の一番後ろに移動します。

     [プロパティ] ウィンドウの **[レイアウト]** セクションで **[ZIndex]** プロパティを変更します。 要素が重なり合うときは、**[ZIndex]** プロパティのほうが、[ドキュメント アウトライン] ウィンドウに表示される要素の順序よりも優先されます。 **[ZIndex]** 値が大きい要素ほど、他の要素より前に表示されます。

## <a name="changing-the-alignment-of-an-element"></a>要素の配置を変更する
 アートボードで要素の配置を調整するには、メニュー コマンドを使用するか、要素をスナップ ガイドラインに沿ってドラッグします。

 *スナップ ガイドライン*は、アプリ内の他の要素に対して要素を整列させる場合に役立つ視覚上の手掛かりです。

#### <a name="to-align-two-or-more-elements-by-using-menu-commands"></a>メニュー コマンドを使用して 2 つ以上の要素の位置を揃えるには

1.  位置を揃える要素を選択します。 複数の要素を選択するには、**Ctrl** キーを押したまま、要素を選択します。

2.  [プロパティ] ウィンドウの **[レイアウト]** セクションの **[HorizontalAlignment]** で、次のいずれかを選択します: **[Left]**、**[Center]**、**[Right]**、または **[Stretch]**。

3.  [プロパティ] ウィンドウの **[レイアウト]** セクションの **[VerticalAlignment]** で、次のいずれかを選択します: **[Top]**、**[Center]**、**[Bottom]**、または **[Stretch]**。

#### <a name="to-align-two-or-more-elements-by-using-snaplines"></a>スナップ ガイドラインを使用して 2 つ以上の要素の位置を揃えるには

-   XAML デザイナーでは、レイアウトに少なくとも 2 つの要素が含まれている場合、1 つの要素がもう 1 つの要素の端と揃うようにドラッグしたりサイズを変更したりできます。

     端が揃うと、合図として*位置揃えライン*が表示されます。 位置揃えライン (スナップ ガイドライン) は赤色の破線です。 位置揃えラインは、 **[スナップ ガイドラインへのスナップ]** が有効に設定されている場合にのみ表示されます。 位置揃えラインが表示されたアートボードの図解は、「[XAML デザイナーを使用した UI の作成](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)」をご覧ください。

## <a name="changing-an-elements-margins"></a>要素の余白の変更
 XAML デザイナーでの余白により、アートボード上で要素の周りに確保される空白領域の量が決まります。 たとえば、要素の外側の端と、その要素を格納している `Grid` パネルの境界との間に取られる領域の大きさは、余白によって指定されます。 また、`StackPanel` に含まれる要素間の領域の量も、余白によって指定されます。

#### <a name="to-change-an-elements-margins-in-the-properties-window"></a>[プロパティ] ウィンドウで要素の余白を変更するには

1.  余白を変更する要素を選択します。

2.  [プロパティ] ウィンドウの **[レイアウト]** で、いずれかの **[Margin]** プロパティ (**[Top]**、**[Left]**、**[Right]**、**[Bottom]**) の値 (単位はピクセル。デバイスに依存しない単位。約 1/96 インチ) を変更します。

#### <a name="to-change-an-elements-margins-in-the-artboard"></a>アートボードで要素の余白を変更するには

-   レイアウト コンテナーを基準として要素の余白を変更するには、レイアウト コンテナー内にある要素を選択したときにアートボードで要素の周りに表示される*余白ガイド*をクリックします。 余白ガイドを示す図解は、「[XAML デザイナーを使用した UI の作成](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)」をご覧ください。

     縦方向または横方向の余白ガイドが開いている場合、余白は設定されていません。 余白ガイドが閉じている場合は、余白が設定されています。

     空白ガイドを開いたときに、反対側の余白が設定されていないと、反対側の空白は、アートボードの要素の場所に従って適切な値に設定されます。 **[Left]** と **[Right]** の余白のような向かい側の余白の場合は、少なくとも一方のプロパティが常に設定されます。

    > [!IMPORTANT]
    >  <xref:Windows.UI.Xaml.Controls.Canvas> など、一部のレイアウト コンテナーの内部に配置された要素には、空白ガイドがありません。 <xref:Windows.UI.Xaml.Controls.StackPanel> 内の要素に配置する要素には、`StackPanel` の方向に従って、左右の余白またはの上下の余白のいずれかに余白ガイドがあります。

## <a name="grouping-and-ungrouping-elements"></a>要素のグループ化とグループ解除
 XAML デザイナーで 2 つ以上の要素をグループ化するには、新しいレイアウト コンテナーを作成して、グループ化する要素をその中に配置します。 複数の要素を 1 つのレイアウト コンテナーにまとめて配置すると、そのグループ内の複数の要素を単一の要素のように簡単に選択、移動、および変換することができます。 グループ化は、相互に関係のある複数の要素 (1 つのナビゲーション要素を構成するボタンなど) を識別するためにも便利です。 要素のグループ化を解除するには、それらの要素を含むレイアウト コンテナーを削除するだけです。

#### <a name="to-group-elements-into-a-new-layout-container"></a>要素を新しいレイアウト コンテナーに入れてグループ化するには

1.  グループ化する要素を選択します。 (複数の要素を選択するには、**Ctrl** キーを押しながらクリックします。)

2.  選択した要素を右クリックし、**[グループ (パネル) に含める]** をポイントし、そのグループを配置するレイアウト コンテナーの種類をクリックします。

    > [!TIP]
    >  要素をグループ化するために <xref:Windows.UI.Xaml.Controls.Viewbox>、<xref:Windows.UI.Xaml.Controls.Border>、または <xref:Windows.UI.Xaml.Controls.ScrollViewer> を選択すると、<xref:Windows.UI.Xaml.Controls.Viewbox>、<xref:Windows.UI.Xaml.Controls.Border>、または <xref:Windows.UI.Xaml.Controls.ScrollViewer> 内の新しい <xref:Windows.UI.Xaml.Controls.Grid> パネルに要素が配置されます。 これらのレイアウト コンテナーのいずれかに配置した要素をグループ解除すると、<xref:Windows.UI.Xaml.Controls.Viewbox>、<xref:Windows.UI.Xaml.Controls.Border>、または <xref:Windows.UI.Xaml.Controls.ScrollViewer> のみが削除され、<xref:Windows.UI.Xaml.Controls.Grid> パネルは残ります。 この `Grid` パネルを削除するには、要素をもう一度グループ解除します。

#### <a name="to-ungroup-elements-and-delete-the-layout"></a>要素をグループ解除してレイアウトを削除するには

-   グループ解除するグループを右クリックして、**[グループ解除]** をクリックします。

 要素のグループ化やグループ解除を行うには、[ドキュメント アウトライン] ウィンドウで選択したアイテムを右クリックして、**[グループ (パネル) に含める]** または **[グループ解除]** をクリックします。

## <a name="resetting-the-element-layout"></a>要素のレイアウトをリセットする
 要素の特定のレイアウト プロパティを既定値に戻すには、レイアウトのリセットのコマンドを使用します。 このコマンドを使用すると、要素の余白、配置、幅、高さ、およびサイズを、個別に、または一括してリセットできます。

#### <a name="to-reset-the-element-layout"></a>要素のレイアウトをリセットするには

-   [ドキュメント アウトライン] ウィンドウまたはアートボードで要素を右クリックし、**[レイアウト]** > **[*PropertyName* のリセット]** の順に選択します。ここで、*PropertyName* は、リセットするプロパティです (あるいは、要素のすべてのレイアウト プロパティをリセットするには、**[レイアウト]** > **[すべてリセット]** の順に選択します)。

## <a name="see-also"></a>関連項目

- [XAML デザイナーを使用した UI の作成](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
