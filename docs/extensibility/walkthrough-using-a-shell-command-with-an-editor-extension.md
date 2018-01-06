---
title: "チュートリアル: シェル コマンドを使用したエディターの拡張子を持つ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
caps.latest.revision: "46"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5a7f9426297ef28bdf4b829bd6697543f5aab55f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-using-a-shell-command-with-an-editor-extension"></a>チュートリアル: シェル コマンドを使用したエディターの拡張子を持つ
VSPackage からには、エディターにメニュー コマンドなどの機能を追加できます。 このチュートリアルでは、メニュー コマンドを呼び出すことによって、エディターでテキスト ビューに表示要素を追加する方法を示します。  
  
 このチュートリアルでは、Managed Extensibility Framework (MEF) コンポーネント パーツと共に VSPackage の使用を示します。 Visual Studio シェルを使用して、メニュー コマンドを登録する VSPackage を使用する必要があり、MEF コンポーネント パーツにアクセスするコマンドを使用することができます。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-an-extension-with-a-menu-command"></a>メニュー コマンドを使用して、拡張機能の作成  
 という名前のメニュー コマンドを格納する VSPackage を作成**表示要素の追加**上、**ツール**メニュー。  
  
1.  という名前の C# の場合は、VSIX プロジェクトを作成する`MenuCommandTest`、項目テンプレート名をカスタム コマンドを追加および**AddAdornment**です。 詳細については、次を参照してください。[メニュー コマンドを使用して、拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
2.  MenuCommandTest をという名前のソリューションが開かれます。 MenuCommandTestPackage ファイルは、メニュー コマンドを作成しに配置するコードを**ツール**メニュー。 この時点では、コマンドが発生すると、メッセージ ボックスを表示します。 後の手順では、このコメントの表示要素を表示する設定を変更する方法を示します。  
  
3.  VSIX マニフェスト エディターで source.extension.vsixmanifest ファイルを開きます。 `Assets`  タブ、Microsoft.VisualStudio.VsPackage MenuCommandTest をという名前の行がある必要があります。  
  
4.  保存して、Source.extension.vsixmanifest ファイルを閉じます。  
  
## <a name="adding-a-mef-extension-to-the-command-extension"></a>コマンドの拡張機能への MEF 拡張機能の追加  
  
1.  **ソリューション エクスプ ローラー**ソリューション ノードを右クリックしをクリックして**追加**、クリックして**新しいプロジェクト**です。 **新しいプロジェクトの追加**ダイアログ ボックスで、をクリックして**機能拡張** **Visual c#**、し**VSIX プロジェクト**です。 プロジェクトに `CommentAdornmentTest` という名前を付けます。  
  
2.  このプロジェクトは、VSPackage の厳密な名前付きアセンブリと対話は、ためアセンブリに署名する必要があります。 VSPackage アセンブリで既に作成キー ファイルを再利用することができます。  
  
    1.  プロジェクトのプロパティを開き、選択、**署名**タブです。  
  
    2.  選択**アセンブリに署名**です。  
  
    3.  **厳密な名前キー ファイルを選択して**、MenuCommandTest アセンブリに対して生成された Key.snk ファイルを選択します。  
  
## <a name="referring-to-the-mef-extension-in-the-vspackage-project"></a>VSPackage プロジェクト内の MEF 拡張機能を参照します。  
 VSPackage に MEF コンポーネントを追加するため、マニフェストで資産の両方の種類を指定する必要があります。  
  
> [!NOTE]
>  MEF の詳細については、次を参照してください。 [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)です。  
  
#### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>VSPackage プロジェクトに MEF コンポーネントを参照するには  
  
1.  MenuCommandTest プロジェクトでは、VSIX マニフェスト エディターで source.extension.vsixmanifest ファイルを開きます。  
  
2.  **資産** タブで、をクリックして**新規**です。  
  
3.  **型**一覧で、選択**Microsoft.VisualStudio.MefComponent**です。  
  
4.  **ソース**一覧で、選択**現在のソリューション内のプロジェクト**です。  
  
5.  **プロジェクト**一覧で、選択**CommentAdornmentTest**です。  
  
6.  保存して、source.extension.vsixmanifest ファイルを閉じます。  
  
7.  MenuCommandTest プロジェクト CommentAdornmentTest プロジェクトを参照していることを確認します。  
  
8.  CommentAdornmentTest プロジェクトでは、アセンブリを生成するためにプロジェクトを設定します。 **ソリューション エクスプ ローラー**プロジェクトを選択して、ファイルの場所、**プロパティ**ウィンドウ、 **OutputDirectory をコピー構築出力**プロパティ、に設定し、**true**です。  
  
