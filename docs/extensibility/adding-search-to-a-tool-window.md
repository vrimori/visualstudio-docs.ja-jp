---
title: "ツール ウィンドウに検索を追加する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
caps.latest.revision: 38
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
ms.sourcegitcommit: bca8c87d4f7d89d491fab13e1a511febce81d3d8
ms.openlocfilehash: 845bbc5c34280f7ceafcaa3d763065f6d73388fe
ms.lasthandoff: 02/22/2017

---
# <a name="adding-search-to-a-tool-window"></a>ツール ウィンドウに検索を追加します。
作成または拡張機能のツール ウィンドウを更新する場合は、Visual Studio で他の場所に表示される同じ検索機能を追加できます。 この機能には、次の機能があります。  
  
-   常に、ツールバーのカスタムの領域にある検索ボックス。  
  
-   検索ボックス自体が込められている進行状況インジケーター。  
  
-   (クイック検索) の各文字を入力するとすぐに、または Enter キー (オンデマンドでの検索) を選択した後にのみ、結果を表示する権限です。  
  
-   検索する最後の用語を示す一覧です。  
  
-   特定のフィールド、または検索対象の関連で検索をフィルター処理する機能。  
  
 このチュートリアルでは、次のタスクを実行する方法について説明します。  
  
1.  VSPackage プロジェクトを作成します。  
  
2.  読み取り専用テキスト ボックスにユーザー コントロールを含むツール ウィンドウを作成します。  
  
3.  ツール ウィンドウに検索ボックスを追加します。  
  
4.  検索の実装を追加します。  
  
5.  クイック検索と進行状況バーの表示を有効にします。  
  
6.  追加、**大文字小文字を**オプション。  
  
7.  追加、**偶数行のみを検索**フィルター。  
  
## <a name="to-create-a-vsix-project"></a>VSIX プロジェクトを作成するには  
  
1.  という名前の VSIX プロジェクトを作成する`TestToolWindowSearch`という名前のツール ウィンドウで**TestSearch**します。 この操作の説明を必要がある場合は、次を参照してください。[ツール ウィンドウで、拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)です。  
  
## <a name="to-create-a-tool-window"></a>ツール ウィンドウを作成するには  
  
1.  `TestToolWindowSearch`プロジェクト TestSearchControl.xaml ファイルを開きます。  
  
2.  既存`<StackPanel>`読み取り専用の追加は、次のブロックとブロック<xref:System.Windows.Controls.TextBox>に、<xref:System.Windows.Controls.UserControl>ツール ウィンドウ</xref:System.Windows.Controls.UserControl></xref:System.Windows.Controls.TextBox>。  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  TestSearchControl.xaml.cs ファイルに次のコードを追加ステートメントを使用します。  
  
    ```c#  
    using System.Text;  
    ```  
  
