---
title: 'チュートリアル: エディター拡張機能でシェル コマンドの使用 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b62ffce08ecf5b6397bdda0b1f9fb6c1b83d7b63
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154338"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>チュートリアル: エディター拡張機能でシェル コマンドを使用します。
VSPackage からには、エディターにメニュー コマンドなどの機能を追加できます。 このチュートリアルでは、メニュー コマンドを呼び出すことによって、エディターでテキスト ビューに表示要素を追加する方法を示します。  
  
 このチュートリアルでは、VSPackage と Managed Extensibility Framework (MEF) コンポーネントの一部の使用を示します。 VSPackage を使用して、Visual Studio シェルをメニュー コマンドを登録する必要があります。 また、MEF コンポーネント パーツにアクセスするコマンドを使用することができます。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールしないでください。 Visual Studio のセットアップのオプション機能として含まれています。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。  
  
## <a name="create-an-extension-with-a-menu-command"></a>メニュー コマンドを使用して拡張機能を作成します。  
 という名前のメニュー コマンドを配置する VSPackage を作成**追加 Adornment**上、**ツール**メニュー。  
  
1.  という名前の c# VSIX プロジェクトを作成する`MenuCommandTest`、カスタム コマンドの項目テンプレート名を追加および**AddAdornment**します。 詳細については、次を参照してください。[メニュー コマンドを使用して拡張機能を作成する](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
2.  MenuCommandTest という名前のソリューションを開きます。 MenuCommandTestPackage ファイルがメニュー コマンドを作成し、に配置するコードを**ツール**メニュー。 この時点では、コマンドが発生すると、メッセージ ボックスを表示します。 後の手順では、コメントの表示要素を表示するときに変更する方法を示します。  
  
3.  開く、 *source.extension.vsixmanifest* VSIX マニフェスト エディターでファイル。 `Assets`  タブ、Microsoft.VisualStudio.VsPackage MenuCommandTest をという名前の行がある必要があります。  
  
4.  保存して閉じます、 *source.extension.vsixmanifest*ファイル。  
  
## <a name="add-a-mef-extension-to-the-command-extension"></a>コマンド拡張機能に MEF 拡張機能を追加します。  
  
1.  **ソリューション エクスプ ローラー**は、ソリューション ノードを右クリックし、[**追加**、] をクリックし、**新しいプロジェクト**します。 **新しいプロジェクトの追加**ダイアログ ボックスで、をクリックして**拡張** **Visual c#**、し**VSIX プロジェクト**。 プロジェクトに `CommentAdornmentTest` という名前を付けます。  
  
2.  このプロジェクトは、VSPackage の厳密な名前付きアセンブリと対話は、ため、アセンブリに署名する必要があります。 既に作成されて、VSPackage アセンブリのキー ファイルを再利用することができます。  
  
    1.  プロジェクトのプロパティを開き、選択、**署名**タブ。  
  
    2.  選択**アセンブリに署名**します。  
  
    3.  **厳密な名前キー ファイルを選択して**を選択、 *Key.snk* MenuCommandTest アセンブリ用に生成されたファイル。  
  
## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>VSPackage プロジェクトで MEF 拡張機能を参照してください。  
 VSPackage を MEF コンポーネントを追加するため、マニフェストで両方の種類のアセットを指定する必要があります。  
  
> [!NOTE]
>  MEF の詳細については、次を参照してください。 [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)します。  
  
### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>VSPackage プロジェクトを MEF コンポーネントを参照するには  
  
1.  MenuCommandTest プロジェクトで開き、 *source.extension.vsixmanifest* VSIX マニフェスト エディターでファイル。  
  
