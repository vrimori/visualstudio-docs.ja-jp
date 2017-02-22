---
title: "エディター内 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] 新しい - アーキテクチャ"
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
caps.latest.revision: 31
caps.handback.revision: 31
ms.author: "gregvanl"
manager: "ghogen"
---
# エディター内
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エディターはさまざまなテキスト ビューとユーザー インターフェイスからモデル別のテキスト エディターを保持する目的として設計された他のサブシステムで構成されます。  
  
 これらのセクションでは、エディターのさまざまな側面について説明します。  
  
-   [サブシステムの概要](../extensibility/inside-the-editor.md#overview)  
  
-   [テキスト モデル](../extensibility/inside-the-editor.md#textmodel)  
  
-   [テキスト ビュー](../extensibility/inside-the-editor.md#textview)  
  
 これらのセクションでは、エディターの機能について説明します。  
  
-   [タグと分類モデル](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
-   [表示要素](../extensibility/inside-the-editor.md#adornments)  
  
-   [射影](../extensibility/inside-the-editor.md#projection)  
  
-   [アウトライン](../extensibility/inside-the-editor.md#outlining)  
  
-   [マウスのバインド](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [エディターの操作](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a> サブシステムの概要  
  
### テキスト モデル サブシステム  
 テキスト モデル サブシステムは、テキストを表すと、その操作を有効にするとします。 テキスト モデルのサブシステムを含む、 <xref:Microsoft.VisualStudio.Text.ITextBuffer> のエディターで表示する文字のシーケンスを記述するインターフェイスです。 このテキストは、変更、追跡、およびそれ以外の場合、さまざまな方法で操作することができます。 テキスト モデルには、次の側面の型も使用できます。  
  
-   ファイルでは、テキストを関連付け、読み取りと書き込みにファイル システムを管理するサービス。  
  
-   2 つのシーケンス オブジェクトの間のわずかな差異の検出された差分サービスです。  
  
-   その他のバッファー内のテキストのサブセットの観点からバッファーにテキストを記述するためのシステム。  
  
 テキスト モデル サブシステムはユーザー インターフェイス \(UI\) の概念です。 たとえばはテキスト形式またはテキストのレイアウトを担当してテキストに関連付けられている可能性のあるビジュアル表示要素の情報を持たない。  
  
 テキスト モデル サブシステムのパブリック型は、.NET Framework 基本クラス ライブラリと Managed Extensibility Framework \(MEF\) にのみ依存 Microsoft.VisualStudio.Text.Data.dll と Microsoft.VisualStudio.CoreUtilitiy.dll に格納されます。  
  
### テキスト ビュー サブシステム  
 テキスト ビュー サブシステムは、書式設定して、テキストを表示するためです。 このサブシステム内の型は、Windows Presentation Foundation \(WPF\) が、型に依存しているかどうかに応じて、2 つのレイヤーに分割されます。 最も重要な型は <xref:Microsoft.VisualStudio.Text.Editor.ITextView> と <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, 、これを表示するテキスト行のセットとも、カレット、選択、および WPF UI 要素を使用して、テキストを装飾するための機能を制御します。 このサブシステムは、テキストの周囲のマージン領域の表示も提供します。 これらのマージンを拡張してさまざまな種類のコンテンツと視覚的効果を含めることができます。 余白の例については、行番号表示やスクロール バーです。  
  
 テキスト ビュー サブシステムのパブリック型は、Microsoft.VisualStudio.Text.UI.dll と Microsoft.VisualStudio.Text.UI.Wpf.dll に格納されます。 最初のアセンブリには、プラットフォームに依存しない要素が含まれているし、2 つ目には、WPF に固有の要素が含まれています。  
  
### 分類サブシステム  
 分類サブシステムは、テキストのフォントのプロパティを決定するためです。 分類子は、テキストを「キーワード」、「コメント」など、別のクラスに分割します。 分類形式マップこれらのクラスに関連する実際のフォントのプロパティ、たとえば、"Blue Consolas 10 pt"です。 この情報は、書式設定し、テキストを描画する場合、テキスト ビューで使用されます。 タグ付けするには、テキストの範囲に関連するデータが有効にしますこのトピックの後半で詳しく記載されています。  
  
 Microsoft.VisualStudio.Text.Logic.dll に分類サブシステムのパブリック型が含まれ、Microsoft.VisualStudio.Text.UI.Wpf.dll に格納されている分類の視覚的要素とやり取りしています。  
  
### 操作のサブシステム  
 操作のサブシステムでは、エディターの動作を定義します。 Visual Studio エディター コマンドの実装と、元に戻すシステムを提供します。  
  
## テキスト モデルとテキスト ビューについて詳しく見て  
  
###  <a name="textmodel"></a> テキスト モデル  
 テキスト モデル サブシステムは、テキスト型のさまざまなグループで構成されます。 バッファーにテキスト、テキストのスナップショットには、テキスト範囲が含まれます。  
  
#### テキスト バッファーとテキストのスナップショット  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> インターフェイスは、これは、エンコードで使用される utf\-16 を使用してエンコードされた Unicode 文字のシーケンスを表す、 `String` .NET Framework の型。 テキスト バッファーは、ファイル システムのドキュメントとして永続化することができますが、これは必要ありません。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> が空のテキスト バッファーまたは文字列から、またはから初期化されるテキスト バッファーを作成するために使用 <xref:System.IO.TextReader>します。 テキスト バッファーとしてファイル システムに永続化できる、 <xref:Microsoft.VisualStudio.Text.ITextDocument>です。  
  
 スレッドが呼び出すことによって、テキスト バッファーの所有権を取得するまで、任意のスレッドで、バッファーにテキストを編集できます <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>します。 その後、そのスレッドのみが編集を実行できます。  
  
 テキスト バッファーは、その有効期間中に多くのバージョンを移動できます。 バッファーが編集されるたびに、変更できない、新しいバージョンが生成される <xref:Microsoft.VisualStudio.Text.ITextSnapshot> そのバージョンのバッファーの内容を表します。 テキストのスナップショットは変更できないためにを表すテキスト バッファーが変化し続ける場合でも、制限なしの任意のスレッドでテキスト スナップショットにアクセスすることができます。  
  
#### テキストのスナップショットとスナップショットの行数  
 文字のシーケンス、または行のシーケンスとしては、テキストのスナップショットの内容を表示できます。 文字と行は、両方は、0 から始まるインデックスが作成されます。 空のテキスト スナップショットには、ゼロの文字と 1 つの空の行が含まれています。 有効な Unicode 改行文字シーケンス、または先頭または末尾バッファーの行が区切られます。 改行文字がテキスト スナップショットに明示的に表現し、テキスト スナップショット内の改行はすべて同じである必要があります。  
  
> [!NOTE]
>  Visual Studio エディターでの改行文字の詳細については、次を参照してください。 [エンコーディングと改行](../ide/encodings-and-line-breaks.md)します。  
  
 行のテキストがによって表される、 <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> オブジェクトで、特定の行番号または特定の文字位置のテキスト スナップショットから取得できます。  
  
#### SnapshotPoints、SnapshotSpans、および NormalizedSnapshotSpanCollections  
 A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> スナップショット内の文字位置を表します。 0 とスナップショットの長さの間にするには、位置が保証されます。 A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> スナップショット内のテキストの範囲を表します。 0 とスナップショットの長さの間にするには、終了位置が保証されます。<xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> のセットから成る <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 、同じスナップショットからのオブジェクト。  
  
#### スパンと NormalizedSpanCollections  
 A <xref:Microsoft.VisualStudio.Text.Span> テキスト スナップショット内のテキストの範囲に適用する間隔を表します。 スナップショットの位置は、範囲をゼロを含む任意の位置で開始できるように、0 から始まる。`End` 範囲のプロパティがの合計に等しい、 `Start` プロパティとその `Length` プロパティです。 A `Span` によってインデックス付けされている文字を含まない、 `End` プロパティです。 開始のあるスパンなど \= 5 と長さ \= 3 が最後 \= 8、5、6、および 7 の位置にある文字が含まれています。 この範囲の表記法は 5..8\) です。  
  
 2 つの範囲は、位置がある、共通の終了位置を含む場合と交差します。 交差部分ではこのため、\[3, 5\) と \[2, 7\) は \[3, 5\) との交差部分 \[3, 5\) と \[5, 7\) は \[5, 5\)。 \(ことに注意して \[5, 5\) は空の範囲です\)。  
  
 終了位置を除く位置が共通である場合、2 つの範囲が重複します。 空の範囲には、もう一方の範囲では、決してが重複していますされ、2 つの範囲の重なりが空ではありません。  
  
 A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> 範囲の開始のプロパティの順序での範囲の一覧を示します。 一覧で、重複または隣接する範囲がマージされます。 たとえば、範囲のセットが与えられる \[5..9\)、\[0..1\)、\[3..6\) と \[9..10\)、範囲の正規化されたリストは、\[0..1\)、\[3..10\) です。  
  
#### ITextEdit、TextVersion およびテキストの変更通知  
 使用してテキスト バッファーの内容を変更できる、 <xref:Microsoft.VisualStudio.Text.ITextEdit> オブジェクトです。 このようなオブジェクトを作成する \(のいずれかを使用して、 `CreateEdit()` メソッドの <xref:Microsoft.VisualStudio.Text.ITextBuffer>\) は、テキスト注釈のテキストのトランザクションを開始します。 すべての編集内容が文字列バッファー内のテキストの一部の範囲に代わるものです。 トランザクションの開始時に、座標および各編集の内容が、バッファーのスナップショットの基準とした表されます。<xref:Microsoft.VisualStudio.Text.ITextEdit> オブジェクトが同じトランザクションに他の編集の影響を受ける編集の座標を調整します。  
  
 たとえば、この文字列を格納しているテキスト バッファーがあるとします。  
  
```  
abcdefghij  
```  
  
 2 つの編集、ある範囲を置換する 1 つの編集を含むトランザクションを適用 \[2..4\) 文字を使用して `X` と 2 番目の編集をある範囲を置き換える \[6..9\) 文字を使用して `Y`します。 このバッファーになります。  
  
```  
abXefYj  
```  
  
 2 番目の編集の座標は、最初の編集を適用する前に、トランザクションの先頭にあるバッファーの内容に関して計算されました。  
  
 バッファーへの変更が反映ときに、 <xref:Microsoft.VisualStudio.Text.ITextEdit> オブジェクトが呼び出すことでコミットの `Apply()` メソッドです。 少なくとも 1 つの空でない編集があった場合、新しい <xref:Microsoft.VisualStudio.Text.ITextVersion> が作成されて、新しい <xref:Microsoft.VisualStudio.Text.ITextSnapshot> 作成されると、1 つと `Changed` イベントが発生します。 すべてのテキストのバージョンが異なるテキスト スナップショット。 テキスト スナップショットが編集トランザクション後テキスト バッファーのすべての状態を表しますが、テキスト バージョンごとに 1 つのスナップショットから変更のみをについて説明します。 一般に、テキスト スナップショットが 2 回使用するためのものし、破棄中に、テキストのバージョンはしばらくの間有効である必要があります。  
  
 テキスト形式を含む、 <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>です。 このコレクションの変更について説明する、スナップショットに適用されるときにその後のスナップショットが生成されます。 各 <xref:Microsoft.VisualStudio.Text.ITextChange> コレクション内で、変更、置換文字列と置換文字列の文字の位置が含まれています。 置換文字列は、基本的な挿入の空で、置換文字列が空の基本的な削除。 正規化されたコレクションは常に `null` テキスト バッファーの最新バージョンに対応します。  
  
 1 つだけ <xref:Microsoft.VisualStudio.Text.ITextEdit> いつでもテキスト バッファー オブジェクトをインスタンス化し、\(所有権を要求すると\) の場合は、テキスト バッファーを所有するスレッドですべてのテキストの編集を実行する必要があります。 テキストの編集を呼び出すことによって破棄することができます、 `Cancel` メソッドまたはその `Dispose` メソッドです。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 用意されています `Insert()`, 、`Delete()`, 、および `Replace()` で検出されたメソッドに類似した、 <xref:Microsoft.VisualStudio.Text.ITextEdit> インターフェイスです。 これらの呼び出しを作成すると同じ効果を持つ、 <xref:Microsoft.VisualStudio.Text.ITextEdit> のような呼び出しを行うと、編集を適用し、オブジェクトです。  
  
#### 追跡ポイントと追跡範囲  
 <xref:Microsoft.VisualStudio.Text.ITrackingPoint> テキスト バッファー内の文字位置を表します。 シフトする文字の位置を原因となる方法でバッファーを編集すると、追跡ポイントがそれに移動します。 たとえば、追跡ポイントは、バッファー内の位置 10 を参照すると、バッファーの先頭に 5 つの文字が挿入、追跡ポイントは、15 の位置を参照します。 動作が決まります正確に追跡ポイントで示される位置にある、挿入する場合は、その <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, 、いずれかを指定する `Positive` または `Negative`です。 追跡ポイントを指すようになりました。 カーソルの最後にある同じ文字追跡モードが正の場合追跡モードが負の値の場合、追跡ポイントは、元の位置に挿入された最初の文字を示します。 追跡ポイントで表される位置にある文字が削除された場合、追跡ポイントは、削除済みの範囲に続く最初の文字に移動します。 たとえば、追跡ポイントが、5 番目の位置にある文字を指す 3. ~ 6. を位置にある文字が削除された場合、追跡ポイントは 3 の位置にある文字を表します。  
  
 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 位置を 1 つだけではなく文字の範囲を表します。 動作が決まりますその <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>します。 スパンの管理モードの場合 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, 、追跡範囲の場合は、span 追跡モード; の端に挿入されたテキストを組み込むように拡大 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, 、追跡の範囲には、エッジに挿入されたテキストが含まれていません。 ただし、span 追跡モードの場合 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, 、挿入の開始に向かって現在の位置をプッシュする場合は、span 追跡モード <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, 、挿入が終了に向けて、現在の位置をプッシュします。  
  
 所属するテキスト バッファーの任意のスナップショットは、追跡ポイントの位置、または追跡の範囲の範囲を取得できます。 追跡ポイントと追跡範囲は、任意のスレッドからは安全に参照することがあります。  
  
#### コンテンツの種類  
 コンテンツの種類は、異なる種類のコンテンツを定義するためのメカニズムです。 コンテンツの種類には、ファイルの種類など、"text"、"code"または"binary"または"xml"、"vb"または"c\#"などのテクノロジの種類を指定できます。 たとえば、単語"using"は、他のプログラミング言語ではなく c\# および Visual Basic の両方でのキーワードです。 そのため、このキーワードの定義は"c\#"、"vb"コンテンツの種類に制限になります。  
  
 コンテンツの種類は、修飾、およびエディターの他の要素のフィルターとして使用されます。 多くのエディターの機能と拡張ポイントがコンテンツの種類ごとに定義されました。たとえば、テキストの色はプレーン テキスト ファイル、XML ファイル、および Visual Basic ソース コード ファイルです。 テキスト バッファーは、作成されると、テキスト バッファーのコンテンツの種類を変更するときに、一般にコンテンツの種類割り当てられています。  
  
 コンテンツの種類できます複数\-その他のコンテンツ タイプから継承します。<xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> で特定のコンテンツ タイプの親として複数の基本型を指定できます。  
  
 開発者が独自のコンテンツ タイプを定義およびそれらを使用して、登録、 <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>です。 使用して特定のコンテンツ タイプに関してエディター多くの機能を定義することができます、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>です。 たとえば、エディターの余白、表示要素、およびマウス ハンドラーは特定のコンテンツ タイプを表示する編集者にのみ適用されるようにします。  
  
###  <a name="textview"></a> テキスト ビュー  
 Model view controller \(MVC\) パターンのビューの一部では、ビュー、スクロール バーやキャレットなどのグラフィック要素の書式、テキスト ビューを定義します。 Visual Studio エディターのすべてのプレゼンテーション要素は、WPF に基づいています。  
  
#### テキスト ビュー  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> インターフェイスは、テキスト ビューのプラットフォームに依存しない形式です。 ウィンドウで、テキスト ドキュメントを表示するには、主に使用されますが、ことがでくにも使用の他の目的などがツールヒントにします。  
  
 テキスト ビューでは、さまざまな種類のテキスト バッファーを参照します。<xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> プロパティを参照、 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> これら 3 つの異なるテキスト バッファーを指すオブジェクトを: 最上位のレベルのデータ バッファーの編集が行われ、ビジュアルのバッファーは、テキスト ビューに表示されているバッファー内の編集バッファーは、データ バッファー。  
  
 テキストは、基になるテキスト バッファーに関連付けられている分類子に基づいて書式設定され、テキスト ビュー自体に関連付けられている adornment プロバイダーを使用した装飾。  
  
#### テキスト ビューの座標系  
 テキスト ビューの座標系では、テキスト ビュー内の位置を指定します。 この座標系において、 x 値 0.0 は表示されているテキストの左側に対応し、 y 値 0.0 は表示されているテキストの上端に対応します。 x 左から右への増加を調整し、 y 上から下への増加を調整します。  
  
 ビューポート \(テキスト ウィンドウに表示されているテキストの一部\) スクロールできない同様に、水平方向、垂直方向にスクロールします。 ビューポートは描画サーフェイスに関してを移動する、左端の座標を変更することで水平方向にスクロールします。 ただしなどが表示されるテキストを変更することによってのみを使用して、ビューポートを縦方向にスクロールする、 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> イベントが発生します。  
  
 座標系内の距離は、論理ピクセルに対応します。 テキストの表示サーフェイスが変換をスケーリングせず表示されている場合、テキスト レンダリング座標系内で 1 つの単位は、ディスプレイに 1 ピクセルに対応します。  
  
#### 余白  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> インターフェイスにある余白を表すし、余白、およびサイズの可視性の制御を有効にします。 "Top"、「左」、"Right"および「下部」を指定し、上部、下部、左側、またはビューの右端にアタッチされている 4 つ定義済みの余白があります。 これらのマージンは、他のマージンを配置できるコンテナーです。 インターフェイスは、余白のサイズと余白の可視性を返すメソッドを定義します。 余白は、アタッチ先のテキスト ビューに関する追加情報を提供するビジュアル要素です。 たとえば、行番号のマージンには、テキスト ビューの行番号が表示されます。 グリフの余白には、UI 要素が表示されます。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> インターフェイスの作成と余白の配置を処理します。 余白は、他のマージンに関して注文できます。 優先順位の高い余白はテキスト ビューに近い場所にあります。 たとえば、2 つの左右の余白、余白 A および B の余白があるし、余白 B が A の余白より低い優先順位、余白 B は余白 A. の左側に表示されます。  
  
#### テキスト ビューのホスト  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> インターフェイスには、テキスト ビューとビュー、スクロール バーなどに付随する隣接した装飾が含まれています。 テキスト ビューのホストには、ビューの枠線にアタッチされている余白も含まれています。  
  
#### 書式設定テキスト  
 テキスト ビューに表示されるテキストから成るは <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> のオブジェクト。 テキスト ビューの各行は、1 行のテキスト ビューでテキストに対応します。 基になるテキスト バッファー内の長い行か、部分的に \(テキストの折り返しが有効でない\) 場合に隠されてしたり複数のテキスト ビューの行に分割します。<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> インターフェイスには、メソッドとプロパティの座標と、文字間のマッピングおよび行に関連付けることの表示要素が含まれています。  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> オブジェクトを使用して作成される、 <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> インターフェイスです。 ビューに現在表示されているテキストは単に懸念がある場合は、書式設定のソースを無視できます。 文字列の形式で関心がある場合 \(たとえば、サポートしてリッチ テキストの切り取りと貼り付けを\)、ビューに表示されることができますを使用する <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> テキスト バッファー内のテキストの書式設定にします。  
  
 テキスト ビューのいずれかの書式 <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> 一度にします。  
  
## エディターの機能  
 エディターの機能は、機能の定義とは別の実装できるように設計されています。 エディターには、これらの機能が含まれています。  
  
-   タグと分類モデル  
  
-   表示要素  
  
-   射影  
  
-   アウトライン  
  
-   マウスとキーのバインド  
  
-   操作とプリミティブ  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a> タグと分類モデル  
 タグは、テキストの範囲に関連付けられているマーカーです。 提示できますさまざまな方法でなどのテキストの色分け表示、下線、グラフィック、またはポップアップを使用しています。 分類子は、1 つの種類のタグです。  
  
 それ以外のタグは <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> のテキストが強調表示、 <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> アウトラインと <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> のコンパイル エラー。  
  
#### 分類の種類  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> インターフェイスは、これは抽象のカテゴリ テキストの等価クラスを表します。 分類型複数の型から継承できます他の分類。 たとえば、プログラミング言語の分類があります「キーワード」、「コメント」と「識別子」、"code\] から継承します。 「名詞」、「動詞」および「形容詞として解釈」、「自然言語」を継承する自然言語の分類の種類があります。  
  
#### 分類  
 分類は、テキストの範囲で通常、特定の分類の種類のインスタンスです。 A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> 、分類を表すために使用します。 分類の範囲をテキストの特定の範囲をカバーし、このテキストの範囲は、特定の分類の種類のシステムに指示ラベルとして考えることができます。  
  
#### 分類モデル  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> テキスト分類のセットを分割するメカニズムです。 分類子の特定のコンテンツの種類に対して定義されているし、特定のテキスト バッファーに対してインスタンス化する必要があります。 クライアントを実装する必要があります <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> テキスト分類に参加します。  
  
#### 分類子アグリゲーター  
 分類子アグリゲーターは、分類の 1 つのセットに 1 つのテキスト バッファーのすべての分類子を結合するメカニズムです。 たとえば、c\# 分類子と英語の言語の分類子の両方は、c\# ファイルにコメントを分類を作成できます。 このコメントを考慮してください。  
  
```  
// This method produces a classifier  
```  
  
 C\# 分類器をコメントとして全体スパンにラベルを付ける可能性があります英語分類器可能性があります分類して「生成」、「動詞」と「名詞」と「メソッド」とします。 アグリゲーターは分類の重複しないのセットを生成し、セットの種類すべての投稿に基づいています。  
  
 テキスト分類のセットを分割しているためにも、分類子アグリゲーターにより、分類器です。 分類子アグリゲーターでは、重複する分類がないことと、分類が並べ替えられることも確認します。 個々 の分類モデルは、任意の順序で分類のセットを返すようにして、任意の方法で重複するには。  
  
#### 分類の書式設定とテキストの色分け  
 テキストの書式設定は、テキストの分類に基づいて構築された機能の例です。 アプリケーションでテキストを表示するテキスト ビューのレイヤーによって使用されます。 テキストの書式設定領域は、WPF によって異なりますが、分類の論理定義ではありません。  
  
 分類形式は、特定の分類の種類のプロパティを書式設定のセットです。 これらの形式は、親分類の種類の形式から継承します。  
  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> は分類の種類からテキストを書式設定プロパティのセットへのマップです。 エディターで書式設定のマップの実装では、分類の形式のすべてのエクスポートを処理します。  
  
###  <a name="adornments"></a> 表示要素  
 表示要素は、フォントとテキスト ビュー内の文字の色に直接関連していないグラフィック効果です。 など多くのプログラミング言語でのコンパイルからコードをマークするために使用に赤い波線の下線は、埋め込みの表示要素とヒントがポップアップ表示要素。 表示要素がから派生した <xref:System.Windows.UIElement> 実装と <xref:Microsoft.VisualStudio.Text.Tagging.ITag>です。 2 種類の特殊な表示要素タグ、 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, 、表示要素の表示ではテキストとして同じ領域を占有するのと <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, 、波線の下線のです。  
  
 埋め込みの表示要素は、テキストの書式設定されたビューの一部を形成するグラフィックスです。 これらは、Z オーダーの異なる層で構成されます。 次のように 3 つの組み込みレイヤーがある: テキスト、カレット、および選択します。 ただし、開発者はより多くのレイヤーを定義し、互いの順序で配置できます。 埋め込みの表示要素の次の 3 つの種類は、テキスト相対表示要素 \(これは、テキストが移動したときの移動とは、テキストを削除するとを削除\)、\(が、ビューのテキスト以外の部分とを行う\) ビューの相対表示要素には、および所有者コントロールの表示要素 \(開発者は、その配置を管理する必要があります\)。  
  
 ポップアップの表示要素は、小さなウィンドウでツールヒントなど、テキスト ビュー上に表示される画像です。  
  
###  <a name="projection"></a> 射影  
 射影は、別の種類のテキストを実際には保存されませんが、他のテキスト バッファーからのテキストが代わりに結合するテキスト バッファーを構築するための手法です。 たとえば、他の 2 つのバッファーからテキストを連結し、1 つのバッファーにある場合、結果を表示する、または 1 つのバッファー内のテキストの部分を非表示には、投影のバッファーを使用できます。 投影バッファーは、別の投影バッファーするソース バッファーとして利用できます。 さまざまな方法でテキストを並べ替えるには、一連の投影で関連付けられているバッファーを構築できます。 \(このようなセットとも呼ばれますが、 *バッファー グラフ*.\) 折りたたまれたテキストを非表示に投影バッファーを使用して、Visual Studio テキスト アウトライン表示機能を実装し、ASP.NET ページの Visual Studio エディターでは、プロジェクションを使用して、Visual Basic や c\# などの埋め込みの言語をサポートします。  
  
 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> を使用して作成された <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>します。 投影バッファーがの順序付けられたシーケンスによって表される <xref:Microsoft.VisualStudio.Text.ITrackingSpan> オブジェクトと呼ばれる *の範囲をソース*します。 これらの範囲の内容は、文字のシーケンスとして表示されます。 ソース範囲の描画元となるテキスト バッファーの名前は *ソース バッファー*します。 投影バッファーのクライアントを通常のテキスト バッファーとは異なることに留意する必要はありません。  
  
 投影バッファーは、ソース バッファーでテキスト変更イベントをリッスンします。 ソース内のテキスト間隔を変更するときに投影バッファーは独自の座標に変更されたテキストの座標をマップし、適切なテキスト変更イベントを発生させます。 たとえば、これらのコンテンツを持つソース バッファー A と B があるとします。  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 投影バッファー P がもう 1 つを持つすべてのバッファー A、B、バッファーのすべてが、2 つのテキスト範囲から形成される場合、P は、次の内容には。  
  
```  
P: ABCDEvwxyz  
```  
  
 場合、部分文字列 `xy` バッファー P を 7 と 8 の位置にある文字が削除されたことを示すイベントが発生し、B、バッファーから削除されます。  
  
 投影バッファーを直接編集もできます。 適切なソース バッファーの編集を伝達します。 たとえば、6 \(文字"v"の元の位置\) の位置にある P をバッファーに文字列を挿入すると場合、は、バッファー B 位置 1 に挿入が反映されます。  
  
 投影のバッファーに関与するソース範囲に制限があります。 ソース範囲が重複しないことがあります。投影バッファー内の場所は、ソース バッファー内の 1 つ以上の場所にマップできないし、ソース バッファーの場所は、投影バッファー内の 1 つ以上の場所にマップできません。 ソース バッファー リレーションシップで circularities が許可されていません。  
  
 イベントは、一連のソース バッファーの投影バッファー変更し、ソースの設定の変更にまたがっている場合がある場合に発生します。  
  
 省略バッファーは、特別な種類の投影バッファーです。 アウトラインの中止\] およびテキストのブロック、閉じたりする操作、主に使用されます。 省略バッファーは 1 つのソース バッファーに基づいており、省略バッファーのスパンする必要があります順序で指定する、同じソース バッファーの順序ができます。  
  
##### バッファーのグラフ  
 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> インターフェイス投影バッファーのグラフ全体のマッピングは有効にします。 すべてのテキスト バッファーと投影バッファーは、言語コンパイラによって生成される抽象構文ツリーと同様の有向非循環グラフに収集されます。 グラフは、すべてのバッファーにテキストになる可能性が最上位のバッファーによって定義されます。 バッファーのグラフには、コピー元のバッファー内のポイントを最上位のバッファー内のポイントまたはソース バッファー内の範囲のセットに最上位のバッファー内の範囲からをマップできます。 同様に、点をマップしたり、ソース バッファーから最上位のバッファー内のポイントにまで及ぶことができます。 バッファーのグラフを使用して作成される、 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>です。  
  
##### イベントと投影バッファー  
 投影バッファーが変更されたときに、それに依存するバッファーへの投影バッファーからの変更が送信されます。 すべてのバッファーを変更すると、以降、最下位のバッファーでバッファー変更イベントが発生します。  
  
###  <a name="outlining"></a> アウトライン  
 アウトラインの中止\] を展開または折りたたむテキスト ビュー内のテキストの異なるブロックがあります。 アウトライン表示は、種類として定義の <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, 、表示要素が定義されている方法で、同じです。 A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> できますを展開または折りたたむテキスト領域を定義するタグです。 インポートする必要がありますアウトラインを使用する、 <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> を取得する、 <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>です。 アウトラインのマネージャーを列挙、縮小、およびとして表現される別のブロックを展開する <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> オブジェクト、および、それに応じてイベントを発生させます。  
  
###  <a name="mousebindings"></a> マウスのバインド  
 マウスのバインドは、別のコマンドにマウスの動きをリンクします。 使用してマウス バインディングが定義されている、 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, を使用してショートカット キーが定義されていると、 <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>です。<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 自動的にすべてのバインディングのインスタンスを作成し、それらをビュー内でマウス イベントに接続します。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> インターフェイスには、別のマウス イベントの前処理や後処理のイベント ハンドラーが含まれています。 イベントのいずれかのハンドルをいくつかのメソッドのオーバーライドできます <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>します。  
  
###  <a name="editoroperations"></a> エディターの操作  
 エディターの操作は、スクリプトを実行して、エディター、またはその他の目的とのやり取りを自動化するために使用できます。 インポートすることができます、 <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> に対するアクセスの操作に、指定された <xref:Microsoft.VisualStudio.Text.Editor.ITextView>します。 これらのオブジェクトを使用して、選択内容を変更して、ビューをスクロールするか、ビューのさまざまな部分にキャレットを移動することができます。  
  
###  <a name="intellisense"></a> IntelliSense  
 ステートメント入力候補、シグネチャ ヘルプ \(パラメーターの情報とも呼ばれます\)、クイック ヒント、および電球、IntelliSense がサポートされます。  
  
 ステートメント入力候補では、メソッド名、XML 要素、およびその他のコードまたはマークアップ要素について、潜在的な入力候補のポップアップ リストを提供します。 一般に、ユーザー ジェスチャは、入力候補のセッションを起動します。 セッションには、潜在的な入力候補の一覧が表示され、ユーザーがいずれかを選択または一覧を消すことができます。<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> を作成して、トリガーする担当、 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>です。<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> 計算、 <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> のセッションの項目を完了します。  
  
## 参照  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)   
 [エディターのインポート](../extensibility/editor-imports.md)