4.  削除、`button1_Click()`メソッドです。  
  
     **TestSearchControl**クラスを次のコードを追加します。  
  
     このコードによって追加パブリック<xref:System.Windows.Controls.TextBox>という名前のプロパティ**SearchResultsTextBox**とという名前のパブリック文字列プロパティ**SearchContent**</xref:System.Windows.Controls.TextBox> 。 コンス トラクターで SearchResultsTextBox がテキスト ボックスに設定されているし、SearchContent は改行で区切られた一連の文字列に初期化します。 テキスト ボックスの内容は、文字列のセットにも初期化されます。  
  
    ```c#  
    public partial class TestSearchControl : UserControl  
    {  
        public TextBox SearchResultsTextBox { get; set; }  
        public string SearchContent { get; set; }  
  
        public TestSearchControl()  
        {  
            InitializeComponent();  
  
            this.SearchResultsTextBox = resultsTextBox;  
            this.SearchContent = BuildContent();  
  
            this.SearchResultsTextBox.Text = this.SearchContent;  
        }  
  
        private string BuildContent()  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendLine("1 go");  
            sb.AppendLine("2 good");  
            sb.AppendLine("3 Go");  
            sb.AppendLine("4 Good");  
            sb.AppendLine("5 goodbye");  
            sb.AppendLine("6 Goodbye");  
  
            return sb.ToString();  
        }  
    }  
    ```  
  
     [!code-cs[ToolWindowSearch&1;](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs) ] 
     [!code-vb [ToolWindowSearch&1;](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
6.  メニュー バー**ビュー**、**その他のウィンドウ**、 **TestSearch**します。  
  
     ツール ウィンドウが表示されますが、検索コントロールがまだ表示されません。  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>ツール ウィンドウに検索ボックスを追加するには  
  
1.  TestSearch.cs ファイルで次のコードを追加、`TestSearch`クラスです。 コードは、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>プロパティ get アクセサーが返されるように`true`</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>。  
  
     検索を有効にするをオーバーライドする必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>プロパティ</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>。 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>クラスが実装する<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>し検索では、既定の実装を提供します</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch></xref:Microsoft.VisualStudio.Shell.ToolWindowPane>。  
  
    ```c#  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
3.  Visual Studio の実験用インスタンスで開きます**TestSearch**します。  
  
     ツール ウィンドウの上部にある検索コントロールが表示されます、**検索**透かしとガラス虫眼鏡のアイコン。 ただし、検索では、検索のプロセスが実装されていないために機能 いません。  
  
## <a name="to-add-the-search-implementation"></a>検索の実装を追加するには  
 検索を有効にすると、<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>前の手順で、[ツール] ウィンドウが検索ホストを作成してください</xref:Microsoft.VisualStudio.Shell.ToolWindowPane>。 このホストを設定し、常にバック グラウンド スレッドで実行する検索のプロセスを管理します。 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>クラスを検索の search ホストと、設定の作成を管理する、のみ検索タスクを作成し、search メソッドを提供する必要があります</xref:Microsoft.VisualStudio.Shell.ToolWindowPane>。 検索処理がバック グラウンド スレッドで発生し、ツール ウィンドウ コントロールへの呼び出しが UI スレッドで発生します。 したがって、使用する必要があります、<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>方法にコントロールを扱うで行ったすべての呼び出しを管理する</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>。  
  
1.  TestSearch.cs ファイルに次のコードを追加`using`ステートメント。  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Runtime.InteropServices;  
    using System.Text;  
    using System.Windows.Controls;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
2.  `TestSearch`クラスを次のコードは、次の操作を追加します。  
  
    -   上書き、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>検索タスクを作成する方法</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>。  
  
    -   上書き、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>テキスト ボックスの状態を復元する方法</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>。 このメソッドは、ユーザーを検索タスクと、ユーザーが設定または設定オプションやフィルターが解除されます。 両方とも<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>UI スレッドで呼び出されます</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>。 テキスト ボックスにアクセスする必要はありませんので、<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>メソッド</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>。  
  
    -   という名前のクラスを作成できます`TestSearchTask` <xref:Microsoft.VisualStudio.Shell.VsSearchTask> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>の既定の実装を提供する</xref:Microsoft.VisualStudio.Shell.VsSearchTask>から継承します。  
  
         `TestSearchTask`、コンス トラクターは、ツール ウィンドウを参照するプライベート フィールドを設定します。 オーバーライドする search メソッドを提供する、<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>と<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>メソッド</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A></xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>。 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>メソッドは、検索処理を実装する</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>。 このプロセスには、検索を実行する、テキスト ボックスに検索結果が表示および検索が完了したことを報告するには、このメソッドの基本クラス実装の呼び出しが含まれています。  
  
    ```c#  
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)  
    {  
        if (pSearchQuery == null || pSearchCallback == null)  
            return null;  
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);  
    }  
  
    public override void ClearSearch()  
    {  
        TestSearchControl control = (TestSearchControl)this.Content;  
        control.SearchResultsTextBox.Text = control.SearchContent;  
    }  
  
    internal class TestSearchTask : VsSearchTask  
    {  
        private TestSearch m_toolWindow;  
  
        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)  
            : base(dwCookie, pSearchQuery, pSearchCallback)  
        {  
            m_toolWindow = toolwindow;  
        }  
  
        protected override void OnStartSearch()  
        {  
            // Use the original content of the text box as the target of the search.   
            var separator = new string[] { Environment.NewLine };  
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;  
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);  
  
            // Get the search option.   
            bool matchCase = false;  
            // matchCase = m_toolWindow.MatchCaseOption.Value;   
  
                // Set variables that are used in the finally block.  
                StringBuilder sb = new StringBuilder("");  
                uint resultCount = 0;  
                this.ErrorCode = VSConstants.S_OK;  
  
                try  
                {  
                    string searchString = this.SearchQuery.SearchString;  
  
                    // Determine the results.   
                    uint progress = 0;  
                    foreach (string line in contentArr)  
                    {  
                        if (matchCase == true)  
                        {  
                            if (line.Contains(searchString))  
                            {  
                                sb.AppendLine(line);  
                                resultCount++;  
                            }  
                        }  
                        else  
                            {  
                                if (line.ToLower().Contains(searchString.ToLower()))  
                                {  
                                    sb.AppendLine(line);  
                                    resultCount++;  
                                }  
                            }  
  
                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));   
  
                            // Uncomment the following line to demonstrate the progress bar.   
                            // System.Threading.Thread.Sleep(100);  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        this.ErrorCode = VSConstants.E_FAIL;  
                    }  
                    finally  
                    {  
                        ThreadHelper.Generic.Invoke(() =>  
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
                        this.SearchResults = resultCount;  
                    }  
  
            // Call the implementation of this method in the base class.   
            // This sets the task status to complete and reports task completion.   
            base.OnStartSearch();  
        }  
  
        protected override void OnStopSearch()  
        {  
            this.SearchResults = 0;  
        }  
    }  
    ```  
  
3.  次の手順を実行して、検索の実装をテストします。  
  
    1.  プロジェクトをリビルドし、デバッグを開始します。  
  
    2.  Visual Studio の実験用インスタンスのツール ウィンドウをもう一度開く検索 ウィンドウに検索テキストを入力し、enter キーを押します。  
  
         正しい結果が表示されます。  
  
## <a name="to-customize-the-search-behavior"></a>検索の動作をカスタマイズするには  
 検索の設定を変更すると、検索コントロールの表示方法と、検索の実行方法のさまざまな変更を行うことができます。 たとえば、ウォーターマーク (検索ボックスに表示される既定のテキスト)、最小値と検索コントロールの幅の最大値および進行状況バーを表示するかどうかを変更できます。 (オンデマンドまたはクイック検索の場合) に表示される検索結果を起動し、最近検索した語句の一覧を表示するかどうかの時点を変更することもできます。 <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>クラス</xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>の設定の完全な一覧を見つけることができます。  
  
1.  TestSearch.cs ファイルで次のコードを追加、`TestSearch`クラスです。 このコードは、オンデマンドで検索 (つまり、ユーザー入力 をクリックする必要はありません) ではなくクイック検索を有効します。 コードは、`ProvideSearchSettings`メソッドで、`TestSearch`クラスで、既定の設定を変更する必要があります。  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  新しいテスト ソリューションをリビルドして、デバッガーを再起動して設定します。  
  
     検索結果は表示たびに、検索ボックスに文字を入力してください。  
  
3.  `ProvideSearchSettings`メソッド、進行状況バーを表示するように、次の行を追加します。  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,   
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);  
    }  
    ```  
  
     表示される進行状況バーで、進行状況を報告する必要があります。 進行状況を報告するために次のコードをコメント解除、`OnStartSearch`のメソッド、`TestSearchTask`クラス。  
  
    ```c#  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  次の行のコメントを解除する進行状況を処理するための十分な速度の遅いバーが表示されて、`OnStartSearch`のメソッド、`TestSearchTask`クラス。  
  
    ```c#  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  ソリューションをリビルドして、debugb を開始して、新しい設定をテストします。  
  
     進行状況バー、検索ウィンドウとして表示されます (検索テキスト ボックスの下の青い線) たびに検索を実行することです。  
  
