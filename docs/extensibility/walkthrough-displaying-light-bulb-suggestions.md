---
title: "チュートリアル: 電球検索候補の表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: 16
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e3838b7f9161991840bc5498f66abcfd3ce2b248
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>チュートリアル: 電球検索候補の表示
電球マークは、Visual Studio エディターで使用される一連のアクションを表示するを展開し、たとえば、組み込みのコード アナライザーまたはコードのリファクタリングによって識別される問題を修正するアイコン。  
  
 Visual c# および Visual Basic のエディターで記述し、独自のコード アナライザー電球を自動的に表示されるアクションをパッケージ化する .NET コンパイラ プラットフォーム ("Roslyn") を使用することもできます。 詳細については次を参照してください:  
  
-   [方法: c# 診断とコード修正を作成](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [方法: Visual Basic の診断とコード修正を作成](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 C などの他の言語では、その関数のスタブ実装を作成する提案などの一部のクイック操作の電球も提供します。  
  
 Light bulb は次のようになります。 赤の波線は、Visual Basic または Visual c# のプロジェクトで無効である場合に変数の名前で表示されます。 無効な識別子にマウス カーソルの近く、電球マークが表示されます。  
  
 ![電球](~/docs/extensibility/media/lightbulb.png "電球")  
  
 電球で下向きの矢印をクリックすると、選択したアクションのプレビューと、推奨されるアクションのセットが表示されますがします。 この場合、アクションを実行した場合、コードに加えられる変更を示します。  
  
 ![電球のプレビュー](~/docs/extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 電球を使用すると、推奨される操作を提供します。 たとえば、開く中かっこが新しい行に移動するか、前の行の末尾に移動するアクションを指定できます。 次のチュートリアルでは、現在のワードに表示される電球を作成する方法と、アクションを推奨される&2; つが:**大文字に変換**と**小文字に変換**します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) プロジェクトの作成  
  
1.  C# の場合は、VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前`LightBulbTest`します。  
  
2.  追加、**エディターの分類器**プロジェクト項目テンプレートです。 詳細については、次を参照してください。[エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。  
  
3.  既存のクラス ファイルを削除します。  
  
4.  プロジェクトに次の参照を追加し、設定**ローカル コピー**に`False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  新しいクラス ファイルを追加し、名前**LightBulbTest**します。  
  
6.  次の追加のステートメントを使用します。  
  
    ```c#  
    using System;  
    using System.Linq;  
    using System.Collections.Generic;  
    using System.Threading.Tasks;  
    using Microsoft.VisualStudio.Language.Intellisense;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Utilities;  
    using System.ComponentModel.Composition;  
    using System.Threading;  
  
    ```  
  
## <a name="implementing-the-light-bulb-source-provider"></a>電球ソース プロバイダーを実装します。  
  
1.  LightBulbTest.cs クラス ファイルでは、LightBulbTest クラスを削除します。 という名前のクラスを追加**TestSuggestedActionsSourceProvider** <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>を実装します。 名前を持つエクスポート**テスト推奨するアクション**と<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"の</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>。  
  
    ```c#  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  ソースのプロバイダー クラス内では、インポート、<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>プロパティとして追加します</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>。  
  
    ```c#  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A>を返すメソッドを<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>オブジェクト</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource></xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A>。 次のセクションで、ソースはについて説明します。  
  
    ```c#  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>ISuggestedActionSource を実装します。  
 推奨される操作のソースは、推奨されるアクションのセットを収集し、適切なコンテキストで追加することを担当します。 ここでは、コンテキストは、現在の単語と推奨される操作を実行**UpperCaseSuggestedAction**と**LowerCaseSuggestedAction**を次のセクションで説明します。  
  
1.  クラスを追加する**TestSuggestedActionsSource** <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>を実装します。  
  
    ```c#  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  推奨される操作の同期元プロバイダー、バッファーにテキストおよびテキスト ビューには、読み取り専用のプライベート フィールドを追加します。  
  
    ```c#  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  プライベート フィールドを設定するコンス トラクターを追加します。  
  
    ```c#  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  現在、カーソルの下にある単語を返すプライベート メソッドを追加します。 次のメソッドを使用して、カーソルの現在の場所を調べ、単語のエクステントをテキスト構造ナビゲーターを要求します。 カーソルが単語の上にある場合、<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>を出力パラメーターとして返しますそれ以外の場合、`out`パラメーターは`null`が返されます`false`。</xref:Microsoft.VisualStudio.Text.Operations.TextExtent> 。  
  
    ```c#  
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)  
    {  
        ITextCaret caret = m_textView.Caret;  
        SnapshotPoint point;  
  
        if (caret.Position.BufferPosition > 0)  
        {  
            point = caret.Position.BufferPosition - 1;  
        }  
        else  
        {  
            wordExtent = default(TextExtent);  
            return false;  
        }  
  
        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);  
  
        wordExtent = navigator.GetExtentOfWord(point);  
        return true;  
    }  
    ```  
  
5.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>メソッド</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>。 エディターでは、電球を表示するかどうかを確認するには、このメソッドを呼び出します。 例についてはこの呼び出しの実行は、多くの場合、カーソルは、1 つの行から移動するたびに、またはマウスを置く、エラー波線になります。 このメソッドを作業中実行するには、その他の UI 操作を許可するために非同期になります。 ほとんどの場合にこのメソッドは、いくつかの解析と現在の行の分析を実行する必要がありますので、処理時間がかかる場合します。  
  
     今回の実装に非同期的に取得、<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>しかどうか、エクステントは重要では、つまり、空白以外の任意のテキストがあるかどうかを決定します</xref:Microsoft.VisualStudio.Text.Operations.TextExtent>。  
  
    ```c#  
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        return Task.Factory.StartNew(() =>  
        {  
            TextExtent extent;  
            if (TryGetWordUnderCaret(out extent))  
            {  
                // don't display the action if the extent has whitespace  
                return extent.IsSignificant;  
              }  
            return false;  
        });  
    }  
    ```  
  
6.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A>の配列を返すメソッドを<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>を含む、さまざまなオブジェクト<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>オブジェクト</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction></xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet></xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A>。 電球が展開されているときは、このメソッドが呼び出されます。  
  
    > [!WARNING]
    >  ことを確認の実装`HasSuggestedActionsAsync()`と`GetSuggestedActions()`が矛盾しています。 は場合は、`HasSuggestedActionsAsync()`を返します`true`、し`GetSuggestedActions()`表示するいくつかのアクションを持つ必要があります。 多くの場合`HasSuggestedActionsAsync()`直前に呼び出されますが`GetSuggestedActions()`、これは常に大文字と小文字ができます。 たとえば、ユーザーは、キーを押して電球のアクションを呼び出します (ctrl キーを押しながら.) のみ`GetSuggestedActions()`と呼びます。  
  
    ```c#  
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        TextExtent extent;  
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)  
        {  
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);  
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);  
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);  
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };  
        }  
        return Enumerable.Empty<SuggestedActionSet>();  
    }   
    ```  
  
7.  定義、`SuggestedActionsChanged`イベントです。  
  
    ```c#  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  実装を完了するための実装を追加、`Dispose()`と`TryGetTelemetryId()`メソッドです。 遠隔測定を行う、false を返すため、および、GUID を空に設定しません。  
  
    ```c#  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample provider and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
## <a name="implementing-light-bulb-actions"></a>電球のアクションを実装します。  
  
1.  プロジェクトで、Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll およびセットへの参照を追加**ローカル コピー**に`False`します。  
  
2.  2 つのクラスを作成する最初の名前付き`UpperCaseSuggestedAction`と&2; 番目の名前付き`LowerCaseSuggestedAction`です。 クラスは両方とも実装<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>。</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>  
  
    ```c#  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     呼び出される<xref:System.String.ToUpper%2A>とその他の呼び出し<xref:System.String.ToLower%2A>。</xref:System.String.ToLower%2A></xref:System.String.ToUpper%2A>する点を除いて、両方のクラスが似た 次の手順では大文字操作クラスのみを対象にしていますが、両方のクラスを実装する必要があります。 小文字操作を実装するためのパターンとして、大文字操作を実装するための手順を使用します。  
  