2.  **資産**] タブで [**新規**します。  
  
3.  **型**一覧で、選択**Microsoft.VisualStudio.MefComponent**します。  
  
4.  **ソース**一覧で、選択**現在のソリューションでプロジェクトを**します。  
  
5.  **プロジェクト**一覧で、選択**CommentAdornmentTest**します。  
  
6.  保存して閉じます、 *source.extension.vsixmanifest*ファイル。  
  
7.  MenuCommandTest プロジェクト CommentAdornmentTest プロジェクトを参照していることを確認します。  
  
8.  CommentAdornmentTest プロジェクトでアセンブリを生成するプロジェクトを設定します。 **ソリューション エクスプ ローラー**、プロジェクトを選択し、ファイルの場所、**プロパティ**のウィンドウ、 **OutputDirectory をコピー構築出力**プロパティ、に設定し、**true**します。  
  
## <a name="define-a-comment-adornment"></a>コメントの表示要素を定義します。  
 コメントの表示要素自体から成る、<xref:Microsoft.VisualStudio.Text.ITrackingSpan>選択したテキストと、作成者とテキストの説明を表すいくつかの文字列を追跡します。  
  
#### <a name="to-define-a-comment-adornment"></a>コメントの表示要素を定義するには  
  
1.  CommentAdornmentTest プロジェクトで新しいクラス ファイルを追加し、名前`CommentAdornment`します。  
  
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
  
3.  次の追加`using`ステートメント。  
  
    ```csharp
    using Microsoft.VisualStudio.Text;  
    ```  
  
4.  ファイルは、という名前のクラスを含める必要があります`CommentAdornment`します。  
  
    ```csharp  
    internal class CommentAdornment  
    ```  
  
5.  次の 3 つのフィールドを追加、`CommentAdornment`クラス、<xref:Microsoft.VisualStudio.Text.ITrackingSpan>作成者、および説明します。  
  
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
  
## <a name="create-a-visual-element-for-the-adornment"></a>表示要素のビジュアル要素を作成します。  
 表示要素のビジュアル要素を定義します。 このチュートリアルでは、Windows Presentation Foundation (WPF) クラスから継承するコントロールを定義<xref:System.Windows.Controls.Canvas>します。  
  
1.  CommentAdornmentTest プロジェクトでクラスを作成し、名前`CommentBlock`します。  
  
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
  
3.  ように、`CommentBlock`クラスから継承する<xref:System.Windows.Controls.Canvas>します。  
  
    ```csharp  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4.  表示要素の視覚的な側面を定義するいくつかのプライベート フィールドを追加します。  
  
    ```csharp  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
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
  
6.  実装することも、<xref:System.Windows.Controls.Panel.OnRender%2A>イベント ハンドラーを表示要素を描画します。  
  
    ```csharp  
    protected override void OnRender(DrawingContext dc)  
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
  
## <a name="add-an-iwpftextviewcreationlistener"></a>追加、IWpfTextViewCreationListener  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>作成イベントの表示をリッスンするように使用できる MEF コンポーネントの一部です。  
  
1.  CommentAdornmentTest プロジェクトにクラス ファイルを追加し、名前`Connector`します。  
  
2.  次の `using` ステートメントを追加します。  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  実装するクラスを宣言<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>でエクスポートし、 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text"、<xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>の<xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>。 コンテンツの種類の属性には、コンポーネントを適用するコンテンツの種類を指定します。 テキスト型は、すべての非バイナリ ファイルの種類の基本型です。 そのため、作成されるほぼすべてのテキスト ビューは、この型になります。 テキスト ビューの role 属性には、コンポーネントを適用するテキスト ビューの種類を指定します。 ドキュメントのテキスト ビュー ロールは、通常は行で構成され、ファイルに格納されているテキストを表示します。  
  
     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]  
  
4.  実装、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>メソッドを呼び出して、静的な`Create()`のイベント、`CommentAdornmentManager`します。  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        CommentAdornmentManager.Create(textView);  
    }  
    ```  
  
5.  コマンドの実行に使用できるメソッドを追加します。  
  
    ```csharp  
    static public void Execute(IWpfTextViewHost host)  
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
  
## <a name="define-an-adornment-layer"></a>装飾層を定義します。  
 新しい表示要素を追加するには、装飾層を定義する必要があります。  
  
### <a name="to-define-an-adornment-layer"></a>装飾層を定義するには  
  
1.  `Connector`クラス、型のパブリック フィールドを宣言<xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>でエクスポート、<xref:Microsoft.VisualStudio.Utilities.NameAttribute>装飾層の一意の名前を指定して、<xref:Microsoft.VisualStudio.Utilities.OrderAttribute>その他のテキストをこの装飾層の Z オーダーのリレーションシップを定義します。(テキスト、カレット、[選択]) のレイヤーを表示します。  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="provide-comment-adornments"></a>コメントの表示要素を提供します。  
 表示要素を定義するときに、コメント表示要素のプロバイダーとコメント表示要素のマネージャーにも実装します。 コメントの表示要素のプロバイダーがコメントの表示要素のリストを保持がリッスンする<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>基になるテキスト バッファー、および基になるテキストが削除されたときに削除コメントの表示要素のイベント。  
  
1.  CommentAdornmentTest プロジェクトに新しいクラス ファイルを追加し、名前`CommentAdornmentProvider`します。  
  
2.  次の `using` ステートメントを追加します。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.ObjectModel;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    ```  
  
3.  という名前のクラスを追加`CommentAdornmentProvider`します。  
  
    ```csharp  
    internal class CommentAdornmentProvider  
    {  
    }  
    ```  
  
4.  テキスト バッファーとバッファーに関連するコメントの表示要素のリスト用のプライベート フィールドを追加します。  
  
    ```csharp  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5.  追加のコンス トラクター`CommentAdornmentProvider`します。 によって、プロバイダーがインスタンス化されるため、このコンス トラクターはプライベート アクセスに必要、`Create()`メソッド。 コンス トラクターを追加、`OnBufferChanged`イベント ハンドラーを<xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>イベント。  
  
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
    public static CommentAdornmentProvider Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });  
    }  
  
    ```  
  
7.  `Detach()` メソッドを追加します。  
  
    ```csharp  
    public void Detach()  
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
  
     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]  
  
9. 宣言を追加、`CommentsChanged`イベント。  
  
    ```csharp  
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;  
    ```  
  
10. 作成、`Add()`表示要素を追加します。  
  
    ```csharp  
    public void Add(SnapshotSpan span, string author, string text)  
    {  
        if (span.Length == 0)  
            throw new ArgumentOutOfRangeException("span");  
        if (author == null)  
            throw new ArgumentNullException("author");  
        if (text == null)  
            throw new ArgumentNullException("text");  
  
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
  
11. 追加、`RemoveComments()`メソッド。  
  
    ```csharp  
    public void RemoveComments(SnapshotSpan span)  
    {  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
  
        //Get a list of all the comments that are being kept   
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
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
  
12. 追加、`GetComments()`を特定のスナップショットの範囲内のすべてのコメントを返すメソッド。  
  
    ```csharp  
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)  
    {  
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();  
        foreach (CommentAdornment comment in this.comments)  
        {  
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
                overlappingComments.Add(comment);  
        }  
  
        return new Collection<CommentAdornment>(overlappingComments);  
    }  
    ```  
  
13. という名前のクラスを追加`CommentsChangedEventArgs`、次のようにします。  
  
    ```csharp  
    internal class CommentsChangedEventArgs : EventArgs  
    {  
        public readonly CommentAdornment CommentAdded;  
  
        public readonly CommentAdornment CommentRemoved;  
  
        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)  
        {  
            this.CommentAdded = added;  
            this.CommentRemoved = removed;  
        }  
    }  
    ```  
  
## <a name="manage-comment-adornments"></a>コメントの表示要素を管理します。  
 コメントの表示要素のマネージャーは、表示要素を作成し、装飾層に追加します。 リッスンし、<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>と<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>イベントを移動したり、表示要素を削除するようにします。 またをリッスンし、`CommentsChanged`コメントを追加または削除されたときに、コメントの表示要素のプロバイダーによって送出されるイベントです。  
  
1.  CommentAdornmentTest プロジェクトにクラス ファイルを追加し、名前`CommentAdornmentManager`します。  
  
2.  次の `using` ステートメントを追加します。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Windows.Media;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Formatting;  
    ```  
  