## <a name="to-enable-users-to-refine-their-searches"></a>検索を絞り込むのにを有効にするには  
 オプションにより、検索を絞り込むようにユーザーができる**大文字小文字を**または**単語単位**します。 オプションは、チェック ボックス、またはボタンとして表示するコマンドとして表示される、ブール値で指定できます。 このチュートリアルでは、ブール型のオプションを作成します。  
  
1.  TestSearch.cs ファイルで次のコードを追加、`TestSearch`クラスです。 コードは、`SearchOptionsEnum`メソッドで、指定したオプションがオンかオフかどうかを検出するために検索を実装できるようにします。 内のコード`SearchOptionsEnum`大文字小文字にするためのオプションを追加、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>列挙子</xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>。 大文字小文字をするためのオプションが利用可能にもとして、`MatchCaseOption`プロパティです。  
  
    ```c#  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
        {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
2.  `TestSearchTask`クラスで matchCase 行をコメント解除、`OnStartSearch`メソッド。  
  
    ```c#  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
         {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
3.  オプションをテストします。  
  
    1.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
    2.  ツール ウィンドウで、テキスト ボックスの右側にある下向き矢印を選択します。  
  
         **大文字** チェック ボックスが表示されます。  
  
    3.  選択、**大文字小文字を**チェック ボックスをオンし、いくつかの検索を実行します。  
  
## <a name="to-add-a-search-filter"></a>検索フィルターを追加するには  
 許可をユーザーに一連の検索対象を絞り込む検索フィルターを追加することができます。 たとえばにそれらが最近変更された日付とそのファイル名拡張子によってファイル エクスプ ローラーでファイルをフィルター処理できます。 このチュートリアルでは、偶数行だけのフィルターを追加します。 そのフィルターを選択すると、検索のホストは、検索クエリを指定する文字列を追加します。 Search メソッド内のこれらの文字列を識別し、検索対象をそれに応じてフィルター処理します。  
  
1.  TestSearch.cs ファイルで次のコードを追加、`TestSearch`クラスです。 コードを実装して`SearchFiltersEnum`追加することで、<xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>偶数行のみが表示されるように、検索結果をフィルタ リングするを指定します</xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>。  
  
    ```c#  
    public override IVsEnumWindowSearchFilters SearchFiltersEnum  
    {  
        get  
        {  
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();  
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));  
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;  
        }  
    }  
  
    ```  
  
     検索コントロールに検索フィルターが表示されます`Search even lines only`します。 ユーザーが、文字列、フィルターを選択すると`lines:"even"`検索ボックスに表示されます。 他の検索条件でフィルターと同時に表示されます。 検索文字列が、フィルターの前に、フィルター、またはその両方の後に表示されます。  
  
2.  TestSearch.cs ファイルで次のメソッドを追加、`TestSearchTask`では、クラス、`TestSearch`クラスです。 これらのメソッドのサポート、`OnStartSearch`メソッドで、次の手順で変更します。  
  
    ```c#  
    private string RemoveFromString(string origString, string stringToRemove)  
    {  
        int index = origString.IndexOf(stringToRemove);  
        if (index == -1)  
            return origString;  
        else   
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();  
    }  
  
    private string[] GetEvenItems(string[] contentArr)  
    {  
        int length = contentArr.Length / 2;  
        string[] evenContentArr = new string[length];  
  
        int indexB = 0;  
        for (int index = 1; index < contentArr.Length; index += 2)  
        {  
            evenContentArr[indexB] = contentArr[index];  
            indexB++;  
        }  
  
        return evenContentArr;  
    }  
    ```  
  
3.  `TestSearchTask`クラス、更新、`OnStartSearch`メソッドを次のコードです。 この変更は、フィルターをサポートするためにコードを更新します。  
  
    ```c#  
    protected override void OnStartSearch()  
    {  
        // Use the original content of the text box as the target of the search.   
        var separator = new string[] { Environment.NewLine };  
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);  
  
        // Get the search option.   
        bool matchCase = false;  
        matchCase = m_toolWindow.MatchCaseOption.Value;  
  
        // Set variables that are used in the finally block.  
        StringBuilder sb = new StringBuilder("");  
        uint resultCount = 0;  
        this.ErrorCode = VSConstants.S_OK;  
  
        try  
        {  
            string searchString = this.SearchQuery.SearchString;  
  
            // If the search string contains the filter string, filter the content array.   
            string filterString = "lines:\"even\"";  
  
            if (this.SearchQuery.SearchString.Contains(filterString))  
            {  
                // Retain only the even items in the array.  
                contentArr = GetEvenItems(contentArr);  
  
                // Remove 'lines:"even"' from the search string.  
                searchString = RemoveFromString(searchString, filterString);  
            }  
  
            // Determine the results.   
            uint progress = 0;  
            foreach (string line in contentArr)  
            {  
                if (matchCase == true)  
                {  
                    if (line.Contains(searchString))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
                else  
                {  
                    if (line.ToLower().Contains(searchString.ToLower()))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
  
                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
  
                // Uncomment the following line to demonstrate the progress bar.   
                // System.Threading.Thread.Sleep(100);  
            }  
        }  
        catch (Exception e)  
        {  
            this.ErrorCode = VSConstants.E_FAIL;  
        }  
        finally  
        {  
            ThreadHelper.Generic.Invoke(() =>  
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
            this.SearchResults = resultCount;  
        }  
  
        // Call the implementation of this method in the base class.   
        // This sets the task status to complete and reports task completion.   
        base.OnStartSearch();  
    }  
    ```  
  
4.  コードをテストします。  
  
5.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスのツール ウィンドウを開き検索コントロール下方向キーを選択します。  
  
     **大文字小文字を** チェック ボックスおよび**偶数行のみを検索**フィルターが表示されます。  
  
6.  フィルターを選択します。  
  
     検索ボックスには**行:「偶数」**、され、次の結果が表示されます。  
  
     適切な&2;  
  
     適切では&4;  
  
     6 goodbye  
  
7.  削除`lines:"even"`、検索ボックスから選択、**大文字小文字を**チェック ボックスをオンにし、入力`g`検索ボックスにします。  
  
     次の結果が表示されます。  
  
     1 します。  
  
     適切な&2;  
  
     5"goodbye"  
  
8.  検索ボックスの右側にある X を選択します。  
  
     検索をオフにすると、され、元の内容が表示されます。 ただし、**大文字小文字を** チェック ボックスが選択されたままです。