3.  次の追加ステートメントを使用して、これらのクラス。  
  
    ```c#  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  一連のプライベート フィールドを宣言します。  
  
    ```c#  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  フィールドを設定するコンストラクターを追加します。  
  
    ```c#  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>メソッドことは、アクションのプレビューを表示できるようにします</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>。  
  
    ```c#  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>メソッドを返す、空、<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>列挙体</xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet></xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>。  
  
    ```c#  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  次のようにプロパティを設定します。  
  
    ```c#  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
    {  
        get { return m_display; }  
    }  
    public ImageMoniker IconMoniker  
    {  
       get { return default(ImageMoniker); }  
    }  
    public string IconAutomationText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public string InputGestureText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public bool HasPreview  
    {  
        get { return true; }  
    }  
    ```  
  
9. 実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>等価な大文字を範囲内のテキストを置き換えることでメソッド</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>。  
  
    ```c#  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  電球アクション**Invoke**メソッドは UI を表示するのには予期されていません。  アクションが特定の新しい UI (たとえばプレビューまたは選択ダイアログ) をもたらす場合も内から直接 UI が表示されない、 **Invoke**メソッドから戻った後、UI を表示する代わりにスケジュールが、 **Invoke**します。  
  
10. 完了するには、実装を追加、`Dispose()`と`TryGetTelemetryId()`メソッドです。  
  
    ```c#  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample action and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
11. に対して同じ処理を行うことを忘れないでください`LowerCaseSuggestedAction`を"'&0;'} 小文字に変換します"の呼び出し、<xref:System.String.ToUpper%2A><xref:System.String.ToLower%2A></xref:System.String.ToLower%2A></xref:System.String.ToUpper%2A>表示テキストを変更する。  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、LightBulbTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の&2; つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成し、いくつかのテキストを入力します。 テキストの左側に電球が表示されます。  
  
     ![電球のテスト](~/docs/extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  電球をポイントします。 下向きの矢印が表示されます。  
  
5.  電球をクリックすると&2; つの推奨する必要がありますと共に表示されます、選択したアクションのプレビュー。  
  
     ![拡大電球のテスト](~/docs/extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  最初の操作をクリックすると、現在の単語内のすべてのテキストが大文字に変換されます。 2 つ目の操作をクリックすると、すべてのテキストが小文字に変換されます。
