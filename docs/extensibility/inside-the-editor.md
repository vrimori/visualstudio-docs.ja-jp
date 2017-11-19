---
title: "エディター内 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
caps.latest.revision: "31"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1876f334ad1b444b464ecc420767dea90baed6b3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="inside-the-editor"></a>エディター内
エディターでは、テキスト ビューと、ユーザー インターフェイスからエディター モデル別のテキストを保持するように設計されている複数のサブシステムの数で構成されます。  
  
 これらのセクションでは、エディターのさまざまな側面について説明します。  
  
-   [サブシステムの概要](../extensibility/inside-the-editor.md#overview)  
  
-   [テキスト モデル](../extensibility/inside-the-editor.md#textmodel)  
  
-   [テキスト ビュー](../extensibility/inside-the-editor.md#textview)  
  
 これらのセクションでは、エディターの機能について説明します。  
  
-   [タグおよび分類子](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
-   [修飾](../extensibility/inside-the-editor.md#adornments)  
  
-   [プロジェクション](../extensibility/inside-the-editor.md#projection)  
  
-   [アウトライン](../extensibility/inside-the-editor.md#outlining)  
  
-   [マウスのバインド](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [エディターの操作](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a>サブシステムの概要  
  
### <a name="text-model-subsystem"></a>テキスト モデル サブシステム  
 テキスト モデル サブシステムは、テキストを表すと、その操作の有効化します。 テキスト モデル サブシステムを含む、<xref:Microsoft.VisualStudio.Text.ITextBuffer>インターフェイスで、エディターによって表示される文字のシーケンスについて説明します。 このテキストを修正して、追跡して、それ以外の場合さまざまな方法で操作します。 テキスト モデルには、次の側面の型も提供されます。  
  
-   テキストと関連付けて、ファイルとそれらの読み書き、ファイル システムを管理するサービス。  
  
-   オブジェクトの 2 つのシーケンスの最小の違いを検出する差分サービス。  
  
-   他のバッファー内のテキストのサブセットの観点から、バッファー内のテキストを記述するためのシステムです。  
  
 テキスト モデル サブシステムはユーザー インターフェイス (UI) の概念です。 たとえばはテキスト形式またはテキストのレイアウトを担当して、テキストと共に関連付けられている可能性のあるビジュアル表示要素の情報を持たない。  
  
 テキスト モデル サブシステムのパブリック型は、.NET Framework の基本クラス ライブラリおよび Managed Extensibility Framework (MEF) にのみ依存 Microsoft.VisualStudio.Text.Data.dll と Microsoft.VisualStudio.CoreUtilitiy.dll に格納されます。  
  
### <a name="text-view-subsystem"></a>テキスト ビュー サブシステム  
 テキスト ビュー サブシステムは書式設定と、テキストを表示します。 このサブシステム内の型は、種類が Windows Presentation Foundation (WPF) を使用するかどうかに応じて、2 つのレイヤーに分かれています。 最も重要な型は<xref:Microsoft.VisualStudio.Text.Editor.ITextView>と<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>を表示するテキスト行のセットとも、カレット、選択、および WPF UI 要素を使用して、テキストを装飾するための機能を制御します。 このサブシステムでは、テキストの周囲のマージン領域の表示も用意されています。 これらの余白は、拡張して、さまざまな種類のコンテンツや視覚的効果を含めることができます。 余白の例は、行番号表示やスクロール バーです。  
  
 Microsoft.VisualStudio.Text.UI.dll と Microsoft.VisualStudio.Text.UI.Wpf.dll には、テキスト ビュー サブシステムのパブリック型が含まれます。 最初のアセンブリには、プラットフォームに依存しない要素が含まれているし、2 つ目には、WPF 固有の要素が含まれています。  
  
### <a name="classification-subsystem"></a>分類サブシステム  
 分類サブシステムは、テキストのフォント プロパティを決定します。 分類器は、「キーワード」、「コメント」など、別のクラスにテキストを分割します。 分類形式のマップに関連してこれらのクラス実際のフォント プロパティをたとえば、"Blue Consolas 10 pt"です。 この情報は、書式を設定し、テキストの表示テキスト ビューで使用されます。 タグ付け、このトピックの後半で詳しくに記載されているテキストの範囲に関連するデータを有効にします。  
  
 分類サブシステムのパブリック型は Microsoft.VisualStudio.Text.Logic.dll に含まれ、Microsoft.VisualStudio.Text.UI.Wpf.dll に含まれている分類を視覚的な側面とやり取りを行います。  
  
### <a name="operations-subsystem"></a>操作のサブシステム  
 操作のサブシステムでは、エディターの動作を定義します。 Visual Studio エディター コマンドの実装と、元に戻すシステムを提供します。  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>テキスト モデルとテキスト ビューについて詳しく見て  
  
###  <a name="textmodel"></a>テキスト モデル  
 テキスト モデル サブシステムは、テキスト型のさまざまなグループで構成されます。 テキスト バッファーには、テキストのスナップショットには、テキスト範囲が含まれます。  
  
#### <a name="text-buffers-and-text-snapshots"></a>テキスト バッファーとテキスト スナップショット  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer>インターフェイスは、これは、エンコードで使用される utf-16 を使用してエンコードされた Unicode 文字のシーケンスを表す、 `String` .NET Framework の型。 テキスト バッファーをファイル システムのドキュメントとして永続化できますが、これは必須ではありません。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>が空のテキスト バッファーまたは文字列から、またはからに初期化されるテキスト バッファーを作成するために使用<xref:System.IO.TextReader>です。 テキスト バッファーとしてファイル システムに永続化できる、<xref:Microsoft.VisualStudio.Text.ITextDocument>です。  
  
 テキスト バッファーは、スレッドは、呼び出すことによってテキスト バッファーの所有権を取得するまでの任意のスレッドが編集できる<xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>です。 その後、そのスレッドのみが編集を実行できます。  
  
 テキスト バッファーは、その有効期間中に、多くのバージョンで移動できます。 新しいバージョンは、バッファーを編集するたびに、変更できない、生成<xref:Microsoft.VisualStudio.Text.ITextSnapshot>バッファーのバージョンの内容を表します。 テキストのスナップショットは変更できないためが表すテキスト バッファーが変化し続ける場合でも、制限なく、任意のスレッドでテキスト スナップショットにアクセスすることができます。  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>テキストのスナップショットとスナップショットの行数  
 文字のシーケンス、または行のシーケンスとしては、テキストのスナップショットの内容を表示できます。 文字と行は、0 から始まるインデックス両方がします。 空のテキストのスナップショットには、ゼロの文字と 1 つの空の行が含まれています。 行は、有効な Unicode 改行文字シーケンスによって、または先頭またはバッファーの末尾で区切られます。 改行文字がテキスト スナップショットで明示的に表現し、テキスト スナップショット内の改行はすべて同じであるがします。  
  
> [!NOTE]
>  Visual Studio エディターでの改行文字の詳細については、次を参照してください。[エンコーディングと改行](../ide/encodings-and-line-breaks.md)です。  
  
 テキストの行として表されます、<xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>オブジェクトで、特定の行番号または特定の文字位置のテキスト スナップショットから取得できます。  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints、SnapshotSpans、および NormalizedSnapshotSpanCollections  
 A<xref:Microsoft.VisualStudio.Text.SnapshotPoint>スナップショット内の文字位置を表します。 位置が 0 と、スナップショットの長さの間に保証されます。 A<xref:Microsoft.VisualStudio.Text.SnapshotSpan>スナップショット内のテキストの範囲を表します。 0 と、スナップショットの長さの間には、終了位置が保証されます。 <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>のセットから成る<xref:Microsoft.VisualStudio.Text.SnapshotSpan>同じスナップショットからのオブジェクト。  
  
#### <a name="spans-and-normalizedspancollections"></a>スパンと NormalizedSpanCollections  
 A<xref:Microsoft.VisualStudio.Text.Span>テキスト スナップショット内のテキストの範囲に適用できる期間を表します。 スナップショットの位置は、範囲は 0 を含む任意の位置に起動できるように、0 から始まる。 `End`範囲のプロパティがの合計に等しいその`Start`プロパティとその`Length`プロパティです。 A`Span`によってインデックスが設定された文字を含まない、`End`プロパティです。 開始する間隔など、= 5 と長さ = 3 はエンド = 8、5、6、および 7 の位置にある文字が含まれているとします。 このスパンの表記法は 5..8) です。  
  
 2 つの範囲は、位置がある、共通の終了位置を含む場合と交差します。 交差部分ではそのため、[3, 5) と [2, 7) は [3, 5) との積集合 [3, 5) と [5, 7) が [5, 5)。 (ことに注意して [5, 5) は、空のスパン)。  
  
 終了位置を除く位置が共通である場合、2 つの範囲が重複します。 空のスパンには、他の範囲、決してが重複していますされ、2 つの範囲の重なりが空ではありません。  
  
 A<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>範囲の開始プロパティの順序での範囲の一覧を示します。 一覧で、重複または隣接する範囲がマージされます。 たとえば、範囲のセットが与えられて [5..9)、[0..1)、[3..6)、および [9..10)、範囲の正規化されたリストは [0..1)、[3..10) です。  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit、TextVersion およびテキストの変更通知  
 使用してテキスト バッファーの内容を変更することができます、<xref:Microsoft.VisualStudio.Text.ITextEdit>オブジェクト。 このようなオブジェクトを作成する (のいずれかを使用して、`CreateEdit()`メソッドの<xref:Microsoft.VisualStudio.Text.ITextBuffer>) テキスト編集ので構成されるテキストのトランザクションを開始します。 すべての編集は、文字列バッファー内のテキストの一部の範囲の置換です。 座標とすべての編集の内容は、トランザクションが開始されたとき、バッファーのスナップショットの基準とした表されます。 <xref:Microsoft.VisualStudio.Text.ITextEdit>オブジェクトが同じトランザクションに他の編集によって影響を受ける編集の座標を調整します。  
  
 たとえば、この文字列を含むテキスト バッファーを考慮してください。  
  
```  
abcdefghij  
```  
  
 2 つの編集、ある範囲を置換する 1 つの編集を含むトランザクションを適用 [2..4) 文字を使用して`X`にスパンを置換する 2 番目の編集と [6..9) 文字を使用して`Y`です。 結果は、このバッファーです。  
  
```  
abXefYj  
```  
  
 2 番目の編集の座標は、最初の編集が適用される前に、トランザクションの先頭にバッファーの内容に対して計算されました。  
  
 バッファーに変更が反映ときに、<xref:Microsoft.VisualStudio.Text.ITextEdit>オブジェクトは、呼び出すことでコミットがその`Apply()`メソッドです。 少なくとも 1 つの空でない編集があった場合、新しい<xref:Microsoft.VisualStudio.Text.ITextVersion>が作成されて、新しい<xref:Microsoft.VisualStudio.Text.ITextSnapshot>作成されると、1 つ`Changed`イベントが発生します。 すべてのバージョンはテキストが、異なるテキスト スナップショット。 テキスト スナップショットが編集トランザクションを後のテキスト バッファーのすべての状態を表しますが、テキスト バージョンごとに 1 つのスナップショットから変更のみを説明します。 一般に、テキスト スナップショットでは、1 回使用するものであり、維持したままテキスト バージョン必要がありますアライブしばらくの間、破棄します。  
  
 テキストのバージョンが含まれています、<xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>です。 このコレクションの変更について説明する、スナップショットを適用するときにその後のスナップショットを生成します。 各<xref:Microsoft.VisualStudio.Text.ITextChange>コレクション内で、変更、置き換えられた文字列、および置換文字列の文字位置が含まれています。 置き換えられた文字列が空の基本的な挿入、および置換文字列が空の基本的な削除します。 正規化されたコレクションは常に`null`テキスト バッファーの最新バージョンについてはします。  
  
 1 つだけ<xref:Microsoft.VisualStudio.Text.ITextEdit>オブジェクトはテキスト バッファーをいつでもインスタンス化することができ、すべてのテキスト編集は、(所有権を要求すると) 場合は、テキスト バッファーを所有しているスレッドで実行する必要があります。 テキストの編集を呼び出すことによって破棄することができます、`Cancel`メソッドまたはその`Dispose`メソッドです。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer>用意されています`Insert()`、 `Delete()`、および`Replace()`のようにメソッドがで検出された、<xref:Microsoft.VisualStudio.Text.ITextEdit>インターフェイスです。 これらの呼び出しを作成すると同じ効果を持つ、<xref:Microsoft.VisualStudio.Text.ITextEdit>オブジェクトはのような呼び出しを実行し、編集を適用します。  
  
#### <a name="tracking-points-and-tracking-spans"></a>追跡ポイントと範囲の追跡  
 <xref:Microsoft.VisualStudio.Text.ITrackingPoint>テキスト バッファー内の文字位置を表します。 シフトする文字の位置を原因となる方法でバッファーを編集すると場合、追跡ポイントは、それに移動します。 たとえば、追跡ポイントが 10、バッファー内の位置を指す、5 つの文字が、バッファーの先頭に挿入された場合は、追跡ポイントは、15 の位置を参照します。 その動作が決まります正確に追跡ポイントで示される位置にある、挿入する場合は、その<xref:Microsoft.VisualStudio.Text.PointTrackingMode>、いずれかのできる`Positive`または`Negative`です。 追跡ポイントを指すようになりましたが、挿入対象であるの最後に、同じ文字追跡モードが正の場合は、追跡モードが負の場合、追跡ポイントは元の位置に挿入された最初の文字を指します。 追跡ポイントで表される位置にある文字が削除された場合、追跡ポイントは、削除の範囲に続く最初の文字に移動します。 たとえば、追跡ポイントが、5 番目の位置にある文字を指す 3 ~ 6 の位置にある文字が削除された場合、追跡ポイントは 3 の位置にある文字を参照します。  
  
 <xref:Microsoft.VisualStudio.Text.ITrackingSpan>位置を 1 つだけではなく文字の範囲を表します。 その動作によって決定されます、<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>です。 Span 追跡モードの場合<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>、span 追跡モードの場合は、端; で挿入したテキストを組み込むに拡大され、追跡範囲<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>追跡の範囲は、エッジで挿入したテキストを組み込んでいません。 ただし、span 追跡モードの場合<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>、挿入の開始に向かって現在の位置をプッシュする場合は span 追跡モード<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>挿入が終了に向けて、現在の位置をプッシュします。  
  
 所属するテキスト バッファーの任意のスナップショットの追跡ポイントの位置、または追跡スパンのスパンを取得できます。 追跡ポイントと追跡範囲は、任意のスレッドからは安全に参照する場合があります。  
  
#### <a name="content-types"></a>コンテンツの種類  
 コンテンツの種類は、異なる種類のコンテンツを定義するためのメカニズムです。 コンテンツの種類には、"text"、"code"、"binary"などのファイルの種類または"xml"、"vb"または"c#"などの技術の種類を指定できます。 たとえば、単語"using"は、c# および Visual Basic の両方ではなくに他のプログラミング言語のキーワードです。 そのため、このキーワードの定義は"c#"や"vb"コンテンツの種類に制限になります。  
  
 コンテンツの種類は、修飾とエディターの他の要素に対するフィルターとして使用されます。 多くのエディターの機能と拡張ポイントがコンテンツの種類ごとに定義されました。たとえば、テキストの色分けはプレーン テキスト ファイル、XML ファイル、および Visual Basic ソース コード ファイルの異なるです。 テキスト バッファーは一般に割り当てられているコンテンツの種類は、作成されると、バッファーにテキストのコンテンツの種類を変更することができます。  
  
 コンテンツの種類複数 - から継承できます他のコンテンツ タイプ。 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>特定のコンテンツ タイプの親として複数の基本型を指定することができます。  
  
 開発者が独自のコンテンツの種類を定義およびそれらを使用して、登録、<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>です。 エディターの機能の多くはに関して特定のコンテンツ タイプを使用して、<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>です。 たとえば、エディター余白、修飾、およびマウス ハンドラーは特定のコンテンツ タイプを表示するためのエディターにのみ適用されるようにします。  
  
###  <a name="textview"></a>テキスト ビュー  
 モデル ビュー コント ローラー (MVC) パターンのビューの一部では、ビュー、スクロール バーやカーソルなどのグラフィック要素の書式、テキスト ビューを定義します。 Visual Studio エディターのすべてのプレゼンテーション要素は、WPF に基づいています。  
  
#### <a name="text-views"></a>テキスト ビュー  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>インターフェイスは、テキスト ビューのプラットフォームに依存しない形式です。 ウィンドウでテキスト ドキュメントを表示するには、主に使用します、ことがでく使用しても他の目的で、たとえば、ツールヒントにします。  
  
 テキスト ビューでは、さまざまな種類のテキスト バッファーを参照します。 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A>プロパティを指す、<xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel>これら 3 つの異なるテキスト バッファーを指すオブジェクトを: データ バッファーの最上位のデータ レベル バッファーの編集が実行され、これをバッファーにはビジュアルのバッファー内の編集バッファーテキスト ビューに表示されます。  
  
 テキストは、基になるテキスト バッファーに関連付けられている分類子に基づいて書式設定し、テキスト ビュー自体に関連付けられている表示要素のプロバイダーを使用した装飾します。  
  
#### <a name="the-text-view-coordinate-system"></a>テキスト ビュー座標系  
 テキスト ビュー座標系では、テキスト ビュー内の位置を指定します。 この座標系の x 値 0.0 が表示されているテキストの左端に対応し、y 値 0.0 が表示されているテキストの上端に対応しています。X 座標が左から右に増加し、y 座標が上から下に増加します。  
  
 ビューポート (テキスト ウィンドウに表示されているテキストの一部) ことはできません、同様に水平にスクロールする垂直方向にスクロールして、します。 描画サーフェイスに関して移動するように、左座標を変更することで、ビューポートが水平にスクロールします。 ただしなど、これにより、レンダリングされたテキストを変更することによってのみを使用して、ビューポートを垂直方向にスクロールできる、<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>イベントが発生します。  
  
 距離の座標システムでは、論理ピクセルに対応します。 テキストの表示サーフェイスが変換をスケーリングせず表示されている場合、テキストのレンダリング座標系内で 1 つの単位はディスプレイ上の 1 つのピクセルに対応します。  
  
#### <a name="margins"></a>余白  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin>インターフェイスにある余白を表すし、余白、およびサイズの可視性の制御を有効にします。 "Top"、「左」、「右」および"Bottom"という名前は、top、bottom、left、またはビューの右のエッジに関連付けられている 4 つ定義済みの余白があります。 これらの余白は、その他の余白を配置できるコンテナーです。 インターフェイスは、余白のサイズと余白の可視性を返すメソッドを定義します。 余白がアタッチされているテキスト ビューに関する追加情報を提供するビジュアル要素です。 たとえば、行番号のマージンには、テキスト ビューの行番号が表示されます。 グリフ余白は、UI 要素を表示します。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>インターフェイスの作成と余白の配置を処理します。 余白の順序に関するその他の余白を指定できます。 優先順位の高い余白は、近いテキスト ビューにあります。 たとえば、2 つの左余白、余白 A および B の余白がある余白 B は A の余白よりも優先順位が低い場合は、余白 B は余白 A. の左側に表示されます。  
  
#### <a name="the-text-view-host"></a>テキスト ビューのホスト  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>インターフェイスには、テキスト ビューと、ビューでは、たとえば、スクロール バーに付随するすべての隣接する装飾が含まれています。 テキスト ビューのホストには、ビューの境界線にアタッチされている余白も含まれています。  
  
#### <a name="formatted-text"></a>書式設定テキスト  
 テキスト ビューに表示されるテキストから成るは<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>オブジェクト。 テキスト ビューのすべての行は、1 つの行のテキスト ビューでのテキストに対応します。 長い行のテキスト バッファーを基になるか、部分的に (テキストの折り返しが有効にしない) 場合に隠されてしたりテキスト ビューの複数の行に分割します。 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>インターフェイスには、メソッドとプロパティの座標と、文字間のマッピングと、行を関連付けることができますの表示要素が含まれています。  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>オブジェクトを使用して作成される、<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>インターフェイスです。 だけが懸念されるビューで現在表示されているテキストを書式設定のソースを無視できます。 テキストの書式に関心がある場合 (たとえば、サポートしてリッチ テキストの切り取りと貼り付けを)、ビューに表示されることができますを使用する<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>テキスト バッファーにテキストを書式設定します。  
  
 いずれかのテキスト ビュー形式<xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>一度にです。  
  
## <a name="editor-features"></a>エディターの機能  
 エディターの機能では、機能の定義は、その実装を区別できるように設計されています。 エディターには、これらの機能が含まれています。  
  
-   タグおよび分類子  
  
-   修飾  
  
-   射影  
  
-   アウトライン  
  
-   マウスとキー バインディング  
  
-   操作とプリミティブ  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a>タグおよび分類子  
 タグは、テキストの範囲に関連付けられているマーカーです。 これらを提示する、さまざまな方法でなどのテキストの色指定、下線、グラフィック、またはポップアップを使用して、します。 分類子は、1 つの種類のタグです。  
  
 その他のタグは<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>のテキストが強調表示、<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>アウトラインと<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>のコンパイル エラー。  
  
#### <a name="classification-types"></a>分類の種類  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>インターフェイスは、これは抽象のカテゴリ文字列の等価クラスを表します。 分類の種類複数の型から継承できます他の分類します。 たとえば、プログラミング言語の分類があります「キーワード」、「コメント」および「識別子」、"code"から継承します。 「名詞」、「動詞」および「形容詞」、「自然言語」から継承される自然言語の分類の種類があります。  
  
#### <a name="classifications"></a>分類  
 分類は、テキストの範囲で通常、特定の分類の種類のインスタンスです。 A<xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan>分類を表すために使用します。 分類スパンは、テキストの特定の範囲をカバーし、このテキストの範囲は、特定の分類の種類のシステムに指示するラベルと考えることができます。  
  
#### <a name="classifiers"></a>分類子  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>は分類のセットにテキストを分割するための機構です。 分類子は、特定のコンテンツの種類に対して定義されているし、特定のテキスト バッファーのインスタンス化する必要があります。 クライアントを実装する必要があります<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>テキスト分類に含めるようにします。  
  
#### <a name="classifier-aggregators"></a>分類子アグリゲーター  
 分類子アグリゲーターは、分類の 1 つのセットに 1 つのテキスト バッファーのすべての分類器を結合するメカニズムです。 たとえば、c# 分類器と英語の言語の分類子の両方は、c# ファイル内のコメントを分類を作成できます。 このコメントを考慮してください。  
  
```  
// This method produces a classifier  
```  
  
 コメントとして範囲全体にラベルを付ける場合があります (C#) の分類子および英語分類器は、可能性があります分類「生成」、「動詞」および「名詞」として"method"として。 アグリゲーターが重複しない分類のセットを生成し、セットの種類は、すべてのコントリビューションに基づいています。  
  
 テキストを一連の分類のためにも、分類器アグリゲーターにより、分類器です。 分類子アグリゲーターは、重複する分類がないことと、分類が並べ替えられているにも保証されます。 個別の分類器は、任意の順序で分類の任意のセットを返すようにする任意の方法で重複します。  
  
#### <a name="classification-formatting-and-text-coloring"></a>分類の書式設定とテキストの色分け  
 テキストの書式設定は、テキスト分類に基づいて構築されている機能の例です。 アプリケーション内のテキストの表示を決定するテキスト ビューのレイヤーによって使用されます。 テキストの書式設定領域が、WPF に依存するには、論理の定義の分類のではありません。  
  
 分類の形式は、特定の分類の種類のプロパティを書式設定のセットです。 これらの形式は、親分類の種類の形式から継承します。  
  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>テキストの書式設定プロパティのセットに分類の種類をマップします。 エディターで形式のマップの実装では、分類の形式のすべてのエクスポートを処理します。  
  
###  <a name="adornments"></a>修飾  
 修飾は、フォントとテキスト ビュー内の文字の色に直接関連していないグラフィックの効果です。 たとえば、多くのプログラミング言語でのコンパイルからコードをマークするために使用に赤い波線の下線は、埋め込みの装飾、ツールヒント ポップアップの表示要素。 派生修飾<xref:System.Windows.UIElement>および実装<xref:Microsoft.VisualStudio.Text.Tagging.ITag>です。 装飾タグの 2 つの特殊な型は、 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>、ビューでは、テキストと同じ領域を占有する表示要素の<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>波線の下線のです。  
  
 埋め込み修飾は、書式付きテキスト ビューの一部を形成するグラフィックです。 これらは、Z オーダーの異なるレイヤーで構成されます。 次のように 3 つの組み込みレイヤーがある: テキスト、カレット、および選択します。 ただし、開発者はより多くのレイヤーを定義し、いずれかの別の順序で配置できます。 埋め込み表示要素の次の 3 つの種類は (これは、テキストが移動したときに移動されは、テキストが削除されたときに削除) テキストの相対修飾、ビューの相対表示 (ビューの非テキスト部分に関係があります) を要素、および所有者制御修飾 (開発者必要があります [管理] の配置) します。  
  
 ポップアップの表示要素は、テキスト ビュー、ツールヒントなどの上の小さいウィンドウに表示される画像です。  
  
###  <a name="projection"></a>プロジェクション  
 射影は、別の種類のテキストは実際には保存されませんが、代わりに他のテキスト バッファーからのテキストが結合されるテキスト バッファーを構築するための手法です。 たとえば、他の 2 つのバッファーからのテキストを連結し、1 つのバッファー内にある場合、結果を表示する、または 1 つのバッファー内のテキストの部分を非表示には、投影バッファーを使用できます。 投影バッファーは、ソース バッファーを別の投影バッファーとして機能できます。 さまざまな方法でテキストを並べ替えるには、一連の投影で関連付けられたバッファーを構築できます。 (このようなセットとも呼ばれます、*バッファー グラフ*)。折りたたまれているテキストを非表示に投影バッファーを使用して、Visual Studio テキストのアウトライン機能を実装し、ASP.NET ページの Visual Studio エディターでは、投影法を使用して、Visual Basic や c# などの埋め込みの言語をサポートします。  
  
 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>を使用して作成された<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>です。 投影バッファーがの順序付けられたシーケンスによって表される<xref:Microsoft.VisualStudio.Text.ITrackingSpan>として知られているオブジェクト*ソース スパン*です。 これらの範囲の内容は、文字のシーケンスとして表示されます。 ソース範囲の描画元となるテキスト バッファーが名前付き*ソース バッファー*です。 投影バッファーのクライアントを通常のテキスト バッファーとは異なることに注意する必要はありません。  
  
 投影バッファーは、ソース バッファーでテキスト変更イベントを待機します。 ソース内のテキスト間隔を変更するときに投影バッファーは、独自の座標に変更されたテキストの座標をマップし、適切なテキスト変更イベントを発生させます。 たとえば、これらのコンテンツを持つソース バッファー A と B があるとします。  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 投影バッファー P がもう 1 つを持つすべてのバッファーとは、すべてのバッファー、B の 2 つのテキスト範囲から形成される場合は、次のコンテンツが P:  
  
```  
P: ABCDEvwxyz  
```  
  
 場合、substring`xy`バッファー P を 7 と 8 の位置にある文字が削除されたことを示すイベントが発生し、B、バッファーから削除されます。  
  
 投影のバッファーを直接編集もできます。 適切なソース バッファーに対する編集内容を伝達します。 たとえば、文字列は、バッファー P 6 ("v"文字の元の位置) の位置に挿入されたが、挿入は位置 1 でバッファー B に反映されます。  
  
 プロジェクション バッファーに関与するソース範囲に制限があります。 ソース範囲が重複しない可能性があります。投影バッファー内の場所は、ソース バッファー内の 1 つ以上の場所にマップできないし、ソース バッファー内の場所は、投影バッファー内の 1 つ以上の場所にマップできません。 ソース バッファー リレーションシップで circularities が許可されていません。  
  
 ソースのセットをバッファーするプロジェクション バッファー変更し、一連のソースの変更にまたがっている場合と、イベントが発生します。  
  
 省略バッファーは、特別な種類の投影バッファーです。 アウトライン表示とテキストのブロック、閉じたりする操作については、主に使用されます。 省略バッファーは 1 つのソース バッファーに基づいており、elision バッファー内の範囲必要があります順序で指定する、同じソース バッファーの順序がします。  
  
##### <a name="the-buffer-graph"></a>バッファーのグラフ  
 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>インターフェイス投影バッファーのグラフ間でマッピングを有効にします。 すべてのテキスト バッファーおよびプロジェクション バッファーは、言語コンパイラによって生成される抽象構文ツリーと同様に、有向無閉路有向グラフに収集されます。 グラフは、最上位のバッファーは、任意のテキスト バッファーは、によって定義されます。 ソース バッファー内のポイントには上位バッファー内のポイントまたはソース バッファー内の範囲のセットには上位バッファー内の範囲から、バッファーのグラフをマップできます。 同様に、点をマップしたり、ソース バッファーから最上位のバッファー内のポイントにまたがることができます。 バッファーのグラフを使用して作成される、<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>です。  
  
##### <a name="events-and-projection-buffers"></a>イベントと投影バッファー  
 投影バッファーが変更されると、変更が依存しているバッファーに投影バッファーから送信されます。 すべてのバッファーが変更されると後、以降、最下位のバッファーでバッファーの変更イベントが発生します。  
  
###  <a name="outlining"></a>アウトライン表示  
 アウトライン表示を展開または折りたたむテキスト ビュー内のテキストのブロックをさまざまな機能です。 アウトライン表示は、種類として定義されての<xref:Microsoft.VisualStudio.Text.Tagging.ITag>の場合と同じ方法の表示要素が定義されます。 A<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>できますを展開または折りたたむテキスト領域を定義するタグがします。 インポートする必要があります、アウトライン表示を使用する、<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>を取得する、<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>です。 アウトラインのマネージャーを列挙、縮小、およびとして表される別のブロックを展開する<xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible>オブジェクトし、それに応じてイベントを発生させます。  
  
###  <a name="mousebindings"></a>マウスのバインド  
 マウスのバインディングは、別のコマンドにマウスの動きをリンクします。 使用してマウス バインディングが定義されている、<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>を使用してキー バインドが定義されていると、<xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>です。 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>自動的にすべてのバインディングをインスタンス化し、それらをビュー内でマウスのイベントに接続します。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor>インターフェイスには、別のマウス イベントの処理する前と処理後のイベント ハンドラーが含まれています。 イベントのいずれかのハンドルをいくつかのメソッドのオーバーライドできます<xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>です。  
  
###  <a name="editoroperations"></a>エディターの操作  
 スクリプトを実行して、エディター、またはその他の目的とのやり取りを自動化するエディターの操作を使用できます。 インポートすることができます、<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>をアクセス操作に、指定された<xref:Microsoft.VisualStudio.Text.Editor.ITextView>です。 これらのオブジェクトを使用して選択範囲の変更、スクロールして、ビューまたはビューのさまざまな部分へカレットを移動できます。  
  
###  <a name="intellisense"></a>IntelliSense  
 IntelliSense には、ステートメント入力候補、シグネチャ ヘルプ (パラメーターの情報とも呼ばれます)、クイック ヒント、および代わって電球がサポートしています。  
  
 ステートメント入力候補は、メソッド名、XML 要素、およびその他のコードまたはマークアップ要素の潜在的な入力候補のポップアップ リストを提供します。 一般に、ユーザー ジェスチャには、入力候補のセッションが呼び出されます。 セッションには、潜在的な入力候補の一覧が表示されます。 および、ユーザーが 1 つを選択または一覧を消すことができます。 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>を作成して、トリガーする担当、<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>です。 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>計算、<xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet>セッションの完了の項目の。  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張点](../extensibility/language-service-and-editor-extension-points.md)   
 [エディターのインポート](../extensibility/editor-imports.md)