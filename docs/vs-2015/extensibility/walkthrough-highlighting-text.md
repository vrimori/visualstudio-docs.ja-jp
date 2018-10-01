---
title: 'チュートリアル: テキストの強調表示 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
caps.latest.revision: 43
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 238d9d65ac43fc5d33c05a28c48ed62c57102d92
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537774"
---
# <a name="walkthrough-highlighting-text"></a>チュートリアル: テキストの強調表示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[チュートリアル: テキストの強調表示](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-highlighting-text)します。  
  
エディターにさまざまな視覚効果を追加するには、Managed Extensibility Framework (MEF) コンポーネント パーツを作成します。 このチュートリアルでは、出現するすべてのテキスト ファイルの現在の単語を強調表示する方法を示します。 単語では、テキスト ファイルの 1 つ以上の時間が 1 つにキャレットを配置する場合は、出現するすべてが強調表示されます。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-mef-project"></a>MEF プロジェクトを作成します。  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前を`HighlightWordTest`します。  
  
2.  エディター分類子の項目テンプレートをプロジェクトに追加します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
## <a name="defining-a-textmarkertag"></a>TextMarkerTag を定義します。  
 テキストの強調表示の最初の手順は、サブクラスに<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>し、その外観を定義します。  
  
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
  
    ```csharp  
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
  
4.  継承するクラスを作成<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>名前を付けます`HighlightWordTag`します。  
  
    ```csharp  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5.  2 番目のクラスから継承する作成<xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>、HighlightWordFormatDefinition 名前を付けます。 この形式の定義をタグを使用するには、次の属性を持つエクスポートする必要があります。  
  
    -   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: タグでは、これを使用して、この形式の参照  
  
    -   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: これにより、UI に表示する形式  
  
    ```csharp  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6.  HighlightWordFormatDefinition のコンス トラクターでは、その表示名と外観を定義します。 Background プロパティは、Foreground プロパティ境界線の色を定義するときに、塗りつぶしの色を定義します。  
  
    ```csharp  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7.  HighlightWordTag のコンス トラクターで作成した形式の定義の名前を渡します。  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implementing-an-itagger"></a>ITagger を実装します。  
 次の手順を実装するためには、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>インターフェイス。 このインターフェイスは、テキストを指定したバッファー、テキストを強調表示を提供するタグとその他の視覚効果を割り当てます。  
  
#### <a name="to-implement-a-tagger"></a>タガーを実装するには  
  
1.  実装するクラスを作成<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>型の`HighlightWordTag`、名前を付けます`HighlightWordTagger`します。  
  
    ```csharp  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2.  クラスには、次のプライベート フィールドとプロパティを追加します。  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.ITextView>、現在のテキスト ビューに対応します。  
  
    -   <xref:Microsoft.VisualStudio.Text.ITextBuffer>、テキスト ビューを基になるテキスト バッファーに対応します。  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>テキストの検索に使用されます。  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>、テキスト範囲内で移動するためのメソッドを持ちます。  
  
    -   A<xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>単語を強調表示のセットを含むです。  
  
    -   A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>、現在の単語に対応します。  
  
    -   A<xref:Microsoft.VisualStudio.Text.SnapshotPoint>キャレットの現在位置に対応します。  
  
    -   ロック オブジェクト。  
  
    ```csharp  
    ITextView View { get; set; }  
    ITextBuffer SourceBuffer { get; set; }  
    ITextSearchService TextSearchService { get; set; }  
    ITextStructureNavigator TextStructureNavigator { get; set; }  
    NormalizedSnapshotSpanCollection WordSpans { get; set; }  
    SnapshotSpan? CurrentWord { get; set; }  
    SnapshotPoint RequestedPoint { get; set; }  
    object updateLock = new object();  
  
    ```  
  
3.  追加前に示したプロパティを初期化するコンス トラクターを追加<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>と<xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>イベント ハンドラー。  
  
    ```csharp  
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
  
4.  両方を呼び出すイベント ハンドラー、`UpdateAtCaretPosition`メソッド。  
  
    ```csharp  
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
  
5.  追加することも必要があります、 `TagsChanged` update メソッドによって呼び出されるイベント。  
  
     [!code-csharp[VSSDKHighlightWordTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkhighlightwordtest/cs/highlightwordtag.cs#10)]
     [!code-vb[VSSDKHighlightWordTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhighlightwordtest/vb/highlightwordtag.vb#10)]  
  
6.  `UpdateAtCaretPosition()`メソッドは、カーソルが配置されの一覧を構築します。 単語と同じであるテキスト バッファー内のすべての単語を検索<xref:Microsoft.VisualStudio.Text.SnapshotSpan>、単語の出現回数に対応するオブジェクト。 呼び出して`SynchronousUpdate`を発生させる、`TagsChanged`イベント。  
  
    ```csharp  
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
  
7.  `SynchronousUpdate`の同期更新を実行、`WordSpans`と`CurrentWord`プロパティ、および発生させ、`TagsChanged`イベント。  
  
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
  
8.  実装する必要があります、<xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>メソッド。 このメソッドのコレクションを受け取り<xref:Microsoft.VisualStudio.Text.SnapshotSpan>オブジェクトおよびタグの範囲の列挙体を返します。  
  
     C# では、このメソッドを yield 反復子は、により、レイジー評価 (つまり、個々 の項目がアクセスされたときにのみ、セットの評価) として、タグの実装します。 Visual basic では、一覧に、タグを追加し、一覧を返します。  
  
     ここで、メソッドが返されます、 <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> "blue"を含むオブジェクト<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>、青色の背景を提供します。  
  
    ```csharp  
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
 実装する必要があります、タガーを作成する、<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>します。 このクラスを MEF コンポーネント パーツはため、この拡張機能が認識されるように、適切な属性を設定する必要があります。  
  
> [!NOTE]
>  MEF の詳細については、次を参照してください。 [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)します。  
  
#### <a name="to-create-a-tagger-provider"></a>タガー プロバイダーを作成するには  
  
1.  という名前のクラスを作成`HighlightWordTaggerProvider`を実装する<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>、およびエクスポートして、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"の<xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>の<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>。  
  
    ```csharp  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2.  2 つのエディター サービスをインポートする必要があります、<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>と<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>タガーをインスタンス化します。  
  
    ```csharp  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3.  実装、<xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>のインスタンスを返すメソッド`HighlightWordTagger`します。  
  
    ```csharp  
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
  
#### <a name="to-build-and-test-the-highlightwordtest-solution"></a>ビルドして HighlightWordTest ソリューションをテストするには  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成し、たとえば、「こんにちはこんにちはこんにちは」では、単語を繰り返す、テキストを入力します。  
  
4.  「こんにちは」の出現回数のいずれかにカーソルを置きます。 すべての検索結果は、青色で強調表示する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

