---
title: プロパティ、タスク一覧、出力、およびオプションの Windows の拡張 |Microsoft Docs
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
ms.openlocfilehash: ad9cd6c3356d38184b24a7e2ecfa06ca954bfbb0
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499878"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>プロパティ、タスク一覧、出力、およびオプションの windows を拡張します。
Visual Studio のいずれかのツール ウィンドウにアクセスできます。 このチュートリアルは、新しいツール ウィンドウに関する情報を統合する方法を示す**オプション**ページと、新しい設定で、**プロパティ** ページで、またに書き込む方法、**タスク一覧**と**出力**windows。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)します。  
  
## <a name="create-an-extension-with-a-tool-window"></a>ツール ウィンドウでの拡張機能を作成します。  
  
1.  という名前のプロジェクトを作成する**TodoList** VSIX のテンプレートを使用して、という名前のカスタム ツール ウィンドウの項目テンプレートを追加**TodoWindow**します。  
  
    > [!NOTE]
    >  ツール ウィンドウで拡張機能の作成の詳細については、次を参照してください。[ツール ウィンドウで拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)します。  
  
## <a name="set-up-the-tool-window"></a>ツール ウィンドウを設定します。  
 新しい ToDo 項目をリストに新しい項目を追加するためのボタンと、リストに項目を表示するリスト ボックスに入力するためのテキスト ボックスを追加します。  
  
1.  *TodoWindow.xaml*、ユーザー コントロールからボタン、テキスト ボックスに、StackPanel コントロールを削除します。  
  
    > [!NOTE]
    >  これは削除されません、 **button1_Click**イベント ハンドラーは、後の手順で再利用します。  
  
2.  **すべての WPF コントロール**のセクション、**ツールボックス**、ドラッグ、**キャンバス**グリッド コントロール。  
  
3.  ドラッグ、 **TextBox**、**ボタン**と**ListBox**をキャンバスにします。 ように、テキスト ボックスとボタンが、同じレベルにして、リスト ボックスには、次の図のように、その下のウィンドウの残りの要素を配置します。  
  
     ![ツール ウィンドウを終了](../extensibility/media/t5-toolwindow.png "T5 ToolWindow")  
  
4.  XAML ウィンドウで、ボタンし、そのコンテンツのプロパティを設定**追加**します。 ボタン コントロールにボタンのイベント ハンドラーを追加することで再接続を`Click="button1_Click"`属性。 このようキャンバス ブロックになります。  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
### <a name="customize-the-constructor"></a>コンス トラクターをカスタマイズします。  
  
1.  *TodoWindowControl.xaml.cs*ファイルに追加し、次のステートメントを使用します。  
  
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
  
3.  *TodoWindow.cs*、TodoWindow パラメーターを含める TodoWindowControl コンス トラクターを変更します。 コードは、次のようになります。  
  
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
 内のページを行うことができます、**オプション** ダイアログ ボックスのユーザーがツール ウィンドウの設定を変更できるようにします。 オプションと内のエントリを記述する、クラスにもオプション ページを作成する必要があります、 *TodoListPackage.cs*または*TodoListPackage.vb*ファイル。  
  
1.  という名前のクラスを追加`ToolsOptions.cs`します。 ように、`ToolsOptions`クラスから継承する<xref:Microsoft.VisualStudio.Shell.DialogPage>します。  
  
    ```csharp  
    class ToolsOptions : DialogPage  
    {  
    }  
    ```  
  
2.  次の追加ステートメントを使用します。  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
3.  このチュートリアルでは、[オプション] ページでは、DaysAhead という名前の 1 つだけのオプションを提供します。 というプライベート フィールドを追加**daysAhead**という名前のプロパティと**DaysAhead**を`ToolsOptions`クラス。  
  
    ```csharp  
    private double daysAhead;  
  
    public double DaysAhead  
    {  
        get { return daysAhead; }  
        set { daysAhead = value; }  
    }  
    ```  
  
 これで、プロジェクトをこのオプション ページの対応する必要があります。  
  
### <a name="make-the-options-page-available-to-users"></a>[オプション] ページをユーザーが利用できるように  
  