## <a name="defining-a-comment-adornment"></a>コメントの表示要素を定義します。  
 自体のコメント表示要素から成る、<xref:Microsoft.VisualStudio.Text.ITrackingSpan>選択したテキストと、作成者およびテキストの説明を表すいくつかの文字列を追跡します。  
  
#### <a name="to-define-a-comment-adornment"></a>コメントの表示要素を定義するには  
  
1.  CommentAdornmentTest プロジェクトで、新しいクラス ファイルを追加し、名前`CommentAdornment`です。  
  
2.  次の参照を追加します。  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  PresentationCore  
  
    8.  PresentationFramework  
  
    9. WindowsBase  
  
3.  次の追加`using`ステートメントです。  
  
    ```vb  
    using Microsoft.VisualStudio.Text;  
    ```  
  
4.  ファイルは、という名前のクラスを含める必要があります`CommentAdornment`です。  
  
    ```  
    internal class CommentAdornment  
    ```  
  
5.  次の 3 つのフィールドを追加、`CommentAdornment`のクラス、<xref:Microsoft.VisualStudio.Text.ITrackingSpan>作成者、および説明します。  
  
    ```csharp  
    public readonly ITrackingSpan Span;  
    public readonly string Author;  
    public readonly string Text;  
    ```  
  
6.  フィールドを初期化するコンス トラクターを追加します。  
  
    ```csharp  
    public CommentAdornment(SnapshotSpan span, string author, string text)  
    {  
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);  
        this.Author = author;  
        this.Text = text;  
    }  
    ```  
  
## <a name="creating-a-visual-element-for-the-adornment"></a>表示要素のビジュアル要素の作成  
 表示要素の視覚的要素を定義することも必要があります。 このチュートリアルでは、Windows Presentation Foundation (WPF) クラスから継承されるコントロールを定義<xref:System.Windows.Controls.Canvas>です。  
  
1.  CommentAdornmentTest プロジェクトでクラスを作成し、名前を付けます`CommentBlock`です。  
  
2.  次の `using` ステートメントを追加します。  
  
    ```csharp  
    using Microsoft.VisualStudio.Text;  
    using System;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Media;  
    using System.Windows.Shapes;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  ように、`CommentBlock`クラスから継承する<xref:System.Windows.Controls.Canvas>です。  
  
    ```csharp  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4.  表示要素の視覚的な側面を定義するいくつかのプライベート フィールドを追加します。  
  
    ```csharp  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
    ```  
  
5.  コメントの表示要素を定義し、関連するテキストを追加するコンス トラクターを追加します。  
  
    ```csharp  
    public CommentBlock(double textRightEdge, double viewRightEdge,   
            Geometry newTextGeometry, string author, string body)  
    {  
        if (brush == null)  
        {  
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));  
            brush.Freeze();  
            Brush penBrush = new SolidColorBrush(Colors.Green);  
            penBrush.Freeze();  
            solidPen = new Pen(penBrush, 0.5);  
            solidPen.Freeze();  
            dashPen = new Pen(penBrush, 0.5);  
            dashPen.DashStyle = DashStyles.Dash;  
            dashPen.Freeze();  
        }  
  
        this.textGeometry = newTextGeometry;  
  
        TextBlock tb1 = new TextBlock();  
        tb1.Text = author;  
        TextBlock tb2 = new TextBlock();  
        tb2.Text = body;  
  
        const int MarginWidth = 8;  
        this.commentGrid = new Grid();  
        this.commentGrid.RowDefinitions.Add(new RowDefinition());  
        this.commentGrid.RowDefinitions.Add(new RowDefinition());  
        ColumnDefinition cEdge = new ColumnDefinition();  
        cEdge.Width = new GridLength(MarginWidth);  
        ColumnDefinition cEdge2 = new ColumnDefinition();  
        cEdge2.Width = new GridLength(MarginWidth);  
        this.commentGrid.ColumnDefinitions.Add(cEdge);  
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());  
        this.commentGrid.ColumnDefinitions.Add(cEdge2);  
  
        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();  
        rect.RadiusX = 6;  
        rect.RadiusY = 3;  
        rect.Fill = brush;  
        rect.Stroke = Brushes.Green;  
  
            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);  
            tb1.Measure(inf);  
            tb2.Measure(inf);  
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);  
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;  
  
        Grid.SetColumn(rect, 0);  
        Grid.SetRow(rect, 0);  
         Grid.SetRowSpan(rect, 2);  
        Grid.SetColumnSpan(rect, 3);  
        Grid.SetRow(tb1, 0);  
        Grid.SetColumn(tb1, 1);  
        Grid.SetRow(tb2, 1);  
        Grid.SetColumn(tb2, 1);  
        this.commentGrid.Children.Add(rect);  
        this.commentGrid.Children.Add(tb1);  
        this.commentGrid.Children.Add(tb2);  
  
        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));  
         Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);  
  
        this.Children.Add(this.commentGrid);  
    }  
    ```  
  
