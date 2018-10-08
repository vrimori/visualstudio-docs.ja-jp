---
title: 'チュートリアル: Displaying Light Bulb Suggestions |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c36dad27a4d4a5bff5381b99041f7221447645e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548982"
---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>チュートリアル: 電球アイコンによる提案の表示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[チュートリアル: を表示する Light Bulb Suggestions](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-displaying-light-bulb-suggestions)します。  
  
電球マークを展開すると、一連のアクションを表示、組み込みのコード アナライザーやコード リファクタリングで識別された問題の修正など、Visual Studio エディターで使用されるアイコン。  
  
 Visual c# および Visual Basic のエディターで記述して、自動的に電球を表示するアクションを含む独自のコード アナライザーをパッケージ化する .NET コンパイラ プラットフォーム ("Roslyn") を使用することもできます。 詳細については次を参照してください:  
  
-   [方法: c# 診断とコード修正を書き込む](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [方法: Visual Basic の診断とコード修正を書き込む](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 C++ などの他の言語では、その関数のスタブ実装を作成する提案など、いくつかのクイック アクションの電球も提供します。  
  
 Light bulb によっては次のようになります。 赤い波線は、Visual Basic または Visual c# プロジェクトで無効である場合に変数の名前で表示されます。 無効な識別子にマウスを置く、カーソルの近くに電球が表示されます。  
  
 ![電球](../extensibility/media/lightbulb.png "電球")  
  
 電球で下矢印をクリックすると、一連の推奨されるアクションが表示され、選択したアクションのプレビュー。 この場合、アクションを実行する場合に、コードになる変更を示しています。  
  
 ![電球のプレビュー](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 電球を使用して、独自の推奨されるアクションを提供することができます。 たとえば、新しい行に中かっこを開くを移動または前の行の末尾に移動するアクションを提供できます。 次のチュートリアルでは、現在の単語の上に表示される電球を作成する方法と、2 つのアクションを提案が:**大文字に変換**と**小文字に変換**します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) プロジェクトの作成  
  
1.  C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューションの名前を`LightBulbTest`します。  
  
2.  追加、**エディター分類子**をプロジェクトに項目テンプレート。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
3.  既存のクラス ファイルを削除します。  
  
4.  次の参照をプロジェクトに追加し、設定**ローカル コピー**に`False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  新しいクラス ファイルを追加し、名前**LightBulbTest**します。  
  
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
  
## <a name="implementing-the-light-bulb-source-provider"></a>電球のソース プロバイダーを実装します。  
  
1.  LightBulbTest.cs クラス ファイルでは、LightBulbTest クラスを削除します。 という名前のクラスを追加**TestSuggestedActionsSourceProvider**を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>します。 名前と共にエクスポート**テスト推奨されるアクション**と<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text"です。  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  ソースのプロバイダー クラス内では、インポート、<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>プロパティとして追加します。  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A>を返すメソッドを<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>オブジェクト。 次のセクションで、ソースがについて説明します。  
  
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
 推奨される操作のソースが推奨されるアクションのセットを収集し、適切なコンテキストで追加することを担当します。 この場合、コンテキストには、現在の単語と推奨されるアクションは**UpperCaseSuggestedAction**と**LowerCaseSuggestedAction**を次のセクションで説明します。  
  
1.  クラスを追加**TestSuggestedActionsSource**を実装する<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>します。  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  推奨される操作のソース プロバイダー、テキスト バッファーおよびテキスト ビューには、読み取り専用のプライベート フィールドを追加します。  
  
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
  
4.  現在のカーソルの下にある単語を返すプライベート メソッドを追加します。 次のメソッドを使用して、カーソルの現在の場所を調べ、テキスト構造のナビゲーターの単語の範囲を要求します。 単語の上にカーソルがある場合、<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>が out パラメーターで返されます。 それ以外の場合、`out`パラメーターが`null`、メソッドを返します`false`します。  
  
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
  
5.  <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> メソッドを実装します。 エディターでは、電球を表示するかどうかを確認するには、このメソッドを呼び出します。 例についてはこの呼び出しの実行は非常に多くの場合、カーソルは、1 つの行から移動したときに、または、エラー波線、マウスを置いたときになります。 このメソッドの実行中実行するには、他の UI 操作を許可するために非同期になります。 このメソッドは、解析および現在の行の分析を実行する必要があるほとんどの場合、そのため、処理時間がかかります。  
  
     今回の実装でそれを非同期に取得、<xref:Microsoft.VisualStudio.Text.Operations.TextExtent>空白以外のいくつかのテキストがあるかどうか、エクステントはつまり、重要で、かどうかを決定します。  
  
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
    >  できるようにしてくださいの実装`HasSuggestedActionsAsync()`と`GetSuggestedActions()`は一貫性のある; である場合は、`HasSuggestedActionsAsync()`を返します`true`、し`GetSuggestedActions()`を表示するいくつかのアクションがあります。 多くの場合`HasSuggestedActionsAsync()`直前に呼び出されますが`GetSuggestedActions()`が常にはこれが、ケースになることはありません。 たとえば、ユーザーがキーを押して電球アクションを呼び出します (CTRL +.) のみ`GetSuggestedActions()`が呼び出されます。  
  
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
  
8.  実装を完了するには、実装を追加、`Dispose()`と`TryGetTelemetryId()`メソッド。 遠隔測定を行う、false を返すため、および GUID を空に設定するはありません。  
  
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
  
## <a name="implementing-light-bulb-actions"></a>電球アクションを実装します。  
  
1.  プロジェクトで、Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll セットへの参照を追加**ローカル コピー**に`False`します。  
  
2.  2 つのクラスを作成するという名前の最初の`UpperCaseSuggestedAction`という名前の 2 つ目と`LowerCaseSuggestedAction`します。 これらのクラスは、どちらも <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> を実装しています。  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     両方のクラスは似ていますが呼び出される<xref:System.String.ToUpper%2A>およびその他の呼び出し<xref:System.String.ToLower%2A>します。 次の手順では大文字操作クラスのみを対象にしていますが、両方のクラスを実装する必要があります。 小文字操作を実装するためのパターンとして、大文字操作を実装するための手順を使用します。  
  
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
  
6.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>メソッドをアクションのプレビューに表示できるようにします。  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>メソッドが返す、空ように<xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>列挙体。  
  
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
  
9. 実装、<xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>範囲内のテキストを等価な大文字に置き換えることによりメソッド。  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  電球アクション**Invoke**メソッドが UI を表示する必要はありません。  新しい UI (プレビューまたは選択ダイアログなど) は、アクションを表示する場合も内から直接 UI が表示されない、 **Invoke**メソッドから返された後、UI を表示する代わりにスケジュールしますが、 **Invoke**.  
  
10. 実装を完了するには追加、`Dispose()`と`TryGetTelemetryId()`メソッド。  
  
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
  
11. 忘れずに、同じこと`LowerCaseSuggestedAction`表示テキストを変更する"変換 '{0}' に大文字と小文字の"と呼び出し<xref:System.String.ToUpper%2A>に<xref:System.String.ToLower%2A>します。  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
 このコードをテストするには、LightBulbTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
1.  ソリューションをビルドします。  
  
2.  デバッガーでこのプロジェクトを実行すると、Visual Studio の 2 つ目のインスタンスがインスタンス化されます。  
  
3.  テキスト ファイルを作成し、いくつかのテキストを入力します。 テキストの左側に電球が表示されます。  
  
     ![電球のテスト](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  電球をポイントします。 下向きの矢印が表示されます。  
  
5.  電球をクリックすると 2 つの推奨されるアクションが表示されます、と共に、選択したアクションのプレビュー。  
  
     ![拡大電球のテスト](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  最初の操作をクリックすると、現在の単語内のすべてのテキストが大文字に変換されます。 2 つ目の操作をクリックすると、すべてのテキストが小文字に変換されます。