1.  *TodoWindowPackage.cs*、追加、<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>を`TodoWindowPackage`クラス。  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  ProvideOptionPage コンス トラクターの最初のパラメーターは、クラスの型`ToolsOptions`、先ほど作成しました。 2 番目のパラメーターでは、"ToDo"はカテゴリの名前、**オプション** ダイアログ ボックス。 3 番目のパラメーターのサブカテゴリの名前を"General"には、**オプション** ダイアログ ボックスの オプション ページが提供されます。 次の 2 つのパラメーターは文字列以外のリソース Id です。1 つは、カテゴリの名前と、2 つ目は、サブカテゴリの名前です。 最後のパラメーターは、オートメーションを使用してこのページにアクセスできるかどうかを判断します。  
  
     ユーザーは、[オプション] ページが開いたら、次の図のようになります。  
  
     ![オプション ページ](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     カテゴリ**ToDo**とサブカテゴリ**全般**します。  
  
## <a name="make-data-available-to-the-properties-window"></a>データ プロパティ ウィンドウに使用できるように  
 という名前のクラスを作成してで ToDo リストの情報を利用できる`TodoItem`ToDo リストの個々 の項目に関する情報を格納します。  
  
1.  という名前のクラスを追加`TodoItem.cs`します。  
  
     ツール ウィンドウがユーザーに利用できる場合、リスト ボックス内の項目は TodoItems によって表されます。 ユーザーがリスト ボックスに、これらの項目のいずれかを選択すると、**プロパティ**項目に関する情報がウィンドウに表示されます。  
  
     データで使用できるように、**プロパティ**ウィンドウを 2 つの特殊な属性を持つパブリック プロパティにデータを有効にする`Description`と`Category`します。 `Description` 下部に表示されるテキスト、**プロパティ**ウィンドウ。 `Category` ときに、プロパティが表示される場所を決定する、**プロパティ**でウィンドウが表示されます、 **Categorized**ビュー。 次の図に、**プロパティ**ウィンドウが**項目別**ビュー、**名前**プロパティ、 **ToDo フィールド**カテゴリは、選択するの説明と、**名前**プロパティは、ウィンドウの下部に表示されます。  
  
     ![[プロパティ] ウィンドウ](../extensibility/media/t5properties.png "T5Properties")  
  
2.  次の追加のステートメントを使用して、 *TodoItem.cs*ファイル。  
  
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
  
     2 つのプロパティを追加`Name`と`DueDate`します。 `UpdateList()`と`CheckForErrors()`以降。  
  
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
  
4.  ユーザー コントロールへの参照をプライベートを追加します。 ユーザー コントロールと ToDo 項目の名前を取得するコンス トラクターを追加します。 値を検索する`daysAhead`、オプション ページのプロパティを取得します。  
  
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
  
5.  のインスタンス、`TodoItem`クラスは、リスト ボックスに格納され、ListBox が呼び出されます、`ToString`オーバー ロードする必要があります、関数、`ToString`関数。 次のコードを追加*TodoItem.cs*、コンス トラクターの後およびクラスの終了前にします。  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  *TodoWindowControl.xaml.cs*、スタブ メソッドを追加、`TodoWindowControl`クラス、`CheckForError`と`UpdateList`メソッド。 ProcessDialogChar 後と前のファイルの末尾には、それらを配置します。  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     `CheckForError`メソッドは、親オブジェクトで同じ名前を持つメソッドを呼び出すし、そのメソッドには、すべてのエラーが発生し、適切に処理するかどうかがチェックされます。 `UpdateList`メソッドは、親コントロールのリスト ボックスで、更新、ときに、メソッドが呼び出されます。、`Name`と`DueDate`プロパティでこのクラスの変更。 これらは後で実装されます。  
  
## <a name="integrate-into-the-properties-window"></a>[プロパティ] ウィンドウに統合します。  
 関連付けられるはリスト ボックスを管理するコードを記述するようになりました、**プロパティ**ウィンドウ。  
  
 ボタンを変更する必要があります、テキスト ボックスを読み取り、作成、TodoItem をハンドラーをクリックし、リスト ボックスに追加します。  
  
1.  既存`button1_Click`関数のコードを新しい TodoItem を作成し、リスト ボックスに追加します。 呼び出す`TrackSelection()`、後で定義されます。  
  
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
  
2.  デザイン ビューでは、ListBox コントロールを選択します。 **プロパティ**ウィンドウをクリックして、**イベント ハンドラー**ボタンをクリックし、検索、 **SelectionChanged**イベント。 テキスト ボックスで塗りつぶし**listBox_SelectionChanged**します。 これにより、SelectionChanged ハンドラーのスタブを追加し、イベントに割り当てられます。  
  
3.  `TrackSelection()` メソッドを実装します。 取得する必要がありますので、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 、サービスが行う必要があります、 <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> TodoWindowControl によってアクセスできます。 次のメソッドを追加、`TodoWindow`クラス。  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  以下を追加するステートメントを使用して*TodoWindowControl.xaml.cs*:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  次のように、SelectionChanged ハンドラーに入力します。  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6.  ここで、入力との統合を提供する TrackSelection 関数、**プロパティ**ウィンドウ。 この関数は、ユーザーがリスト ボックスに項目を追加またはリスト ボックス内の項目をクリックしたときに呼び出されます。 リスト ボックスの内容を SelectionContainer に追加しを SelectionContainer を渡します、**プロパティ**ウィンドウの<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>イベント ハンドラー。 TrackSelection サービスは、ユーザー インターフェイス (UI) で選択したオブジェクトを追跡し、それらのプロパティを表示します。  
  
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
  
     クラスが用意できたが、**プロパティ**ウィンドウを使用できる、統合することができます、**プロパティ**ツール ウィンドウのウィンドウ。 ユーザーがツール ウィンドウで、リスト ボックス内の項目をクリックすると、**プロパティ**ウィンドウを適宜更新する必要があります。 ユーザーが ToDo 項目に変更されたときに同様に、**プロパティ**ウィンドウで、関連付けられているアイテムを更新する必要があります。  
  
7.  UpdateList 関数コードの残りの部分を次に、追加*TodoWindowControl.xaml.cs*します。 削除して、リスト ボックスから変更後の TodoItem を再追加が必要があります。  
  
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
  
9. 開く、**ツール** > **オプション**ページ。 左側のウィンドウで、[ToDo] カテゴリが表示されます。 アルファベット順でカテゴリの一覧、したがって、Ts の下になります。  
  
10. **Todo**オプション ページに、表示する必要があります、`DaysAhead`プロパティに設定**0**します。 変更して**2**します。  
  
11. **ビュー/その他の Windows** ] メニューの [open **TodoWindow**します。 型**EndDate**テキスト ボックスをクリックします**追加**します。  
  
12. リスト ボックスでは、2 つの日の後に今日より後の日付が表示されます。  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>テキスト出力ウィンドウとタスク リストに項目を追加します。  
 **タスク一覧**、タスクの種類の新しいオブジェクトを作成しするには、そのタスク オブジェクトを追加し、**タスク一覧**を呼び出してその`Add`メソッド。 書き込む、**出力**呼び出しのウィンドウで、その`GetPane`ウィンドウのオブジェクトとし、取得するメソッドを呼び出す、`OutputString`ウィンドウ オブジェクトのメソッド。  
  
1.  *TodoWindowControl.xaml.cs*で、`button1_Click`メソッドを取得するコードを追加、**全般**のウィンドウ、**出力**(つまり、既定値) ウィンドウと書き込みを。 メソッドは、このようになります。  
  
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
  
2.  タスク一覧に項目を追加するには、TodoWindowControl クラスに入れ子になったクラスを追加します。 入れ子になったクラスから派生する必要がある<xref:Microsoft.VisualStudio.Shell.TaskProvider>します。 末尾に次のコードを追加、`TodoWindowControl`クラス。  
  
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
  
3.  次にプライベートの参照を追加`TodoTaskProvider`と`CreateProvider()`メソッドを`TodoWindowControl`クラス。 コードは、次のようになります。  
  
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
  
4.  追加`ClearError()`、タスクの一覧をクリアし、`ReportError()`に、タスク リストにエントリを追加する、`TodoWindowControl`クラス。  
  
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
  
5.  今すぐ実装、`CheckForErrors`メソッドは、次のようにします。  
  
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
  
## <a name="try-it-out"></a>試してみる  
  
1.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
2.  開く、 **TodoWindow** (**ビュー** > **他の Windows** > **TodoWindow**)。  
  
3.  テキスト ボックスに情報を入力し、**追加**します。  
  
     期日 2 日後、今日は、リスト ボックスに追加されます。 エラーは発生せず、および**タスク一覧**(**ビュー** > **タスク一覧**) のエントリはありません。  
  
4.  設定を今すぐ変更、**ツール** > **オプション** > **ToDo**からページ**2** に**0**します。  
  
5.  内の他の何か入力、 **TodoWindow**し**追加**もう一度です。 これをトリガー内のエントリとエラー、**タスク一覧**します。  
  
     項目を追加すると、最初の日付は、ここでさらに 2 日間に設定されます。  
  
6.  **ビュー**  メニューのをクリックして**出力**を開く、**出力**ウィンドウ。  
  
     確認するたびに項目を追加することでメッセージが表示されます、**タスク一覧**ウィンドウ。  
  
7.  リスト ボックス内の項目のいずれかをクリックします。  
  
     **プロパティ**ウィンドウには、2 つの項目のプロパティが表示されます。  
  
8.  プロパティのいずれかを変更し、キーを押します**Enter**します。  
  
     リスト ボックスで、項目が更新されます。