6.  実装も、<xref:System.Windows.Controls.Panel.OnRender%2A>表示要素を描画するイベント ハンドラー。  
  
    ```csharp  
    protected override void OnRender(DrawingContext dc)  
    {  
        base.OnRender(dc);  
        if (this.textGeometry != null)  
        {  
            dc.DrawGeometry(brush, solidPen, this.textGeometry);  
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);  
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);  
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);  
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);  
            dc.DrawLine(dashPen, p1, p2);  
            dc.DrawLine(dashPen, p2, p3);  
        }  
    }  
    ```  
  
## <a name="adding-an-iwpftextviewcreationlistener"></a>IWpfTextViewCreationListener を追加します。  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>ビューの作成イベントをリッスンするように使用できる MEF コンポーネント パーツがします。  
  
1.  CommentAdornmentTest プロジェクトにクラス ファイルを追加し、名前を付けます`Connector`です。  
  
2.  次の `using` ステートメントを追加します。  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  実装するクラスを宣言<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>、およびエクスポートに、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"と<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>の<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>します。 コンテンツの種類の属性は、コンポーネントを適用するコンテンツの種類を指定します。 テキストの種類は、すべての非バイナリ ファイルの種類の基本型です。 そのため、作成されるほとんどすべてのテキスト ビューは、この型のされます。 テキスト ビューに role 属性には、コンポーネントを適用するテキスト ビューの種類を指定します。 ドキュメントのテキスト ビュー ロールは、通常は行で構成され、ファイルに格納されているテキストを表示します。  
  
     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]  
  
4.  実装、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>メソッドを呼び出す、静的なので`Create()`のイベント、`CommentAdornmentManager`です。  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        CommentAdornmentManager.Create(textView);  
    }  
    ```  
  
5.  コマンドの実行に使用できるメソッドを追加します。  
  
    ```csharp  
    static public void Execute(IWpfTextViewHost host)  
    {  
        IWpfTextView view = host.TextView;  
        //Add a comment on the selected text.   
        if (!view.Selection.IsEmpty)  
        {  
            //Get the provider for the comment adornments in the property bag of the view.  
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));  
  
            //Add some arbitrary author and comment text.   
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;  
            string comment = "Four score....";  
  
            //Add the comment adornment using the provider.  
            provider.Add(view.Selection.SelectedSpans[0], author, comment);  
        }  
    }  
    ```  
  
## <a name="defining-an-adornment-layer"></a>装飾層を定義します。  
 新しい装飾を追加するには、装飾層を定義する必要があります。  
  
#### <a name="to-define-an-adornment-layer"></a>装飾層を定義するには  
  
1.  `Connector`クラス、型のパブリック フィールドを宣言<xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>でエクスポートし、<xref:Microsoft.VisualStudio.Utilities.NameAttribute>装飾層に一意の名前を指定して、<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>他のテキストをこの装飾層の Z オーダーのリレーションシップを定義します。レイヤー (テキスト、カレット、選択範囲) を表示します。  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="providing-comment-adornments"></a>コメントの表示要素を提供します。  
 表示要素を定義するときは、コメントの表示要素プロバイダーとコメント装飾マネージャーにも実装します。 コメントの表示要素のプロバイダーはコメントの表示要素の一覧を保持がリッスンする<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>基になるテキスト バッファーと、基になるテキストが削除されたときに削除コメントの表示要素のイベントです。  
  
1.  CommentAdornmentTest プロジェクトに新しいクラス ファイルを追加し、名前`CommentAdornmentProvider`です。  
  
2.  次の `using` ステートメントを追加します。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.ObjectModel;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    ```  
  
3.  という名前のクラスを追加`CommentAdornmentProvider`です。  
  
    ```csharp  
    internal class CommentAdornmentProvider  
    {  
    }  
    ```  
  
