---
title: プロパティ、タスク一覧、出力、およびオプションの Windows を拡張 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4db9bb9101bd06921814132856fab0335a4a2530
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135548"
---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>プロパティ、タスク一覧、出力、およびオプションの Windows の拡張
Visual Studio での任意のツール ウィンドウにアクセスすることができます。 このチュートリアルは、新しいツール ウィンドウに関する情報を統合する方法を示す**オプション**ページと、新しい設定で、**プロパティ**に書き込む方法と ページで、**タスク一覧**と**出力**windows です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="create-an-extension-with-a-tool-window"></a>ツール ウィンドウと拡張機能を作成します。  
  
1.  という名前のプロジェクトを作成する**TodoList** VSIX テンプレートを使用して、という名前のカスタム ツール ウィンドウの項目テンプレートの追加**TodoWindow**です。  
  
    > [!NOTE]
    >  ツール ウィンドウで、拡張機能の作成の詳細については、次を参照してください。[ツール ウィンドウで、拡張機能の作成](../extensibility/creating-an-extension-with-a-tool-window.md)です。  
  
## <a name="set-up-the-tool-window"></a>ツール ウィンドウを設定します。  
 新しい ToDo 項目をリストに新しい項目を追加するボタンとリストに項目を表示するリスト ボックスに入力するためのテキスト ボックスを追加します。  
  
1.  TodoWindow.xaml では、ユーザー コントロールからボタン、テキスト ボックスに、[stackpanel] コントロールを削除します。  
  
    > [!NOTE]
    >  これは削除されません、 **button1_Click**イベント ハンドラーは、後の手順で再利用されます。  
  
2.  **すべての WPF コントロール**のセクションで、**ツールボックス**、ドラッグ、**キャンバス**コントロールはグリッドにします。  
  
3.  ドラッグ、 **TextBox**、**ボタン**、および**ListBox**キャンバスにします。 ように、テキスト ボックスとボタンが、同じレベルに、リスト ボックスには、次の図のように、それらの下のウィンドウの残りの要素を配置します。  
  
     ![ツール ウィンドウの終了](../extensibility/media/t5-toolwindow.png "T5 ToolWindow")  
  
4.  XAML ウィンドウで、ボタンを見つけてそのコンテンツのプロパティを設定**追加**です。 ボタン コントロールにボタンのイベント ハンドラーを追加することで再接続、`Click="button1_Click"`属性。 キャンバスのブロックは、次のようになります。  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>コンス トラクターをカスタマイズします。  
  
1.  TodoWindowControl.xaml.cs ファイルに次のコードを追加ステートメントを使用します。  
  
    ```csharp  
    using System;  
    ```  
  
2.  TodoWindow パラメーターを受け取る TodoWindowControl コンス トラクターと、TodoWindow にパブリックの参照を追加します。 コードは、次のようになります。  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  TodoWindow.cs、TodoWindow パラメーターを含める TodoWindowControl コンス トラクターを変更します。 コードは、次のようになります。  
  
    ```csharp  
    public TodoWindow() : base(null)  
    {  
        this.Caption = "TodoWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
  
         this.Content = new TodoWindowControl(this);  
    }  
    ```  
  
## <a name="create-an-options-page"></a>オプション ページを作成します。  
 内のページを使用できる、**オプション** ダイアログ ボックスのユーザーがツール ウィンドウの設定を変更できるようにします。 オプション ページを作成するには、オプションと TodoListPackage.cs または TodoListPackage.vb ファイル内のエントリを表す両方のクラスが必要です。  
  
1.  という名前のクラスを追加`ToolsOptions.cs`です。 制御クラスから継承するように<xref:Microsoft.VisualStudio.Shell.DialogPage>です。  
  
    ```csharp  
    class ToolsOptions : DialogPage  
    {  
    }  
    ```  
  
2.  次の追加ステートメントを使用します。  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
3.  このチュートリアルの [オプション] ページでは、DaysAhead をという 1 つだけのオプションを提供します。 というプライベート フィールドを追加**daysAhead**という名前のプロパティと**DaysAhead**制御クラスに。  
  
    ```csharp  
    private double daysAhead;  
  
    public double DaysAhead  
    {  
        get { return daysAhead; }  
        set { daysAhead = value; }  
    }  
    ```  
  
 これで、プロジェクトをこのオプション ページを認識させる必要があります。  
  
#### <a name="make-the-options-page-available-to-users"></a>[オプション] ページをユーザーが使用できるように  
  
