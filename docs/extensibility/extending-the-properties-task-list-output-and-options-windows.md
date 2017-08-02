---
title: "プロパティ、タスク一覧、出力、およびオプションの Windows の拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
caps.latest.revision: 37
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
ms.openlocfilehash: 75937e3f2cf1d3fa9c5c78de8b7df5f8869ef49e
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>プロパティ、タスク一覧、出力、およびオプションの Windows の拡張
Visual Studio でのツール ウィンドウを表示できます。 このチュートリアルでは、新しいツール ウィンドウに関する情報を統合する方法**オプション**ページと、新しい設定で、**プロパティ** ページとを記述する方法、**タスク一覧**と**出力**windows です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="create-an-extension-with-a-tool-window"></a>ツール ウィンドウでの拡張機能を作成します。  
  
1.  という名前のプロジェクトを作成する**TodoList** VSIX のテンプレートを使用し、という名前のカスタム ツール ウィンドウの項目テンプレートを追加**TodoWindow**します。  
  
    > [!NOTE]
    >  ツール ウィンドウで拡張機能の作成の詳細については、次を参照してください。[ツール ウィンドウで、拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)です。  
  
## <a name="set-up-the-tool-window"></a>ツール ウィンドウを設定します。  
 新しい ToDo 項目をリストに新しい項目を追加 ボタンをクリックし、リストに項目を表示するリスト ボックスに入力するためのテキスト ボックスを追加します。  
  
1.  TodoWindow.xaml では、ユーザー コントロールから、ボタン、テキスト ボックスと StackPanel コントロールを削除します。  
  
    > [!NOTE]
    >  これは削除されません、 **button1_Click**イベント ハンドラーは、後の手順で再利用されます。  
  
2.  **すべての WPF コントロール**のセクションで、**ツールボックス**、ドラッグ、**キャンバス**コントロールはグリッドにします。  
  
3.  ドラッグ、 ** テキスト ボックス**、**ボタン**、および**ListBox**をキャンバスにします。 テキスト ボックスとボタンが同じレベルには、リスト ボックスには、次の図に示すように、それらの下のウィンドウの残りの要素を配置します。  
  
     ![ツール ウィンドウを終了](~/extensibility/media/t5-toolwindow.png "T5 ツール ウィンドウ")  
  
4.  XAML ウィンドウで、ボタンを見つけて、コンテンツのプロパティを設定**追加**します。 Button コントロールにボタンのイベント ハンドラーを追加することで再接続、`Click="button1_Click"`属性です。 キャンバスのブロックは、次のようになります。  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>コンス トラクターをカスタマイズします。  
  
1.  TodoWindowControl.xaml.cs ファイルに次のコードを追加ステートメントを使用します。  
  
    ```c#  
    using System;  
    ```  
  