4.  テキスト バッファーおよびバッファーに関連するコメントの表示要素の一覧のプライベート フィールドを追加します。  
  
    ```csharp  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5.  コンス トラクターを追加`CommentAdornmentProvider`です。 このコンス トラクターは、によって、プロバイダーがインスタンス化されるため、プライベート アクセス権がある、`Create()`メソッドです。 コンス トラクターを追加、`OnBufferChanged`イベント ハンドラーを<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>イベント。  
  
    ```csharp  
    private CommentAdornmentProvider(ITextBuffer buffer)  
    {  
        this.buffer = buffer;  
        //listen to the Changed event so we can react to deletions.   
        this.buffer.Changed += OnBufferChanged;  
    }  
  
    ```  
  
6.  `Create()` メソッドを追加します。  
  
    ```csharp  
    public static CommentAdornmentProvider Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });  
    }  
  
    ```  
  
7.  `Detach()` メソッドを追加します。  
  
    ```csharp  
    public void Detach()  
    {  
        if (this.buffer != null)  
        {  
            //remove the Changed listener   
            this.buffer.Changed -= OnBufferChanged;  
            this.buffer = null;  
        }  
    }  
    ```  
  
8.  追加、`OnBufferChanged`イベント ハンドラー。  
  
    ```csharp  
    private void OnBufferChanged(object sender, TextContentChangedEventArgs e)  
    {  
        //Make a list of all comments that have a span of at least one character after applying the change. There is no need to raise a changed event for the deleted adornments. The adornments are deleted only if a text change would cause the view to reformat the line and discard the adornments.  
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            Span span = comment.Span.GetSpan(e.After);  
            //if a comment does not span at least one character, its text was deleted.   
            if (span.Length != 0)  
            {  
                keptComments.Add(comment);  
            }  
        }  
  
        this.comments = keptComments;  
    }  
  
    ```  
  
     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]  
  
9. 宣言を追加、`CommentsChanged`イベント。  
  
    ```csharp  
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;  
    ```  
  
10. 作成、`Add()`表示要素を追加するメソッド。  
  
    ```csharp  
    public void Add(SnapshotSpan span, string author, string text)  
    {  
        if (span.Length == 0)  
            throw new ArgumentOutOfRangeException("span");  
        if (author == null)  
            throw new ArgumentNullException("author");  
        if (text == null)  
            throw new ArgumentNullException("text");  
  
        //Create a comment adornment given the span, author and text.  
        CommentAdornment comment = new CommentAdornment(span, author, text);  
  
        //Add it to the list of comments.   
        this.comments.Add(comment);  
  
        //Raise the changed event.  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
        if (commentsChanged != null)  
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));  
    }  
  
    ```  
  
11. 追加、`RemoveComments()`メソッドです。  
  
    ```csharp  
    public void RemoveComments(SnapshotSpan span)  
    {  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
  
        //Get a list of all the comments that are being kept   
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith.   
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
            {  
                //Raise the change event to delete this comment.   
                if (commentsChanged != null)  
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));  
            }  
            else  
                keptComments.Add(comment);  
        }  
  
        this.comments = keptComments;  
    }  
    ```  
  
12. 追加、`GetComments()`を指定したスナップショットの範囲内のすべてのコメントを返すメソッド。  
  
    ```csharp  
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)  
    {  
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();  
        foreach (CommentAdornment comment in this.comments)  
        {  
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
                overlappingComments.Add(comment);  
        }  
  
        return new Collection<CommentAdornment>(overlappingComments);  
    }  
    ```  
  
13. という名前のクラスを追加`CommentsChangedEventArgs`、次のようにします。  
  
    ```csharp  
    internal class CommentsChangedEventArgs : EventArgs  
    {  
        public readonly CommentAdornment CommentAdded;  
  
        public readonly CommentAdornment CommentRemoved;  
  
        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)  
        {  
            this.CommentAdded = added;  
            this.CommentRemoved = removed;  
        }  
    }  
    ```  
  
## <a name="managing-comment-adornments"></a>コメントの表示要素の管理  
 コメントの装飾マネージャーは、表示要素を作成し、装飾層に追加します。 リッスンする、<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>と<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>イベントことが移動または表示要素を削除することができます。 これもをリッスンする、`CommentsChanged`コメントの追加または削除する場合に、コメントの表示要素のプロバイダーによって発生するイベントです。  
  
1.  CommentAdornmentTest プロジェクトにクラス ファイルを追加し、名前を付けます`CommentAdornmentManager`です。  
  
2.  次の `using` ステートメントを追加します。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Windows.Media;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Formatting;  
    ```  
  
3.  という名前のクラスを追加`CommentAdornmentManager`です。  
  
    ```csharp  
    internal class CommentAdornmentManager  
        {  
        }  
    ```  
  
4.  いくつかのプライベート フィールドを追加します。  
  
    ```csharp  
    private readonly IWpfTextView view;  
    private readonly IAdornmentLayer layer;  
    private readonly CommentAdornmentProvider provider;  
    ```  
  