1.  TodoWindowPackage.cs で追加、 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> TodoWindowPackage クラスに。  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  ProvideOptionPage コンス トラクターの最初のパラメーターは、先ほど作成した制御クラスの型です。 2 番目のパラメーターでは、"ToDo"はカテゴリの名前、**オプション** ダイアログ ボックス。 3 番目のパラメーターのサブカテゴリの名前を「全般」には、**オプション** ダイアログ ボックスの オプション ページを使用できます。 次の 2 つのパラメーターは次のリソース Id の文字列です。1 つは、カテゴリの名前と、2 つ目は、サブカテゴリの名前。 最後のパラメーターは、このページをオートメーションを使用してアクセスできるかどうかを判断します。  
  
     ユーザーがオプション ページを開くときに、次の図のようになります  
  
     ![オプション ページ](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     カテゴリに注意してください**ToDo**およびサブカテゴリ**全般**です。  
  
## <a name="make-data-available-to-the-properties-window"></a>[プロパティ] ウィンドウにデータを利用できるように  
 情報を一覧表示するにを使用できるようにするには、ToDo リストに、個々 の項目に関する情報を格納する TodoItem をという名前のクラスを作成することで。  
  
1.  という名前のクラスを追加`TodoItem.cs`です。  
  
     ツール ウィンドウは、ユーザーが利用できるが、リスト ボックス内の項目は TodoItems で表されます。 ユーザーがこれらの項目のいずれか、ボックスの一覧に選択したときに、**プロパティ**項目に関する情報がウィンドウに表示されます。  
  
     データで利用できるようにする、**プロパティ**ウィンドウで、2 つの特殊な属性を持つパブリック プロパティにデータを変換する`Description`と`Category`です。 `Description` 下部に表示されるテキスト、**プロパティ**ウィンドウです。 `Category` ときに、プロパティが表示される場所を決定、**プロパティ**でウィンドウが表示されます、 **Categorized**ビュー。 次の図に、**プロパティ**ウィンドウが**Categorized**ビュー、**名前**プロパティに、 **ToDo フィールド**カテゴリが選択すると、およびの説明、**名前**プロパティは、ウィンドウの下部に表示されます。  
  
     ![[プロパティ] ウィンドウ](../extensibility/media/t5properties.png "T5Properties")  
  
2.  次の追加 TodoItem.cs ファイル ステートメントを使用します。  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  追加、`public`クラス宣言にアクセス修飾子。  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     名前と DueDate、2 つのプロパティを追加します。 UpdateList() と CheckForErrors() を後で実行します。  
  
    ```csharp  
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
  
4.  ユーザー コントロールへのプライベートの参照を追加します。 ユーザー コントロールと ToDo 項目の名前を受け取るコンス トラクターを追加します。 DaysAhead の値が見つかりません、オプション ページのプロパティを取得します。  
  
    ```csharp  
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
  
5.  のインスタンス、`TodoItem`クラスは、リスト ボックスとリスト ボックスが呼び出されます、`ToString`オーバー ロードする必要があります、関数、`ToString`関数。 コンス トラクターの後およびクラスの末尾の前に、次のコードを TodoItem.cs に追加します。  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  TodoWindowControl.xaml.cs、TodoWindowControl クラスにスタブ メソッドを追加、`CheckForError`と`UpdateList`メソッドです。 ProcessDialogChar 後と前のファイルの末尾には、それらを配置します。  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     `CheckForError`メソッドを親オブジェクトに同じ名前を持つメソッドを呼び出すし、そのメソッドは、エラーが発生し、それらを正しく処理するかどうかを確認します。 `UpdateList`メソッドは、親コントロールのリスト ボックスで、更新以外のときに、メソッドが呼び出されます、`Name`と`DueDate`このクラスの変更でのプロパティです。 これらは後で実装されます。  
  
## <a name="integrate-into-the-properties-window"></a>[プロパティ] ウィンドウに統合します。  
 関連付けられたはリスト ボックスを管理するコードを記述できるよう、**プロパティ**ウィンドウです。  
  
 ボタンを変更する必要があります、テキスト ボックスを読み取り、a TodoItem を作成するハンドラーをクリックし、リスト ボックスに追加します。  
  
1.  既存の置換`button1_Click`新しい TodoItem を作成し、リスト ボックスに追加するコードを持つ関数です。 後で定義されている TrackSelection() を呼び出します。  
  
    ```csharp  
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
  
2.  デザイン ビューでは、リスト ボックス コントロールを選択します。 **プロパティ**ウィンドウをクリックして、**イベント ハンドラー**  ボタンをクリックし、SelectionChanged イベントを確認します。 テキスト ボックスで塗りつぶし**listBox_SelectionChanged**です。 これにより、SelectionChanged ハンドラーのスタブが追加され、イベントに割り当てます。  
  
3.  TrackSelection() メソッドを実装します。 取得する必要がありますので、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>行う必要があるサービス、 <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> TodoWindowControl からアクセスします。 TodoWindow クラスに次のメソッドを追加します。  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  次の追加 TodoWindowControl.xaml.cs にステートメントを使用します。  
  
    ```csharp  
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
  
6.  ここで、入力との統合を提供する TrackSelection 関数、**プロパティ**ウィンドウです。 この関数は、ユーザーがリスト ボックスに項目を追加またはリスト ボックス内の項目をクリックしたときに呼び出されます。 リスト ボックスの内容を SelectionContainer に追加しを SelectionContainer を渡します、**プロパティ**ウィンドウの<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>イベント ハンドラー。 TrackSelection サービスは、ユーザー インターフェイス (UI) で選択したオブジェクトを追跡し、そのプロパティが表示されます。  
  
    ```csharp  
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
  
     保持されているクラスを**プロパティ**ウィンドウを使用して、統合することができます、**プロパティ**ツール ウィンドウを持つウィンドウです。 ユーザーがツール ウィンドウのリスト ボックス内の項目をクリックしたときに、**プロパティ**ウィンドウも更新する必要があります。 同様に、ユーザーが変更された時点での ToDo 項目、**プロパティ**ウィンドウで、関連付けられた項目を更新する必要があります。  
  
7.  ここで、TodoWindowControl.xaml.cs で UpdateList 関数のコードの残りの部分を追加します。 削除して、リスト ボックスから変更後の TodoItem を再追加が必要があります。  
  
    ```csharp  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8.  コードをテストします。 プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
9. 開く、**ツール/オプション**ページ。 左側のウィンドウで、ToDo カテゴリが表示されます。 カテゴリは、アルファベット順で表示されます、Ts の下にあるようです。  
  
10. Todo のオプション ページで、DaysAhead プロパティに設定が表示されます**0**します。 変更して**2**です。  
  
11. ビュー/その他のウィンドウ メニューを開いている**TodoWindow**です。 型**EndDate** 、テキスト ボックスに**追加**です。  
  
12. リスト ボックスでは、2 つの日の後に今日より後の日付が表示されます。  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>テキスト出力ウィンドウおよびタスクのリストに項目を追加します。  
 **タスク一覧**、[タスク] タイプの新しいオブジェクトを作成しするには、そのタスク オブジェクトを追加する、**タスク一覧**の Add メソッドを呼び出すことによってです。 書き込む、**出力**ウィンドウで、ウィンドウのオブジェクトを取得するには、その GetPane メソッドを呼び出すし、するメソッドを呼び出す、OutputString ウィンドウのオブジェクトの。  
  
1.  TodoWindowControl.xaml.cs、内で、`button1_Click`メソッドを取得するコードを追加、**全般**のペイン、**出力**ウィンドウ (既定値) と書き込みをします。 メソッドは、次のようになります。  
  
    ```csharp  
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
  
2.  タスク リストに項目を追加する必要があります、TodoWindowControl クラスに入れ子になったクラスを追加します。 派生する必要があります、入れ子になったクラス<xref:Microsoft.VisualStudio.Shell.TaskProvider>です。 TodoWindowControl クラスの末尾に次のコードを追加します。  
  
    ```csharp  
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]  
    public class TodoWindowTaskProvider : TaskProvider  
    {  
        public TodoWindowTaskProvider(IServiceProvider sp)  
            : base(sp)  
        {  
        }  
    }  
    ```  
  
3.  次に TodoWindowControl クラス TodoTaskProvider への参照をプライベートおよび CreateProvider() メソッドを追加します。 コードは、次のようになります。  
  
    ```csharp  
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
  
    ```csharp  
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
  
    ```csharp  
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
  
3.  テキスト ボックスに情報を入力し、をクリックして**追加**です。  
  
     Due date 今日がリスト ボックスに追加された後、2 日間です。 エラーは発生せず、および**タスク一覧**(**を表示する]、[タスク一覧**) エントリはありません。  
  
4.  設定を変更するようになりました、**ツール/オプション/ToDo**からページ**2**に**0**します。  
  
5.  内の他の情報を入力、 **TodoWindow**  をクリックし、**追加**もう一度です。 これは、場合、トリガー内のエントリとエラー、**タスク一覧**です。  
  
     項目を追加すると、最初の日付は、ここでさらに 2 日間に設定されます。  
  
6.  **ビュー**  メニューのをクリックして**出力**を開くには、**出力**ウィンドウです。  
  
     確認するたびに項目を追加することでメッセージが表示されます、**タスク一覧**ウィンドウです。  
  
7.  リスト ボックス内の項目のいずれかをクリックします。  
  
     **プロパティ**ウィンドウには、項目の 2 つのプロパティが表示されます。  
  
8.  プロパティのいずれかを変更し、ENTER キーを押します。  
  
     リスト ボックス内にアイテムを更新します。