3.  という名前のクラスを追加`CommentAdornmentManager`します。  
  
    ```csharp  
    internal class CommentAdornmentManager  
        {  
        }  
    ```  
  
4.  いくつかのプライベート フィールドを追加します。  
  
    ```csharp  
    private readonly IWpfTextView view;  
    private readonly IAdornmentLayer layer;  
    private readonly CommentAdornmentProvider provider;  
    ```  
  
5.  サブスクライブするには管理コンス トラクターを追加、<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>と<xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>イベントとにも、`CommentsChanged`イベント。 静的、マネージャーがインスタンス化されるため、コンス トラクターはプライベート`Create()`メソッド。  
  
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
  
6.  追加、`Create()`プロバイダーを取得または必要に応じて、1 つを作成するメソッド。  
  
    ```csharp  
    public static CommentAdornmentManager Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });  
    }  
    ```  
  
7.  追加、`CommentsChanged`ハンドラー。  
  
    ```csharp  
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)  
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
    private void OnClosed(object sender, EventArgs e)  
    {  
        this.provider.Detach();  
        this.view.LayoutChanged -= OnLayoutChanged;  
        this.view.Closed -= OnClosed;  
    }  
    ```  
  
9. 追加、<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>ハンドラー。  
  
    ```csharp  
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
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
  
## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>メニュー コマンドを使用して、コメントの表示要素を追加するには  
 メニュー コマンドを使用して実装することによってコメントの表示要素を作成することができます、 `MenuItemCallback` VSPackage のメソッド。  
  
1.  MenuCommandTest プロジェクトに次の参照を追加します。  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.Editor  
  
    -   Microsoft.VisualStudio.Text.UI.Wpf  
  
2.  開く、 *AddAdornment.cs*ファイルを開き、次の追加`using`ステートメント。  
  
    ```csharp  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3.  削除、`Execute()`メソッドを次のコマンド ハンドラーを追加します。  
  
    ```csharp  
    private async void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4.  アクティブなビューを取得するコードを追加します。 取得する必要があります、 `SVsTextManager` 、アクティブなを取得する Visual Studio shell の`IVsTextView`します。  
  
    ```csharp  
    private async void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5.  このテキスト ビューがエディターのテキスト ビューのインスタンスの場合にキャストできます、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>インターフェイスを取得し、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>とそれに関連付けられた<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>します。 使用して、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>を呼び出す、`Connector.Execute()`メソッドでは、コメントの表示要素のプロバイダーを取得し、表示要素を追加します。 コマンド ハンドラーは、このコードのようになります。  
  
    ```csharp  
    private async void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));  
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
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    } 
    ```  
  
## <a name="build-and-test-the-code"></a>ビルドし、コードのテスト  
  
1.  ソリューションをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
2.  テキスト ファイルを作成します。 いくつかのテキストを入力し、それを選択します。  
  
3.  **ツール** メニューのをクリックして**呼び出す追加 Adornment**します。 バルーン形式は、テキスト ウィンドウの右側にある表示し、次のテキストのような文字列を含める必要があります。  
  
     YourUserName  
  
     Fourscore.  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: コンテンツの種類をファイル名拡張子にリンクさせる](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