5.  管理者がサブスクライブしているコンス トラクターを追加、<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>と<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>イベント、およびにも、`CommentsChanged`イベント。 静的で、マネージャーがインスタンス化されるため、コンス トラクターはプライベート`Create()`メソッドです。  
  
    ```csharp  
    private CommentAdornmentManager(IWpfTextView view)  
    {  
        this.view = view;  
        this.view.LayoutChanged += OnLayoutChanged;  
        this.view.Closed += OnClosed;  
  
        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");  
  
        this.provider = CommentAdornmentProvider.Create(view);  
        this.provider.CommentsChanged += OnCommentsChanged;  
    }  
    ```  
  
6.  追加、`Create()`をプロバイダーを取得するか、必要な場合は、1 つを作成します。  
  
    ```csharp  
    public static CommentAdornmentManager Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });  
    }  
    ```  
  
7.  追加、`CommentsChanged`ハンドラー。  
  
    ```csharp  
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)  
    {  
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag).   
        if (e.CommentRemoved != null)  
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);  
  
        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout).   
        if (e.CommentAdded != null)  
            this.DrawComment(e.CommentAdded);  
    }  
    ```  
  
8.  追加、<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>ハンドラー。  
  
    ```csharp  
    private void OnClosed(object sender, EventArgs e)  
    {  
        this.provider.Detach();  
        this.view.LayoutChanged -= OnLayoutChanged;  
        this.view.Closed -= OnClosed;  
    }  
    ```  
  
9. 追加、<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>ハンドラー。  
  
    ```csharp  
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        //Get all of the comments that intersect any of the new or reformatted lines of text.  
        List<CommentAdornment> newComments = new List<CommentAdornment>();  
  
        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.    
        //Use the latter to find the comments that intersect the new or reformatted lines of text.   
        foreach (Span span in e.NewOrReformattedSpans)  
        {  
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));  
        }  
  
        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not.   
        //Sort the list and skip duplicates.  
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });  
  
        CommentAdornment lastComment = null;  
        foreach (CommentAdornment comment in newComments)  
        {  
            if (comment != lastComment)  
            {  
                lastComment = comment;  
                this.DrawComment(comment);  
            }  
        }  
    }  
    ```  
  
10. コメントを描画するプライベート メソッドを追加します。  
  
     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]  
  
## <a name="using-the-menu-command-to-add-the-comment-adornment"></a>コメントの表示要素を追加するメニュー コマンドを使用します。  
 実装することによってコメントの表示要素を作成するメニュー コマンドを使用することができます、 `MenuItemCallback` VSPackage のメソッドです。  
  
1.  MenuCommandTest プロジェクトに次の参照を追加します。  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.Editor  
  
    -   Microsoft.VisualStudio.Text.UI.Wpf  
  
2.  AddAdornment.cs ファイルを開き、次の追加`using`ステートメントです。  
  
    ```csharp  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3.  ShowMessageBox() メソッドを削除し、次のコマンド ハンドラーを追加します。  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4.  アクティブなビューを取得するコードを追加します。 取得する必要があります、 `SVsTextManager` 、アクティブなを取得する Visual Studio シェルの`IVsTextView`します。  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5.  このテキスト ビューがエディターのテキスト ビューのインスタンスの場合にキャストできます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>インターフェイスを取得、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>とそれに関連する<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>です。 使用して、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>を呼び出して、`Connector.Execute()`メソッドでは、コメントの表示要素のプロバイダーを取得し、表示要素を追加します。 コマンド ハンドラーは、次のようになります。  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
        IVsUserData userData = vTextView as IVsUserData;  
         if (userData == null)  
        {  
            Console.WriteLine("No text view is currently open");  
                            return;  
        }  
        IWpfTextViewHost viewHost;  
        object holder;  
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;  
        userData.GetData(ref guidViewHost, out holder);  
        viewHost = (IWpfTextViewHost)holder;  
        Connector.Execute(viewHost);  
    }  
    ```  
  
6.  AddAdornment コンス トラクターで AddAdornment コマンドのハンドラーとして AddAdornmentHandler メソッドを設定します。  
  
    ```csharp  
    private AddAdornment(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.AddAdornmentHandler;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>コードのビルドとテスト  
  
1.  ソリューションをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
2.  テキスト ファイルを作成します。 いくつかのテキストを入力し、それを選択します。  
  
3.  **ツール** メニューのをクリックして**呼び出す追加装飾**です。 バルーンは、テキスト ウィンドウの右側に表示するかし、次のようなテキストを含める必要があります。  
  
     YourUserName  
  
     Fourscore しています.  
  
## <a name="see-also"></a>参照  
 [チュートリアル: コンテンツの種類とファイル名拡張子とをリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)