2.  TodoWindow パラメーターを受け取る TodoWindowControl コンス トラクターと、TodoWindow にパブリックの参照を追加します。 コードは、次のようになります。  
  
    ```c#  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  TodoWindow.cs では、TodoWindowControl TodoWindow パラメーターが含まれてコンス トラクターを変更します。 コードは、次のようになります。  
  
    ```c#  
    public TodoWindow() : base(null)  
    {  
        this.Caption = "TodoWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
  
         this.Content = new TodoWindowControl(this);  
    }  
    ```  
  
## <a name="create-an-options-page"></a>オプション ページを作成します。  
 ページを指定することができます、**オプション** ダイアログ ボックスのユーザーがツール ウィンドウの設定を変更できるようにします。 オプション ページを作成するには、オプションと TodoListPackage.cs または TodoListPackage.vb ファイル内のエントリを表す両方のクラスが必要です。  
  
1.  という名前のクラスを追加`ToolsOptions.cs`します。 <xref:Microsoft.VisualStudio.Shell.DialogPage>。</xref:Microsoft.VisualStudio.Shell.DialogPage>から継承制御クラスします。  
  
    ```c#  
    class ToolsOptions : DialogPage  
    {  
    }  
    ```  
  
2.  次の追加ステートメントを使用します。  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
3.  このチュートリアルで [オプション] ページには、1 つだけのオプションが DaysAhead という名前が提供されます。 というプライベート フィールドを追加**daysAhead**という名前のプロパティと**DaysAhead**制御クラスにします。  
  
    ```c#  
    private double daysAhead;  
  
    public double DaysAhead  
    {  
        get { return daysAhead; }  
        set { daysAhead = value; }  
    }  
    ```  
  
 これで、プロジェクトをこのオプション ページを認識させる必要があります。  
  
#### <a name="make-the-options-page-available-to-users"></a>[オプション] ページをユーザーが使用できるように  
  
1.  TodoWindowPackage.cs で追加、 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>TodoWindowPackage クラス:</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
    ```c#  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  ProvideOptionPage コンス トラクターの最初のパラメーターは、先ほど作成した制御クラスの型です。 2 番目のパラメーターでは、"ToDo"は、[カテゴリの名前、**オプション**] ダイアログ ボックス。 3 番目のパラメーターのサブカテゴリの名前を「全般」には、**オプション** ダイアログ ボックスの オプション ページを使用できます。 次の&2; つのパラメーターは次のリソース Id の文字列です。1 つ目は、カテゴリの名前で、2 番目は、サブカテゴリの名前です。 最後のパラメーターは、このページをオートメーションを使用してアクセスできるかどうかを決定します。  
  
     ユーザーが、[オプション] ページを開いたときは、次の図ようになります。  
  
     ![オプション ページ](~/extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     カテゴリに注意してください**ToDo**とサブカテゴリ**全般**します。  
  
## <a name="make-data-available-to-the-properties-window"></a>[プロパティ] ウィンドウにデータを利用できるように  
 一覧の情報を使用できるようにするには ToDo リスト内の個々 の項目に関する情報を格納する TodoItem という名前のクラスを作成することで。  
  
1.  という名前のクラスを追加`TodoItem.cs`します。  
  
     ツール ウィンドウは、ユーザーが利用できるが、リスト ボックス内の項目は TodoItems で表されます。 ユーザーが、リスト ボックスにこれらの項目のいずれかを選択すると、**プロパティ**ウィンドウの項目についての情報が表示されます。  
  
     データで利用できるようにする、**プロパティ**ウィンドウで、次の&2; つの特別な属性を持つパブリック プロパティにデータを変換する`Description`と`Category`です。 `Description`下部に表示されるテキスト、**プロパティ**ウィンドウです。 `Category`ときに、プロパティが表示される場所を決定する、**プロパティ**でウィンドウが表示されます、**項目別**ビューです。 次の図に、**プロパティ**期間が**項目別**ビュー、**名**プロパティに、 **ToDo フィールド**カテゴリを選択するとの説明、**名前**プロパティは、ウィンドウの下部に表示されます。  
  
     ![[プロパティ] ウィンドウ](~/extensibility/media/t5properties.png "T5Properties")  
  
2.  次の追加ステートメントを TodoItem.cs ファイルを使用します。  
  
    ```c#  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  追加、`public`クラス宣言に、アクセス修飾子です。  
  
    ```c#  
    public class TodoItem  
    {  
    }  
    ```  
  
     2 つのプロパティ名と DueDate を追加します。 UpdateList() と CheckForErrors() を後で実行します。  
  
    ```c#  
    public class TodoItem  
    {  
        private TodoWindowControl parent;  
        private string name;  
        [Description("Name of the ToDo item")]  
        [Category("ToDo Fields")]  
        public string Name  
        {  
            get { return name; }  
            set  
            {  
                name = value;  
                parent.UpdateList(this);  
            }  
        }  
  
        private DateTime dueDate;  
        [Description("Due date of the ToDo item")]  
        [Category("ToDo Fields")]  
        public DateTime DueDate  
        {  
            get { return dueDate; }  
            set  
            {  
                dueDate = value;  
                parent.UpdateList(this);  
                parent.CheckForErrors();  
            }  
        }  
    }  
    ```  
  
4.  ユーザー コントロールへの参照をプライベートを追加します。 ユーザー コントロールおよびこの ToDo 項目の名前を取得するコンス トラクターを追加します。 DaysAhead の値を検索するには、オプション ページのプロパティを取得します。  
  
    ```c#  
    private TodoWindowControl parent;  
  
    public TodoItem(TodoWindowControl control, string itemName)  
    {  
        parent = control;  
        name = itemName;  
        dueDate = DateTime.Now;  
  
        double daysAhead = 0;  
        IVsPackage package = parent.parent.Package as IVsPackage;  
        if (package != null)  
        {  
            object obj;  
            package.GetAutomationObject("ToDo.General", out obj);  
  
            ToolsOptions options = obj as ToolsOptions;  
            if (options != null)  
            {  
                daysAhead = options.DaysAhead;  
            }  
        }  
  
        dueDate = dueDate.AddDays(daysAhead);  
    }  
    ```  
  
5.  のインスタンス、`TodoItem`クラスは、リスト ボックスとリスト ボックスが呼び出されます、`ToString`関数をオーバー ロードする必要があります、`ToString`関数です。 コンス トラクターとクラスの末尾の間には、次のコードを TodoItem.cs を追加します。  
  
    ```c#  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  TodoWindowControl.xaml.cs で TodoWindowControl クラスにスタブ メソッドを追加、`CheckForError`と`UpdateList`メソッドです。 ProcessDialogChar 後、ファイルの末尾の前に配置します。  
  
    ```c#  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     `CheckForError`メソッドは、親オブジェクトで同じ名前を持つメソッドを呼び出しますおり、そのメソッドは、すべてのエラーが発生し、適切に処理するかどうかを確認します。 `UpdateList`メソッドは、親コントロールのリスト ボックスで、更新、ときに、メソッドが呼び出された、`Name`と`DueDate`このクラスの変更のプロパティです。 これらは後で実装されます。  
  
## <a name="integrate-into-the-properties-window"></a>[プロパティ] ウィンドウに統合します。  
 関連付けられている、リスト ボックスを管理するコードを記述、**プロパティ**ウィンドウです。  
  
 ボタンを変更する必要があります、テキスト ボックスを読み取り、作成、TodoItem にハンドラーをクリックし、リスト ボックスに追加します。  
  
1.  既存`button1_Click`関数を新しい TodoItem を作成し、リスト ボックスに追加するコードです。 後で定義されている TrackSelection() を呼び出します。  
  
    ```c#  
    private void button1_Click(object sender, RoutedEventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  デザイン ビューでは、ListBox コントロールを選択します。 **プロパティ**ウィンドウをクリックして、**イベント ハンドラー**  ボタンをクリックし、SelectionChanged イベントを確認します。 テキスト ボックスに入力**listBox_SelectionChanged**します。 これを行うと、SelectionChanged ハンドラーのスタブを追加して、イベントに割り当てます。  
  
3.  TrackSelection() メソッドを実装します。 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>を取得する必要がある<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>する必要がある、サービス、 <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A>、TodoWindowControl からアクセスできる</xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A></xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>。</xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> TodoWindow クラスに次のメソッドを追加します。  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  次の追加 TodoWindowControl.xaml.cs にステートメントを使用します。  
  
    ```c#  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  SelectionChanged ハンドラーを次のように入力します。  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6.  これで、入力との統合を提供する TrackSelection 関数、**プロパティ**ウィンドウです。 ユーザーがリスト ボックスに項目を追加またはリスト ボックスに項目をクリックしたときは、この関数が呼び出されます。 SelectionContainer をリスト ボックスの内容を追加しを SelectionContainer、**プロパティ**ウィンドウの<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>イベント ハンドラー</xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 。 TrackSelection サービスは、ユーザー インターフェイス (UI) で選択したオブジェクトを追跡し、そのプロパティが表示されます。  
  
    ```c#  
    private SelectionContainer mySelContainer;  
    private System.Collections.ArrayList mySelItems;  
    private IVsWindowFrame frame = null;  
  
    private void TrackSelection()  
    {  
        if (frame == null)  
        {  
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;  
            if (shell != null)  
            {  
                var guidPropertyBrowser = new  
                Guid(ToolWindowGuids.PropertyBrowser);  
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,  
                ref guidPropertyBrowser, out frame);  
            }  
        }  
        if (frame != null)  
            {  
                frame.Show();  
            }  
        if (mySelContainer == null)  
        {  
            mySelContainer = new SelectionContainer();  
        }  
  
        mySelItems = new System.Collections.ArrayList();  
  
        var selected = listBox.SelectedItem as TodoItem;  
        if (selected != null)  
        {  
            mySelItems.Add(selected);  
        }  
  
        mySelContainer.SelectedObjects = mySelItems;  
  
        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))  
                                as ITrackSelection;  
        if (track != null)  
        {  
            track.OnSelectChange(mySelContainer);  
        }  
    }  
    ```  
  
     クラスが作成できたが、**プロパティ**ウィンドウを使用して、統合することができます、**プロパティ**ツール ウィンドウを持つウィンドウです。 ユーザーがツール ウィンドウのリスト ボックス内の項目をクリックすると、**プロパティ**ウィンドウに更新する必要があります。 同様に、ユーザーが内の ToDo 項目を変更すると、**プロパティ**ウィンドウで、関連付けられているアイテムを更新する必要があります。  
  
7.  これで、TodoWindowControl.xaml.cs で UpdateList 関数のコードの残りの部分を追加します。 削除して、再、リスト ボックスから変更された TodoItem を追加する必要があります。  
  
    ```c#  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8.  コードをテストします。 プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
