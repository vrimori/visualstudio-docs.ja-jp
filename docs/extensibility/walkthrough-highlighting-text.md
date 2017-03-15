---
title: "チュートリアル: テキストの強調表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
caps.latest.revision: 42
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 029cc7785c49a08c7128bfaaff8f236e438efad8
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-highlighting-text"></a>チュートリアル: テキストの強調表示
エディターにさまざまな視覚効果を追加するには、Managed Extensibility Framework (MEF) コンポーネント パーツを作成します。 このチュートリアルでは、テキスト ファイルの現在の単語の出現がすべて強調表示する方法を示します。 単語では、テキスト ファイルの&1; つ以上の時間内で&1; か所でキャレットを配置する場合は、すべての検索結果が強調表示されます。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
1.  C# の場合は、VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前`HighlightWordTest`します。  
  
2.  エディターの分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="defining-a-textmarkertag"></a>TextMarkerTag を定義します。  
 テキストの強調表示する最初の手順は、サブクラスに<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>し、その外観を定義します</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。  
  
#### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>TextMarkerTag と、MarkerFormatDefinition を定義するには  
  
1.  クラス ファイルを追加し、名前**HighlightWordTag**します。  
  
2.  次の参照を追加します。  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  Presentation.Core  
  
    8.  Presentation.Framework  
  
3.  次の名前空間をインポートします。  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Linq;  
    using System.Threading;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Text.Tagging;  
    using Microsoft.VisualStudio.Utilities;  
    using System.Windows.Media;  
    ```  
  
4.  継承するクラスを作成<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>と名付けます`HighlightWordTag`</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。  
  
    ```c#  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5.  継承する&2; 番目のクラスを作成する<xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>、し HighlightWordFormatDefinition という名前を付けます</xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>。 に、タグをこの形式の定義を使用するために次の属性を持つエクスポートする必要があります。  
  
    -   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: タグでは、これを使用して、この形式の参照</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
    -   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: これが原因で UI に表示する形式</xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>  
  
    ```c#  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6.  HighlightWordFormatDefinition のコンス トラクターでは、表示名と外観を定義します。 背景のプロパティは、Foreground プロパティには、境界線の色が定義されています、塗りつぶしの色を定義します。  
  
    ```c#  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7.  HighlightWordTag のコンス トラクターで作成した形式の定義の名前を指定します。  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implementing-an-itagger"></a>ITagger を実装します。  
 次の手順を実装するのには、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>インターフェイス</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>。 このインターフェイスは、特定のテキスト バッファー、テキストの強調表示を提供するタグおよびその他の視覚効果に割り当てます。  
  
#### <a name="to-implement-a-tagger"></a>タガーを実装するには  
  
