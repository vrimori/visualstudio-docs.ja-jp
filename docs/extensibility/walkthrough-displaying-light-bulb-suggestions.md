---
title: 'チュートリアル: 電球候補の表示 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 750e3b0915478b4249ce8db1ac294c1f2a3006f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148702"
---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>チュートリアル: 電球候補を表示します。
電球マークは、一連のアクションを表示するを展開し、組み込みのコード アナライザーまたはコードのリファクタリングによって特定した問題の修正例を Visual Studio エディターで使用されるアイコン。  
  
 は、Visual c# および Visual Basic エディターを記述して、代わって電球が自動的に表示されるアクションがある場合は、独自コード アナライザーをパッケージ化する .NET コンパイラ プラットフォーム ("Roslyn") を使用することができます。 詳細については次を参照してください:  
  
-   [方法: c# 診断と修正プログラムのコードを記述](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [方法: Visual Basic の診断と修正プログラムのコードを記述](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 C などの他の言語では、その関数のスタブ実装を作成する提案など、一部のクイック操作の代わって電球も提供します。  
  
 電球の外観を次に示します。 赤の波線は、Visual Basic または Visual c# プロジェクトで無効である場合に変数の名前で表示されます。 無効な識別子にマウスを置くと、カーソルの近く電球が表示されます。  
  
 ![電球](../extensibility/media/lightbulb.png "電球")  
  
 電球で下向きの矢印をクリックした場合、選択したアクションのプレビューと、一連の推奨される操作が表示されますがします。 この場合、アクションを実行する場合に、コードに加え、変更を示します。  
  
 ![電球のプレビュー](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 電球を使用すると、推奨される操作を提供します。 たとえば、かっこが新しい行に移動するか、前の行の末尾に移動するアクションを指定できます。 次のチュートリアルでは、現在の単語に表示される電球を作成する方法とは 2 つの推奨アクション:**大文字に変換**と**小文字に変換**です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) プロジェクトの作成  
  
1.  C# の場合は、VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前を付けます`LightBulbTest`です。  
  
2.  追加、**エディター分類子**プロジェクト項目テンプレート。 詳細については、次を参照してください。[エディター項目テンプレートに、拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
4.  プロジェクトに次の参照を追加し、設定**ローカル コピー**に`False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  新しいクラス ファイルを追加し、名前**LightBulbTest**です。  
  
6.  次の追加ステートメントを使用します。  
  
    ```csharp  
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
  
## <a name="implementing-the-light-bulb-source-provider"></a>電球ソース プロバイダーの実装  
  
1.  LightBulbTest.cs クラス ファイルでは、LightBulbTest クラスを削除します。 という名前のクラスを追加**TestSuggestedActionsSourceProvider**を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>です。 名前を持つエクスポート**テスト推奨アクション**と<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"です。  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  ソース プロバイダー クラス内のインポート、<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>プロパティとして追加します。  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A>を返すメソッドを<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>オブジェクト。 次のセクションで、ソースはについて説明します。  
  
    ```csharp  
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
 推奨されるアクションのソースは、推奨されるアクションのセットを収集し、適切なコンテキストで追加することを担当します。 この場合、コンテキストには、現在の単語と推奨される操作は**UpperCaseSuggestedAction**と**LowerCaseSuggestedAction**を次のセクションで説明します。  
  
1.  クラスを追加**TestSuggestedActionsSource**を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>です。  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  テキスト バッファーとテキスト ビューでは、推奨されるアクション ソース プロバイダーの読み取り専用のプライベート フィールドを追加します。  
  
    ```csharp  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  プライベート フィールドを設定するコンス トラクターを追加します。  
  
    ```csharp  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  現在のカーソルの下にある単語を返すプライベート メソッドを追加します。 次のメソッドを使用して、カーソルの現在の場所を調べ、単語の範囲をテキスト構造ナビゲーターを要求します。 カーソルが単語の上にある場合、<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>を out パラメーターで返します。 それ以外の場合、`out`パラメーターは`null`が返されます`false`です。  
  
    ```csharp  
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
  
5.  <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> メソッドを実装します。 エディターでは、電球を表示するかどうかを確認するには、このメソッドを呼び出します。 例についてはこの呼び出しの実行が多くの場合、カーソルは、1 つの行から移動するたびに、またはエラー波線、マウスがポイントされたときになります。 このメソッドを作業中実行するには、その他の UI 操作を許可するために非同期であります。 ほとんどの場合にこのメソッドがいくつかの解析と現在の行の分析を実行する必要があるため、処理時間がかかる場合します。  
  
     この実装でそれを非同期に取得、<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>しかどうか、エクステントは重要では、つまり、空白以外のいくつかのテキストがあるかどうかを決定します。  
  
    ```csharp  
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
  
6.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A>の配列を返すメソッド<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>を含む、さまざまなオブジェクト<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>オブジェクト。 電球が展開されている場合は、このメソッドが呼び出されます。  
  
    > [!WARNING]
    >  ことを確認の実装`HasSuggestedActionsAsync()`と`GetSuggestedActions()`が矛盾しています。 は場合、`HasSuggestedActionsAsync()`を返します`true`、し`GetSuggestedActions()`表示するいくつかのアクションを持つ必要があります。 多くの場合`HasSuggestedActionsAsync()`直前に呼び出されますが`GetSuggestedActions()`、これは常に大文字と小文字がします。 たとえば、ユーザーは、キーを押して、電球のアクションを呼び出します (CTRL +.) のみ`GetSuggestedActions()`と呼びます。  
  
    ```csharp  
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
  
7.  定義、`SuggestedActionsChanged`イベント。  
  
    ```csharp  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  完了するには、実装の実装を追加、`Dispose()`と`TryGetTelemetryId()`メソッドです。 製品利用統計情報、false を返すため、および GUID を空に設定したくありません。  
  
    ```csharp  
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
  
1.  プロジェクトで、Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll とセットへの参照を追加**ローカル コピー**に`False`です。  
  
2.  2 つのクラスを作成する最初の名前付き`UpperCaseSuggestedAction`と 2 番目の名前付き`LowerCaseSuggestedAction`します。 これらのクラスは、どちらも <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> を実装しています。  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     呼び出されることを除き、両方のクラスは似ています<xref:System.String.ToUpper%2A>および他の呼び出し<xref:System.String.ToLower%2A>です。 次の手順では大文字操作クラスのみを対象にしていますが、両方のクラスを実装する必要があります。 小文字操作を実装するためのパターンとして、大文字操作を実装するための手順を使用します。  
  
3.  次の追加ステートメントを使用して、これらのクラス。  
  
    ```csharp  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  一連のプライベート フィールドを宣言します。  
  
    ```csharp  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  フィールドを設定するコンストラクターを追加します。  
  
    ```csharp  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>メソッドがアクションのプレビューに表示できるようにします。  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>メソッドが、空を返すように<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>列挙します。  
  
    ```csharp  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  次のようにプロパティを設定します。  
  
    ```csharp  
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
  
9. 実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>等価な大文字を範囲内のテキストを置き換えることでメソッドです。  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  電球アクション**Invoke**メソッドは、UI を表示する必要はありません。  アクションは、新しい UI (たとえばプレビューまたは選択ダイアログ) を呼び出すことは、表示されません、UI 内から直接、 **Invoke**メソッドから返された後、UI を表示する代わりにスケジュールしますが、 **Invoke**.  
  
10. 完了するには、実装を追加、`Dispose()`と`TryGetTelemetryId()`メソッドです。  
  
    ```csharp  
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
  
11. 同じことに注意してください`LowerCaseSuggestedAction`"' 0'} 小文字に変換"と呼び出しを表示するテキストを変更する<xref:System.String.ToUpper%2A>に<xref:System.String.ToLower%2A>です。  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、LightBulbTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成し、いくつかのテキストを入力します。 電球マークのテキストの左側にあるはずです。  
  
     ![電球のテスト](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  電球をポイントします。 下向きの矢印が表示されます。  
  
5.  電球をクリックすると、2 つの推奨されるアクションが表示されます、と共に選択されたアクションのプレビューでは。  
  
     ![拡大電球のテスト](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  最初の操作をクリックすると、現在の単語内のすべてのテキストが大文字に変換されます。 2 つ目の操作をクリックすると、すべてのテキストが小文字に変換されます。  
  