9. 開いている、**ツール/オプション**ページです。 左側のウィンドウで、[ToDo] カテゴリが表示されます。 カテゴリはアルファベット順で表示されます、そのため、Ts を調べます。  
  
10. Todo オプション ページで、DaysAhead プロパティに設定を確認する必要があります**0**です。 変更して**2**します。  
  
11. ビュー/その他のウィンドウ メニューを開いている**TodoWindow**します。 型**EndDate**  をクリックし、テキスト ボックスに**追加**します。  
  
12. リスト ボックスでは、2 つの日の後に今日より後の日付が表示されます。  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>[出力] ウィンドウとタスクのリストに項目にテキストを追加します。  
 **タスク一覧**、[タスク] タイプの新しいオブジェクトを作成し、その Task オブジェクトを追加、**タスク一覧**の Add メソッドを呼び出すことによってです。 書き込む、**出力**ウィンドウで、ウィンドウ オブジェクトを取得するには、その GetPane メソッドを呼び出すし、ウィンドウ オブジェクトの OutputString メソッドを呼び出します。  
  
1.  TodoWindowControl.xaml.cs、で、`button1_Click`メソッドを取得するコードを追加、**全般的な**のウィンドウ、**出力**ウィンドウ (既定値) と書き込みをします。 このメソッドは、次のようになります。  
  
    ```c#  
    private void button1_Click(object sender, EventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
  
            var outputWindow = parent.GetVsService(  
                typeof(SVsOutputWindow)) as IVsOutputWindow;  
            IVsOutputWindowPane pane;  
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;  
            outputWindow.GetPane(ref guidGeneralPane, out pane);  
            if (pane != null)  
            {  
                 pane.OutputString(string.Format(  
                    "To Do item created: {0}\r\n",  
                 item.ToString()));  
        }  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  必要なタスクのリストに項目を追加するために、TodoWindowControl クラスに入れ子になったクラスを追加します。 入れ子になったクラスが<xref:Microsoft.VisualStudio.Shell.TaskProvider>。</xref:Microsoft.VisualStudio.Shell.TaskProvider>から派生する必要があります。 TodoWindowControl クラスの末尾に次のコードを追加します。  
  
    ```c#  
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]  
    public class TodoWindowTaskProvider : TaskProvider  
    {  
        public TodoWindowTaskProvider(IServiceProvider sp)  
            : base(sp)  
        {  
        }  
    }  
    ```  
  
3.  次に TodoWindowControl クラス TodoTaskProvider への参照をプライベートと CreateProvider() メソッドを追加します。 コードは、次のようになります。  
  
    ```c#  
    private TodoWindowTaskProvider taskProvider;  
    private void CreateProvider()  
    {  
        if (taskProvider == null)  
        {  
            taskProvider = new TodoWindowTaskProvider(parent);  
            taskProvider.ProviderName = "To Do";  
        }  
    }  
    ```  
  
4.  TodoWindowControl クラスに、タスクの一覧を消去、ClearError() と ReportError() で、タスク一覧にエントリを追加を追加します。  
  
    ```c#  
    private void ClearError()  
    {  
        CreateProvider();  
        taskProvider.Tasks.Clear();  
    }  
    private void ReportError(string p)  
    {  
        CreateProvider();  
        var errorTask = new Task();  
        errorTask.CanDelete = false;  
        errorTask.Category = TaskCategory.Comments;  
        errorTask.Text = p;  
  
        taskProvider.Tasks.Add(errorTask);  
  
        taskProvider.Show();  
  
        var taskList = parent.GetVsService(typeof(SVsTaskList))  
            as IVsTaskList2;  
        if (taskList == null)  
        {  
            return;  
        }  
  
        var guidProvider = typeof(TodoWindowTaskProvider).GUID;  
         taskList.SetActiveProvider(ref guidProvider);  
    }  
    ```  
  
5.  次のように CheckForErrors メソッドを実装するようになりました。  
  
    ```c#  
    public void CheckForErrors()  
    {  
        foreach (TodoItem item in listBox.Items)  
        {  
            if (item.DueDate < DateTime.Now)  
            {  
                ReportError("To Do Item is out of date: "  
                    + item.ToString());  
            }  
        }  
    }  
    ```  
  
## <a name="trying-it-out"></a>試してみる  
  
1.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
2.  開く、TodoWindow (**ビュー/その他の Windows/TodoWindow**)。  
  
3.  テキスト ボックスに情報を入力し、**追加**します。  
  
     期日今日は、リスト ボックスに追加した後、2 日間です。 エラーは発生せず、および**タスク一覧**(**を表示する]、[タスク一覧**) エントリはありません。  
  
4.  現在の設定を変更、**ツール/オプション/ToDo**からページ**2**に**0**です。  
  
5.  内の他の何か入力、 **TodoWindow**  をクリックし、**追加**再度します。 これは、場合、トリガー内のエントリをエラー、**タスク一覧**します。  
  
     項目を追加すると、最初の日付は、ここでさらに 2 日間に設定されます。  
  
6.  **ビュー**  メニューのをクリックして**出力**を開くには、**出力**ウィンドウです。  
  
     確認するたびに項目を追加することで、メッセージが表示されます、**タスク一覧**ウィンドウです。  
  
7.  リスト ボックス内の項目のいずれかをクリックします。  
  
     **プロパティ**ウィンドウには、アイテムの&2; つのプロパティが表示されます。  
  
8.  プロパティのいずれかを変更し、ENTER キーを押します。  
  
     リスト ボックス内の項目を更新します。