1.  実装するクラスを作成する<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>型の`HighlightWordTag`と名付けます`HighlightWordTagger`</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>。  
  
    ```c#  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2.  次のプライベート フィールドやプロパティをクラスに追加します。  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.ITextView>、現在のテキスト ビューに対応します</xref:Microsoft.VisualStudio.Text.Editor.ITextView>。  
  
    -   <xref:Microsoft.VisualStudio.Text.ITextBuffer>、テキスト ビューの基になるテキスト バッファーに対応します</xref:Microsoft.VisualStudio.Text.ITextBuffer>。  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>を使用してテキストを検索します</xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>。  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>、テキスト範囲内で移動するためのメソッドがあり</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>。  
  
    -   A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>、強調表示する単語のセットが含まれます</xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>。  
  
    -   A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>、現在の単語に対応します</xref:Microsoft.VisualStudio.Text.SnapshotSpan>。  
  
    -   A <xref:Microsoft.VisualStudio.Text.SnapshotPoint>、カレットの現在位置に対応します</xref:Microsoft.VisualStudio.Text.SnapshotPoint>。  
  
    -   ロック オブジェクトです。  
  
    ```c#  
    ITextView View { get; set; }  
    ITextBuffer SourceBuffer { get; set; }  
    ITextSearchService TextSearchService { get; set; }  
    ITextStructureNavigator TextStructureNavigator { get; set; }  
    NormalizedSnapshotSpanCollection WordSpans { get; set; }  
    SnapshotSpan? CurrentWord { get; set; }  
    SnapshotPoint RequestedPoint { get; set; }  
    object updateLock = new object();  
  
    ```  
  
3.  追加前に示したプロパティを初期化するコンス トラクターを追加<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>と<xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>イベント ハンドラー</xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> </xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 。  
  
    ```c#  
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,  
    ITextStructureNavigator textStructureNavigator)  
    {  
        this.View = view;  
        this.SourceBuffer = sourceBuffer;  
        this.TextSearchService = textSearchService;  
        this.TextStructureNavigator = textStructureNavigator;  
        this.WordSpans = new NormalizedSnapshotSpanCollection();  
        this.CurrentWord = null;  
        this.View.Caret.PositionChanged += CaretPositionChanged;  
        this.View.LayoutChanged += ViewLayoutChanged;  
    }  
  
    ```  
  
4.  両方の呼び出しのイベント ハンドラー、`UpdateAtCaretPosition`メソッドです。  
  
    ```c#  
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        // If a new snapshot wasn't generated, then skip this layout   
        if (e.NewSnapshot != e.OldSnapshot)  
        {  
            UpdateAtCaretPosition(View.Caret.Position);  
        }  
    }  
  
    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)  
    {  
        UpdateAtCaretPosition(e.NewPosition);  
    }  
    ```  
  
5.  追加する必要がありますも、 `TagsChanged` update メソッドが呼び出されるイベントです。  
  
     [!code-cs[VSSDKHighlightWordTest&#10;](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs) ] 
     [!code-vb [VSSDKHighlightWordTest&#10;](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]  
  
6.  `UpdateAtCaretPosition()`メソッドは、カーソルが配置されのリストを構築、単語と同じであるテキスト バッファー内のすべての単語を検索<xref:Microsoft.VisualStudio.Text.SnapshotSpan>、単語の出現回数に対応するオブジェクト</xref:Microsoft.VisualStudio.Text.SnapshotSpan>。 呼び出して`SynchronousUpdate`、どのを発生させる、`TagsChanged`イベントです。  
  
    ```c#  
    void UpdateAtCaretPosition(CaretPosition caretPosition)  
    {  
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);  
  
        if (!point.HasValue)  
            return;  
  
        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it   
        if (CurrentWord.HasValue  
            && CurrentWord.Value.Snapshot == View.TextSnapshot  
            && point.Value >= CurrentWord.Value.Start  
            && point.Value <= CurrentWord.Value.End)  
        {  
            return;  
        }  
  
        RequestedPoint = point.Value;  
        UpdateWordAdornments();  
    }  
  
    void UpdateWordAdornments()  
    {  
        SnapshotPoint currentRequest = RequestedPoint;  
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();  
        //Find all words in the buffer like the one the caret is on  
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);  
        bool foundWord = true;  
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit  
        if (!WordExtentIsValid(currentRequest, word))  
        {  
            //Before we retry, make sure it is worthwhile   
            if (word.Span.Start != currentRequest  
                 || currentRequest == currentRequest.GetContainingLine().Start  
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))  
            {  
                foundWord = false;  
            }  
            else  
            {  
                // Try again, one character previous.    
                //If the caret is at the end of a word, pick up the word.  
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);  
  
                //If the word still isn't valid, we're done   
                if (!WordExtentIsValid(currentRequest, word))  
                    foundWord = false;  
            }  
        }  
  
        if (!foundWord)  
        {  
            //If we couldn't find a word, clear out the existing markers  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);  
            return;  
        }  
  
        SnapshotSpan currentWord = word.Span;  
        //If this is the current word, and the caret moved within a word, we're done.   
        if (CurrentWord.HasValue && currentWord == CurrentWord)  
            return;  
  
        //Find the new spans  
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);  
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;  
  
        wordSpans.AddRange(TextSearchService.FindAll(findData));  
  
        //If another change hasn't happened, do a real update   
        if (currentRequest == RequestedPoint)  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);  
    }  
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)  
    {  
        return word.IsSignificant  
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));  
    }  
  
    ```  
  
7.  `SynchronousUpdate`に対して同期更新を実行、`WordSpans`と`CurrentWord`プロパティ、およびを発生させる、`TagsChanged`イベントです。  
  
    ```vb  
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)  
    {  
        lock (updateLock)  
        {  
            if (currentRequest != RequestedPoint)  
                return;  
  
            WordSpans = newSpans;  
            CurrentWord = newCurrentWord;  
  
            var tempEvent = TagsChanged;  
            if (tempEvent != null)  
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));  
        }  
    }  
    ```  
  
8.  実装する必要があります、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>メソッド</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>。 このメソッドのコレクションを受け取って<xref:Microsoft.VisualStudio.Text.SnapshotSpan>オブジェクトおよびタグの範囲の列挙を返します</xref:Microsoft.VisualStudio.Text.SnapshotSpan>。  
  
     C# の場合は、タグのにより、レイジー評価 (つまり、個々 の項目にアクセスする場合にのみセットの評価) yield 反復子としてこのメソッドを実装します。 Visual basic では、一覧に、タグを追加し、一覧を返します。  
  
     ここで返ります、<xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>を"blue"を持つオブジェクト<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>、青色の背景を提供する</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag></xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>。  
  
    ```c#  
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)  
    {  
        if (CurrentWord == null)  
            yield break;  
  
        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same  
        // collection throughout  
        SnapshotSpan currentWord = CurrentWord.Value;  
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;  
  
        if (spans.Count == 0 || wordSpans.Count == 0)  
            yield break;  
  
        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot   
        if (spans[0].Snapshot != wordSpans[0].Snapshot)  
        {  
            wordSpans = new NormalizedSnapshotSpanCollection(  
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));  
  
            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);  
        }  
  
        // First, yield back the word the cursor is under (if it overlaps)   
        // Note that we'll yield back the same word again in the wordspans collection;   
        // the duplication here is expected.   
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))  
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());  
  
        // Second, yield all the other words in the file   
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))  
        {  
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());  
        }  
    }  
    ```  
  
## <a name="creating-a-tagger-provider"></a>タガー プロバイダーを作成します。  
 タガーを作成するには、 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>。</xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>を実装する必要があります。 このクラスは MEF コンポーネント部分はので、この拡張機能が認識されるように、適切な属性を設定する必要があります。  
  
> [!NOTE]
>  MEF の詳細については、次を参照してください。 [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)します。  
  
#### <a name="to-create-a-tagger-provider"></a>タガー プロバイダーを作成するには  
  
1.  という名前のクラスを作成する`HighlightWordTaggerProvider`を実装する<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>、および<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"と<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute><xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag></xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag></xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute></xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>でエクスポート</xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>。  
  
    ```c#  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2.  2 つのエディター サービスをインポートする必要があります、<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>と<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>、タガーのインスタンスを作成します</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService></xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>。  
  
    ```c#  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3.  実装、<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>のインスタンスを返すメソッド`HighlightWordTagger`</xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>。  
  
    ```c#  
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag  
    {  
        //provide highlighting only on the top buffer   
        if (textView.TextBuffer != buffer)  
            return null;  
  
        ITextStructureNavigator textStructureNavigator =  
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);  
  
        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、HighlightWordTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
#### <a name="to-build-and-test-the-highlightwordtest-solution"></a>ビルドし、HighlightWordTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の&2; つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成し、単語が反復的テキスト「こんにちはこんにちはこんにちは」などを入力します。  
  
4.  「こんにちは」の出現回数のいずれかにカーソルを置きます。 すべての検索結果は、青で強調表示する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: ファイル名拡張子へのコンテンツの種類のリンク](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
