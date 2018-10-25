---
title: エディター内で |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18587516298fa58e8a5e783ffb1f7c37d5a6b497
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859682"
---
# <a name="inside-the-editor"></a>エディター内で
エディターはさまざまなテキスト ビューとユーザー インターフェイスからモデルの個別のテキスト エディターを維持するために設計は、さまざまなサブシステムで構成されます。  
  
 これらのセクションでは、エディターのさまざまな側面について説明します。  
  
- [サブシステムの概要](../extensibility/inside-the-editor.md#overview-of-the-subsystems)  
  
- [テキスト モデル](../extensibility/inside-the-editor.md#the-text-model)  
  
- [テキスト ビュー](../extensibility/inside-the-editor.md#the-text-view)  
  
  これらのセクションでは、エディターの機能について説明します。  
  
- [タグおよび分類子](../extensibility/inside-the-editor.md#tags-and-classifiers)  
  
- [修飾](../extensibility/inside-the-editor.md#adornments)  
  
- [射影](../extensibility/inside-the-editor.md#projection)  
  
- [アウトライン](../extensibility/inside-the-editor.md#outlining)  
  
- [マウスのバインド](../extensibility/inside-the-editor.md#mousebindings)  
  
- [エディターの操作](../extensibility/inside-the-editor.md#editoroperations)  
  
- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
## <a name="overview-of-the-subsystems"></a>サブシステムの概要  
  
### <a name="text-model-subsystem"></a>テキスト モデル サブシステム  
 テキスト モデルのサブシステムはテキストを表すと、その操作を有効化します。 テキスト モデルのサブシステムを含む、<xref:Microsoft.VisualStudio.Text.ITextBuffer>インターフェイスで、エディターによって表示される文字のシーケンスについて説明します。 このテキストは、変更、追跡、およびそれ以外の場合さまざまな方法で操作できることができます。 テキスト モデルには、次の側面の型も用意されています。  
  
- ファイルでは、テキストを関連付け、読み取りとファイル システムで手書き入力を管理するサービス。  
  
- 2 つのシーケンス オブジェクトの間のわずかな差異を検出する差分サービス。  
  
- その他のバッファー内のテキストのサブセットの観点からのバッファー内のテキストを記述するためのシステム。  
  
  テキスト モデルのサブシステムでは、無料ユーザー インターフェイス (UI) の概念です。 たとえばはテキスト形式またはテキストのレイアウトを担当して visual 修飾テキストと関連付けることができるは、サポート技術情報を持ちません。  
  
  テキスト モデル サブシステムのパブリック型が含まれている*Microsoft.VisualStudio.Text.Data.dll*と*Microsoft.VisualStudio.CoreUtility.dll*、.NET Framework ベースののみに依存します。クラス ライブラリと Managed Extensibility Framework (MEF)。  
  
### <a name="text-view-subsystem"></a>テキスト ビュー サブシステム  
 テキスト ビューのサブシステムは書式設定およびテキストを表示します。 このサブシステム内の型は、種類が Windows Presentation Foundation (WPF) を利用するかどうかに応じて、2 つのレイヤーに分割されます。 最も重要なは<xref:Microsoft.VisualStudio.Text.Editor.ITextView>と<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>を表示するテキスト行のセットともキャレット、選択、および WPF UI 要素を使用して、テキストを装飾するための機能を制御します。 このサブシステムでは、領域を表示するテキストを囲む余白も提供します。 これらの余白は、拡張して、さまざまな種類のコンテンツや視覚エフェクトを含めることができます。 余白の例については、行番号の表示とスクロール バーです。  
  
 テキスト ビュー サブシステムのパブリック型が含まれている*Microsoft.VisualStudio.Text.UI.dll*と*Microsoft.VisualStudio.Text.UI.Wpf.dll*します。 最初のアセンブリには、プラットフォームに依存しない要素が含まれているし、2 つ目には、WPF 固有の要素が含まれています。  
  
### <a name="classification-subsystem"></a>分類サブシステム  
 分類のサブシステムが、テキストのフォント プロパティを判断します。 分類子は、「キーワード」、「コメント」など、別のクラスにテキストを分割します。 分類形式のマップに関連してこれらのクラス実際のフォントのプロパティ、たとえば、"Blue Consolas 10 pt"です。 この情報は、書式設定し、テキストを描画する場合、テキスト ビューで使用されます。 タグ付け、により、テキストの範囲に関連するデータをこのトピックの後半で説明に記載されています。  
  
 Microsoft.VisualStudio.Text.UI.Wpf.dll に含まれている分類の視覚的な側面とやり取りしているに Microsoft.VisualStudio.Text.Logic.dll、分類のサブシステムのパブリック型が含まれています。  
  
### <a name="operations-subsystem"></a>操作のサブシステム  
 操作のサブシステムでは、エディターの動作を定義します。 Visual Studio のエディター コマンドの実装と、元に戻すシステムを提供します。  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>テキスト モデルとテキスト ビューについて詳しく見て  
  
### <a name="the-text-model"></a>テキスト モデル  
 テキスト モデルのサブシステムは、テキスト型のさまざまなグループで構成されます。 テキスト バッファー、テキストのスナップショット、およびテキストの範囲が含まれます。  
  
#### <a name="text-buffers-and-text-snapshots"></a>テキスト バッファーとテキストのスナップショット  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer>インターフェイスは、これは、エンコードで使用される utf-16 を使用してエンコードされた Unicode 文字のシーケンスを表す、 `String` .NET Framework の型。 テキスト バッファーをファイル システムのドキュメントとして永続化することができますが、これは必要ありません。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> 、空のテキスト バッファーまたは文字列からまたはからに初期化されるテキスト バッファーを作成するために使用<xref:System.IO.TextReader>します。 テキスト バッファーとしてファイル システムに永続化できる、<xref:Microsoft.VisualStudio.Text.ITextDocument>します。  
  
 スレッドが呼び出すことによって、テキスト バッファーの所有権を取得するまで、すべてのスレッドからテキスト バッファーを編集できる<xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>します。 その後、そのスレッドのみが編集を実行できます。  
  
 テキスト バッファーは、その有効期間中に、多くのバージョンで移動できます。 バッファーが編集されるたびに、変更できない、新しいバージョンが生成される<xref:Microsoft.VisualStudio.Text.ITextSnapshot>そのバージョンのバッファーの内容を表します。 テキストのスナップショットは変更できないためにを表すテキスト バッファーが変化し続ける場合でも、制限なく、任意のスレッドでテキスト スナップショットにアクセスすることができます。  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>テキストのスナップショットとスナップショット行のテキスト  
 文字のシーケンス、または行のシーケンスとしては、テキストのスナップショットの内容を表示できます。 行の文字とは、0 から始まるインデックス両方が。 空のテキストのスナップショットには、ゼロの文字と 1 つの空の行が含まれています。 行は、有効な Unicode の改行文字シーケンス、または先頭またはバッファーの末尾で区切られます。 改行文字は、テキストのスナップショットに明示的に表現し、テキスト スナップショット内の改行はすべて同じであるがします。  
  
> [!NOTE]
>  Visual Studio エディターでの改行文字の詳細については、次を参照してください。[エンコーディングと改行](../ide/encodings-and-line-breaks.md)します。  
  
 によって表される行のテキスト、<xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>オブジェクトで、特定の行番号または特定の文字位置のテキスト スナップショットから取得できます。  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>Snapshotpoints は、SnapshotSpans、および NormalizedSnapshotSpanCollections  
 A<xref:Microsoft.VisualStudio.Text.SnapshotPoint>スナップショット内の文字位置を表します。 位置 0 とスナップショットの長さまでの値にすることが保証されます。 A<xref:Microsoft.VisualStudio.Text.SnapshotSpan>スナップショット内のテキストの範囲を表します。 終了位置 0 とスナップショットの長さまでの値にすることが保証されます。 <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>のセットから成る<xref:Microsoft.VisualStudio.Text.SnapshotSpan>同じスナップショットからのオブジェクト。  
  
#### <a name="spans-and-normalizedspancollections"></a>スパンと NormalizedSpanCollections  
 A<xref:Microsoft.VisualStudio.Text.Span>テキスト スナップショット内のテキストの範囲に適用できる間隔を表します。 スナップショットの位置は、範囲は 0 を含む任意の位置に起動できるように、0 から始まる。 `End`範囲のプロパティは、の合計に等しい、`Start`プロパティとその`Length`プロパティ。 A`Span`によってインデックスが設定された文字を含まない、`End`プロパティ。 開始のあるスパンなど = 5 と長さ = 3 はエンド = 8、5、6、および 7 の位置にある文字が含まれています。 このスパンの表記法は 5..8) です。  
  
 位置がある、共通の終了位置を含む場合、2 つの範囲が交差します。 交差部分ではそのため、[3, 5) と [2, 7) は [3, 5) との交差部分 [3, 5) と [5, 7) は [5, 5)。 (注意 [5, 5) は空の範囲)。  
  
 終了位置を除く位置が共通してある場合、2 つの範囲が重複します。 空の範囲では、もう一方の範囲では、決してと重複され、2 つの範囲の重複が空ではありません。  
  
 A<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>スパンの開始プロパティの順序の範囲の一覧を示します。 一覧で、重複または隣接する範囲がマージされます。 たとえば、範囲のセットを指定 [5..9)、[0..1)、[3..6)、および [9..10)、範囲の正規化されたリストは [0..1)、[3..10) します。  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit、TextVersion とテキストの変更通知  
 使用してテキスト バッファーの内容を変更することができます、<xref:Microsoft.VisualStudio.Text.ITextEdit>オブジェクト。 このようなオブジェクトを作成する (のいずれかを使用して、`CreateEdit()`メソッドの<xref:Microsoft.VisualStudio.Text.ITextBuffer>) テキストの編集で構成されるテキストのトランザクションが開始されます。 すべての編集は、文字列バッファー内のテキストの一部の範囲の代わりには。 座標とすべての編集のコンテンツは、トランザクションが開始されたときにバッファのスナップショットに対して相対的で表現されます。 <xref:Microsoft.VisualStudio.Text.ITextEdit>オブジェクトが同じトランザクション内で他の編集の影響を受ける編集の座標を調整します。  
  
 たとえば、この文字列を含むテキスト バッファーを検討してください。  
  
```  
abcdefghij  
```  
  
 2 つの編集、ある範囲を置換する 1 つの編集を含むトランザクションを適用 [2..4) 文字を使用して`X`に span を置換する 2 番目の編集と [6..9) 文字を使用して`Y`します。 このバッファーになります。  
  
```  
abXefYj  
```  
  
 最初の編集が適用される前に、トランザクションの先頭にバッファーの内容に関して 2 つ目の編集の座標が計算されます。  
  
 バッファーへの変更が反映時に、<xref:Microsoft.VisualStudio.Text.ITextEdit>オブジェクトが呼び出すことによってコミットされたその`Apply()`メソッド。 少なくとも 1 つの空でない編集があった場合、新しい<xref:Microsoft.VisualStudio.Text.ITextVersion>が作成されて、新しい<xref:Microsoft.VisualStudio.Text.ITextSnapshot>作成されると、1 つ`Changed`イベントが発生します。 すべてのテキスト バージョンが異なるテキスト スナップショット。 テキストのスナップショットが、編集トランザクション後にテキスト バッファーの完全な状態を表しますが、テキスト バージョンには、次に 1 つのスナップショットから変更のみがについて説明します。 一般に、テキストのスナップショットが 1 回使用するためのものし、その後破棄中に、テキストのバージョンはしばらくの間有効である必要があります。  
  
 テキストのバージョンが含まれています、<xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>します。 このコレクションには、変更がについて説明するスナップショットに適用すると、その後のスナップショットが生成されます。 すべて<xref:Microsoft.VisualStudio.Text.ITextChange>コレクション内で、変更、置き換えられた文字列、および置換文字列の文字の位置が含まれています。 置き換えられた文字列が空の基本的な挿入、置換文字列が空の基本的な削除. 正規化されたコレクションは常に`null`テキスト バッファーの最新バージョン。  
  
 1 つだけ<xref:Microsoft.VisualStudio.Text.ITextEdit>、いつでもテキスト バッファー オブジェクトをインスタンス化し、すべてのテキストの編集は、(所有権が要求されている) 場合は、テキスト バッファーを所有しているスレッドで実行する必要があります。 呼び出すことによってテキストの編集を破棄することができます、`Cancel`メソッドまたはその`Dispose`メソッド。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 用意されています`Insert()`、 `Delete()`、および`Replace()`に類似するメソッドがで検出された、<xref:Microsoft.VisualStudio.Text.ITextEdit>インターフェイス。 これらの呼び出しを作成すると同じ効果を持つ、<xref:Microsoft.VisualStudio.Text.ITextEdit>のような呼び出しを実行し、編集を適用しているオブジェクト。  
  
#### <a name="tracking-points-and-tracking-spans"></a>追跡ポイントと追跡範囲  
 <xref:Microsoft.VisualStudio.Text.ITrackingPoint>テキスト バッファー内の文字位置を表します。 シフトする文字の位置を原因となる方法でバッファーを編集すると、追跡ポイントはそれに移動します。 たとえば、追跡ポイントは、バッファー内の位置 10 を参照すると、バッファーの先頭に 5 つの文字が挿入されます、追跡ポイントは、15 の位置を参照します。 によってその動作が決まりますが正確に追跡ポイントによって示される位置に挿入する場合は、その<xref:Microsoft.VisualStudio.Text.PointTrackingMode>、いずれかをされる`Positive`または`Negative`。 追跡モードが正の値であり、追跡ポイントが; カーソルの最後になっていますが、同じ文字を指す場合追跡モードが負の場合、追跡ポイントは、元の位置に挿入された最初の文字を指します。 追跡ポイントで表される位置にある文字が削除された場合、追跡ポイントは削除された範囲に続く最初の文字に移動します。 たとえば、追跡ポイントとは、位置、5 文字、3 ~ 6 の位置にある文字が削除された場合は、追跡ポイントは、3 の位置にある文字を指します。  
  
 <xref:Microsoft.VisualStudio.Text.ITrackingSpan>位置を 1 つだけではなく文字の範囲を表します。 その動作によって決定されます、<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>します。 Span 追跡モードの場合<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>、追跡の範囲の拡大を span 追跡モードの場合、そのエッジに挿入されたテキストを組み込む<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>追跡の範囲は、エッジで挿入したテキストを組み込んでいません。 ただし、span 追跡モードの場合<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>、挿入、先頭方向への現在の位置をプッシュする場合に、span 追跡モード<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>、挿入が末尾に向かって現在の位置をプッシュします。  
  
 所属するテキスト バッファーのすべてのスナップショットは、追跡ポイントの位置、または追跡スパンのスパンを取得できます。 追跡ポイントと追跡範囲は、任意のスレッドから安全に参照できます。  
  
#### <a name="content-types"></a>コンテンツの種類  
 コンテンツの種類は、異なる種類のコンテンツを定義するためのメカニズムです。 コンテンツの種類には、"text"、"code"または「バイナリ」などのファイルの種類または"xml"、"vb"または"c#"などのテクノロジの種類を指定できます。 たとえば、単語"using"は、他のプログラミング言語ではなく c# と Visual Basic の両方でのキーワードです。 そのため、このキーワードの定義は"c#"や"vb"コンテンツの種類に制限されます。  
  
 コンテンツの種類は、表示要素と、エディターの他の要素のフィルターとして使用されます。 多くのエディターの機能と拡張機能ポイントは、コンテンツの種類ごとに定義されます。たとえば、テキストの色はプレーン テキスト ファイル、XML ファイル、および Visual Basic ソース コード ファイルのさまざまなです。 テキスト バッファーが作成されると、テキスト バッファーのコンテンツの種類を変更するときに、一般にコンテンツの種類を割り当てられています。  
  
 コンテンツの種類複数-継承できる他のコンテンツ タイプ。 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>特定のコンテンツ タイプの親として複数の基本型を指定することができます。  
  
 開発者が独自のコンテンツの種類を定義およびそれらを使用して、登録、<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>します。 使用して、特定のコンテンツの種類に関してエディター多くの機能を定義できます、<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>します。 たとえば、エディターの余白、表示要素、およびマウス ハンドラーは特定のコンテンツ タイプを表示する編集者にのみ適用されるようにします。  
  
###  <a name="the-text-view"></a>テキスト ビュー  
 モデル ビュー コント ローラー (MVC) パターンのビューの一部では、ビュー、カーソル、スクロール バーなどのグラフィック要素の書式設定、テキスト ビューを定義します。 Visual Studio エディターのすべてのプレゼンテーション要素は、WPF に基づいています。  
  
#### <a name="text-views"></a>テキスト ビュー  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>インターフェイスはプラットフォームに依存しないテキスト ビューを表したものです。 ウィンドウで、テキスト ドキュメントを表示するには、主が使用されますが、そのこともできます、他の目的など、ツールヒントに。  
  
 テキスト ビューでは、さまざまな種類のテキスト バッファーを参照します。 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A>プロパティを参照、<xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel>これら 3 つの異なるテキスト バッファーを指すオブジェクトこれは、次のように最上位データ レベル バッファー編集バッファー、編集が発生し、visual バッファー、バッファーは、データ バッファー。テキスト ビューに表示されます。  
  
 テキストは、基になるテキスト バッファーに関連付けられている分類子に基づいて書式設定され、テキスト ビュー自体に関連付けられている表示要素のプロバイダーを使用してが設定されています。  
  
#### <a name="the-text-view-coordinate-system"></a>テキスト ビューの座標系  
 テキスト ビューの座標システムでは、テキスト ビュー内の位置を指定します。 この座標系では、x 値 0.0 表示されているテキストの左端に対応し、y 値 0.0 は表示されているテキストの上端に対応します。 左から右、x 座標が増加し、y 座標が上から下に増加します。  
  
 ビューポート (テキスト ウィンドウに表示されるテキストの一部) ことはできません、同様に水平スクロール、垂直方向にスクロールします。 描画サーフェイスに対して移動するように、左の座標を変更することで、ビューポートに水平方向にスクロールされます。 これにより、レンダリングされたテキストを変更することだけで、ビューポートを縦方向にスクロールするただし、<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>イベントが発生します。  
  
 距離の座標システムでは、論理ピクセルに対応します。 場合は、テキスト レンダリング サーフェイス倍率変換が非表示、テキスト レンダリングの座標システムで 1 つの単位はディスプレイ上の 1 つのピクセルに対応します。  
  
#### <a name="margins"></a>余白  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin>インターフェイスの余白を表し、余白、およびサイズの可視性の制御を有効します。 "Top"、"Left"、"Right"および"Bottom"という名前があり、top、bottom、left、またはビューの右端に関連付けられている定義済み余白、4 つがあります。 これらの余白は、その他の余白を配置できるコンテナーです。 インターフェイスは、余白のサイズと余白の可視性を返すメソッドを定義します。 余白は、アタッチ先のテキスト ビューに関する追加情報を提供するビジュアル要素です。 たとえば、行番号の余白には、テキスト ビューの行番号が表示されます。 グリフの余白には、UI 要素が表示されます。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>インターフェイスの作成と余白の配置を処理します。 余白は、その他の余白に関して注文できます。 優先順位の高い余白は、テキスト ビューに近い場所に配置します。 たとえばは、2 つの左余白、余白、および余白 B、B の余白に余白 A よりも優先順位の低い場合は、余白 B は余白 A. の左側に表示されます。  
  
#### <a name="the-text-view-host"></a>テキスト ビューのホスト  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>インターフェイスには、テキスト ビューとビュー、スクロール バーなどに付随するすべての隣接する装飾が含まれています。 テキスト ビューのホストには、ビューの枠線にアタッチされている余白も含まれています。  
  
#### <a name="formatted-text"></a>書式付きテキスト  
 テキスト ビューに表示されるテキストから成るは<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>オブジェクト。 すべての行のテキスト表示では、1 つの行のテキスト ビューでのテキストに対応します。 基になるテキスト バッファー内で長い行が部分的に (テキストの折り返しが有効でない) 場合に隠されてかテキスト ビューの複数の行に分割します。 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>インターフェイスにはメソッドと座標と、文字間のマッピングと行に関連付けられている可能性のある表示要素のプロパティが含まれています。  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> オブジェクトを使用して作成された、<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>インターフェイス。 ビューに現在表示されているテキストに関するだけに懸念がある場合は、書式設定のソースを無視できます。 テキストの形式で関心がある場合 (たとえば、リッチ テキストの切り取りをサポートして貼り付ける)、ビューに表示されることができますを使用する<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>テキスト バッファー内のテキストの書式設定します。  
  
 1 つのテキスト ビュー形式<xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>一度にします。  
  
## <a name="editor-features"></a>エディターの機能  
 エディターの機能では、フィーチャーの定義とは別の実装できるように設計されています。 エディターには、これらの機能が含まれています。  
  
-   タグおよび分類子  
  
-   修飾  
  
-   射影  
  
-   アウトライン  
  
-   マウスとキー バインド  
  
-   操作およびプリミティブ  
  
-   IntelliSense  
  
### <a name="tags-and-classifiers"></a>タグおよび分類子  
 タグは、テキストの範囲に関連付けられているマーカーです。 提示できます、さまざまな方法で、テキストの色分け表示、下線、グラフィック、またはポップアップを使用しています。 分類子は、1 つの種類のタグです。  
  
 その他のタグは<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>のテキストが強調表示、<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>アウトラインと<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>のコンパイル エラー。  
  
#### <a name="classification-types"></a>分類の種類  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>インターフェイスは、テキストの抽象のカテゴリには、等価クラスを表します。 分類の種類複数-継承できるその他の分類の種類。 たとえば、プログラミング言語の分類があります「キーワード」、「コメント」および「識別子」、"code"から継承します。 「名詞」、「動詞」および「形容詞」、「自然言語」から継承される自然言語の分類の種類があります。  
  
#### <a name="classifications"></a>分類  
 分類は、テキストの範囲を通常、特定の分類の種類のインスタンスです。 A<xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan>分類を表すために使用します。 分類の範囲は、テキストの特定の期間を対象とし、このスパンのテキストは、特定の分類の種類のシステムに指示するラベルと考えることができます。  
  
#### <a name="classifiers"></a>分類子  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>は一連の分類のテキストに分割するメカニズムです。 分類器は、特定のコンテンツの種類に対して定義されているし、特定のテキスト バッファーのインスタンス化する必要があります。 クライアントを実装する必要があります<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>テキスト分類に参加します。  
  
#### <a name="classifier-aggregators"></a>分類器のアグリゲーター  
 分類器アグリゲーターは、分類の 1 つのセットに 1 つのテキスト バッファーのすべての分類器を結合するメカニズムです。 たとえば、c# の分類器と英語の分類子の両方は、c# ファイルにコメントを分類を作成できます。 このコメントを考慮してください。  
  
```  
// This method produces a classifier  
```  
  
 コメントとして範囲全体にラベルを付ける可能性があります (C#) の分類子と英語分類器が「生成」として分類「動詞」と「名詞」として「メソッド」。 アグリゲーターの分類の重複のセットを生成して、セットの種類すべての投稿に基づいています。  
  
 テキストを一連の分類のためにも、分類器アグリゲーターにより、分類子は。 分類器アグリゲーターは、重複する分類がないことと、分類が並べ替えられることも確認します。 個々 の分類子は、任意の順序で分類の任意のセットを返すこと、および任意の方法で重複します。  
  
#### <a name="classification-formatting-and-text-coloring"></a>分類の書式設定とテキストの色分け  
 テキストの書式設定は、テキスト分類に基づいて構築されている機能の例です。 アプリケーション内のテキストの表示を決定する、テキスト表示の層で使用されます。 テキストの書式設定領域は、WPF によって異なりますが、分類の論理の定義ではありません。  
  
 分類形式には、特定の分類の種類のプロパティを書式設定のセットです。 これらの形式は、親分類の種類の形式から継承します。  
  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>は分類の種類からテキストを書式設定プロパティのセットへのマップ。 エディターで書式設定のマップの実装では、分類の形式のすべてのエクスポートを処理します。  
  
###   <a name="adornments"></a>修飾  
 修飾は、フォントとテキスト ビュー内の文字の色に直接関連しないグラフィック効果です。 たとえば、多くのプログラミング言語でのコンパイルされていないコードをマークするために使用する赤い波線の下線は、埋め込みの表示要素と、ツール ヒントがポップアップ表示要素。 派生修飾<xref:System.Windows.UIElement>実装と<xref:Microsoft.VisualStudio.Text.Tagging.ITag>。 タグの表示要素の 2 つの特殊な型は、 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>、ビューでは、テキストとして同じ領域の表示要素の<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>波線の下線の。  
  
 埋め込みの表示要素は、書式設定されたテキスト ビューの一部を形成するグラフィックスです。 これらは、Z オーダーの異なる層で構成されます。 次のように 3 つの組み込みのレイヤーがある: テキスト、カレット、および選択します。 ただし、開発者はレイヤーを定義し、互いの順序で配置できます。 埋め込みの表示要素の 3 種類がテキストの相対表示要素 (これは、テキストが移動したときの移動とは、テキストが削除されたときに削除)、ビューの相対修飾 (これは、ビューのテキスト以外の部分に必要)、および所有者によって制御された表示要素 (、開発する必要がありますの管理 の配置)。  
  
 ポップアップの表示要素は、ツールヒントなどのテキスト ビュー上の小さいウィンドウに表示されるグラフィックスです。  
  
###  <a name="projection"></a> 射影  
 プロジェクションは、別の種類のテキストを実際には保存されませんが、他のテキスト バッファーからのテキストを代わりに組み合わされているテキスト バッファーを構築するための手法です。 たとえばを他の 2 つのバッファーからテキストを連結し、1 つのバッファー内にある場合、結果を表示、または 1 つのバッファー内のテキストの部分を非表示には、投影のバッファーを使用できます。 投影のバッファーは、ソース バッファーを別の投影バッファーとして機能できます。 さまざまな方法でテキストを並べ替えるには、プロジェクションによって関連付けられたバッファーのセットを構築できます。 (このようなセットとも呼ばれますが、*バッファー グラフ*)。Visual Studio のテキストのアウトライン機能は、折りたたまれたテキストを非表示にするプロジェクション バッファーを使用して実装され、ASP.NET ページの Visual Studio エディターでは、プロジェクションを使用して、Visual Basic や c# などの埋め込みの言語をサポートします。  
  
 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>を使用して作成されて<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>します。 投影のバッファーが、順序付けられたシーケンスによって表される<xref:Microsoft.VisualStudio.Text.ITrackingSpan>オブジェクトと呼ばれる*ソース スパン*します。 これらの範囲の内容は、一連の文字として表示されます。 ソース範囲の描画元となるテキスト バッファーの名前は*ソース バッファー*します。 投影のバッファーのクライアントを通常のテキスト バッファーとは異なることに注意してくださいに必要はありません。  
  
 投影のバッファーは、ソース バッファーでテキスト変更イベントをリッスンします。 ソース内のテキスト間隔を変更するときに投影バッファーは、独自の座標に変更されたテキストの座標をマップし、適切なテキスト変更イベントを発生させます。 たとえば、これらの内容を含むソース バッファー A と B があるとします。  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 投影バッファー P がもう 1 つを持つすべてのバッファーをすべてのバッファー、B が、2 つのテキスト範囲から形成される場合は、次の内容が P:  
  
```  
P: ABCDEvwxyz  
```  
  
 場合、部分文字列`xy`バッファー P は、7 および 8 の位置にある文字が削除されたことを示すイベントを発生させます。 その後、B、バッファーから削除されます。  
  
 投影バッファーが直接編集することもできます。 適切なソース バッファーするために編集を伝達します。 たとえば、6 ("v"文字の元の位置) の位置にある P をバッファーに文字列が挿入される場合、挿入が位置 1 で B をバッファーに反映されます。  
  
 投影のバッファーに影響を与えるソース範囲の制限があります。 ソース範囲が重複しない可能性があります。投影バッファー内の場所は、ソース バッファーには、複数の場所にマップできませんし、元のバッファー内の場所は、投影バッファー内の 1 つ以上の場所にマップできません。 ソース バッファーのリレーションシップで circularities が許可されていません。  
  
 ソースのセットをバッファーのプロジェクション バッファーの変更を使用して、一連のソースにわたる変更イベントが発生します。  
  
 省略バッファーは、投影バッファーの特別な種類です。 アウトライン表示および操作を展開したり折りたたんだりテキストのブロックに主に使用されます。 省略バッファーは 1 つのソース バッファーに基づいており、省略バッファー内の範囲する必要があります同じ順序になるように、元のバッファーに順序付けされています。  
  
#### <a name="the-buffer-graph"></a>バッファーのグラフ  
 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>インターフェイス、グラフの投影バッファー間でマッピングを有効にします。 すべてのテキスト バッファーと投影バッファーは、言語コンパイラによって生成される抽象構文ツリーと同様の有向非巡回グラフで収集されます。 グラフは、最上位のバッファーは、任意のテキスト バッファーは、によって定義されます。 バッファーのグラフには、元のバッファー内のポイントには上位バッファー内のポイントから、またはソース バッファー内の範囲のセットには上位バッファー内の範囲からをマップできます。 同様に、マップのポイントまたは最上位のバッファー内のポイントから元のバッファーにまたがることできます。 バッファーのグラフを使用して作成、<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>します。  
  
#### <a name="events-and-projection-buffers"></a>イベントと投影バッファー  
 投影バッファーが変更されたときに、変更が依存しているバッファーに投影バッファーから送信されます。 すべてのバッファーを変更した後以降、最下位のバッファーでバッファーの変更イベントが発生します。  
  
###  <a name="outlining"></a> アウトライン表示  
 アウトラインを展開または折りたたむテキスト ビュー内のテキストのブロックをさまざまな機能があります。 アウトライン表示は、種類として定義の<xref:Microsoft.VisualStudio.Text.Tagging.ITag>、表示要素が定義されていると同じにします。 A<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>展開または折りたたむテキスト領域を定義するタグします。 インポートする必要がありますのアウトラインを使用する、<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>を取得する、<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>します。 アウトラインのマネージャーを列挙、縮小、およびとして表現される別のブロックを展開する<xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible>オブジェクトし、それに応じてイベントを発生させます。  
  
###  <a name="mousebindings"></a> マウスのバインド  
 マウスのバインドは、別のコマンドにマウスの動きをリンクします。 使用してマウス バインディングが定義されている、<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>を使用してキー バインドが定義されていると、<xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>します。 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>自動的にすべてのバインディングをインスタンス化して、ビュー内でマウス イベントに接続します。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor>インターフェイスには、別のマウス イベントの前処理と後処理のイベント ハンドラーが含まれています。 イベントのいずれかのハンドルをいくつかのメソッドのオーバーライドできます<xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>します。  
  
###  <a name="editoroperations"></a> エディターの操作  
 エディター操作は、自動化スクリプトを実行して、エディター、またはその他の目的とのやり取りに使用できます。 インポートすることができます、<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>でアクセス操作を指定された<xref:Microsoft.VisualStudio.Text.Editor.ITextView>します。 選択範囲の変更、ビューをスクロールまたはビューのさまざまな部分へカレットを移動し、これらのオブジェクトを使用できます。  
  
###  <a name="intellisense"></a> IntelliSense  
 IntelliSense は、ステートメント入力候補、シグネチャ ヘルプ (パラメーターの情報とも呼ばれます)、クイック ヒント、および電球をサポートしています。  
  
 ステートメント入力候補は、メソッド名、XML 要素、およびその他のコードまたはマークアップ要素の潜在的な入力候補のポップアップ リストを提供します。 一般に、ユーザー ジェスチャには、完了セッションが起動します。 セッション、潜在的な入力候補の一覧を表示して、ユーザーが 1 つを選択または一覧を消すことができます。 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>を作成して、トリガーする責任を負いますが、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>します。 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>計算、<xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet>のセッションの項目を完了します。  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)   
 [エディターのインポート](../extensibility/editor-imports.md)
