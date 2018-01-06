---
title: "ツール ウィンドウに検索を追加する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d37956c01cbbebbe29d7506cf5eacd9456b3bbc1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="adding-search-to-a-tool-window"></a>ツール ウィンドウに検索を追加します。
作成または拡張機能のツール ウィンドウを更新するときは、Visual Studio で別の場所に表示される同じの検索機能を追加できます。 この機能では、次の機能があります。  
  
-   常に、ツールバーのカスタムの領域にある検索ボックスです。  
  
-   検索ボックス自体に重ねて表示、進行状況インジケーター。  
  
-   (クイック検索) の各文字を入力するとすぐに、または Enter キー (オンデマンドでの検索) を選択した後にのみ、結果を表示する権限です。  
  
-   用語を検索する最後を示す一覧です。  
  
-   特定のフィールド、または検索対象の関連で検索をフィルター処理する機能。  
  
 このチュートリアルでは、次のタスクを実行する方法について説明します。  
  
1.  VSPackage プロジェクトを作成します。  
  
2.  読み取り専用テキスト ボックスにユーザー コントロールを含んでいるツール ウィンドウを作成します。  
  
3.  ツール ウィンドウに検索ボックスを追加します。  
  
4.  検索の実装を追加します。  
  
5.  クイック検索と進行状況バーの表示を有効にします。  
  
6.  追加、**大文字小文字を**オプション。  
  
7.  追加、**偶数行のみを検索**フィルター。  
  
## <a name="to-create-a-vsix-project"></a>VSIX プロジェクトを作成するには  
  
1.  という名前の VSIX プロジェクトを作成する`TestToolWindowSearch`という名前のツール ウィンドウで**TestSearch**です。 この作業の説明を必要がある場合は、次を参照してください。[ツール ウィンドウで、拡張機能の作成](../extensibility/creating-an-extension-with-a-tool-window.md)です。  
  
## <a name="to-create-a-tool-window"></a>ツール ウィンドウを作成するには  
  
1.  `TestToolWindowSearch`プロジェクト、TestSearchControl.xaml ファイルを開きます。  
  
2.  既存の置換`<StackPanel>`読み取り専用の追加は、次のブロックとブロック<xref:System.Windows.Controls.TextBox>を<xref:System.Windows.Controls.UserControl>ツール ウィンドウにします。  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  TestSearchControl.xaml.cs ファイルに次のコードを追加ステートメントを使用します。  
  
    ```csharp  
    using System.Text;  
    ```  
  
4.  削除、`button1_Click()`メソッドです。  
  
     **TestSearchControl**クラスで、次のコードを追加します。  
  
     このコードは追加パブリック<xref:System.Windows.Controls.TextBox>という名前のプロパティ**SearchResultsTextBox**およびという名前のパブリックの文字列プロパティ**SearchContent**です。 コンス トラクターで SearchResultsTextBox がテキスト ボックスに設定されているし、SearchContent は改行で区切られた一連の文字列に初期化します。 テキスト ボックスの内容は、文字列のセットにも初期化されます。  
  
    ```csharp  
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
  
     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
6.  メニュー バーで、次のように選択します。**ビュー**、**その他のウィンドウ**、 **TestSearch**です。  
  
     ツール ウィンドウが表示されますが、検索コントロールがまだ表示されません。  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>ツール ウィンドウに検索ボックスを追加するには  
  
1.  TestSearch.cs ファイル内に次のコードを追加、`TestSearch`クラスです。 コードは、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>プロパティ get アクセサーを返しますように`true`です。  
  
     検索を有効にするをオーバーライドする必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>プロパティです。 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>クラスが実装する<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>し、検索では、既定の実装を提供します。  
  
    ```csharp  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
3.  Visual Studio の実験用インスタンスの開く**TestSearch**です。  
  
     ツール ウィンドウの上部には、検索コントロールが表示されます、**検索**ウォーターマークと拡大ガラス アイコン。 ただし、検索それでもまだ検索プロセスが実装されていないためです。  
  
## <a name="to-add-the-search-implementation"></a>検索の実装を追加するには  
 検索を有効にすると、 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>、前の手順で、[ツール] ウィンドウが検索ホストを作成します。 このホストを設定し、検索のプロセスは、常にバック グラウンド スレッドで発生する可能性を管理します。 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>クラスは、search ホストと、設定の作成を検索の管理、のみ検索タスクを作成し、検索メソッドを提供する必要があります。 検索処理はバック グラウンド スレッドで発生し、ツール ウィンドウのコントロールへの呼び出しが UI スレッドで発生します。 したがって、使用する必要があります、<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>方法にコントロールを扱うで行ったすべての呼び出しを管理します。  
  
1.  TestSearch.cs ファイルに次のコードを追加`using`ステートメント。  
  
    ```csharp  
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
  
2.  `TestSearch`クラスで、次の操作を実行する次のコードを追加します。  
  
    -   上書き、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>検索タスクを作成します。  
  
    -   上書き、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>をテキスト ボックスの状態を復元します。 ユーザーと、ユーザーが設定または解除オプションまたはフィルターの検索タスクをキャンセルすると、このメソッドが呼び出されます。 両方<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>UI スレッドで呼び出されます。 テキスト ボックスにアクセスするため、する必要はありません、<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>メソッドです。  
  
    -   という名前のクラスを作成できます`TestSearchTask`から継承する<xref:Microsoft.VisualStudio.Shell.VsSearchTask>の既定の実装を提供する<xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>です。  
  
         `TestSearchTask`、コンス トラクターは、ツール ウィンドウを参照するプライベート フィールドを設定します。 オーバーライドする search メソッドを提供する、<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>と<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>メソッドです。 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>メソッドは、検索プロセスを実装します。 このプロセスには、検索を実行する、テキスト ボックスに、検索結果を表示して、検索が完了したことを報告するには、このメソッドの基本クラス実装を呼び出すことが含まれています。  
  
    ```csharp  
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
  
3.  次の手順を実行することによって、検索の実装をテストします。  
  
    1.  プロジェクトをリビルドし、デバッグを開始します。  
  
    2.  Visual Studio の実験用インスタンスのツール ウィンドウをもう一度開き、[検索] ウィンドウで、検索テキストを入力および enter キーを押します。  
  
         正しい結果が表示されます。  
  
## <a name="to-customize-the-search-behavior"></a>検索の動作をカスタマイズするには  
 検索設定を変更すると、検索コントロールの表示方法と、検索の実行方法のさまざまな変更を行うことができます。たとえば、透かし (既定のテキストの検索ボックスに表示される)、最小値と、検索コントロールの幅の最大値と進行状況バーを表示するかどうかを変更することができます。 (要求時またはクイック検索) 上に表示される検索結果を起動し、最近検索した用語の一覧を表示するかどうかの点を変更することもできます。 設定の完全な一覧を見つけることができます、<xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>クラスです。  
  
1.  TestSearch.cs ファイル内に次のコードを追加、`TestSearch`クラスです。 このコードは、オンデマンドで検索 (つまり、ユーザー入力 をクリックする必要はありません) の代わりにクイック検索を使用できます。 コードは、`ProvideSearchSettings`メソッドで、`TestSearch`クラスで、既定の設定を変更する必要があります。  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  新しいテスト ソリューションをリビルドして、デバッガーを再起動して設定します。  
  
     検索結果は表示たびに、検索ボックスに文字を入力してください。  
  
3.  `ProvideSearchSettings`メソッド、進行状況バーの表示を有効にする次の行を追加します。  
  
    ```csharp  
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
  
     表示される進行状況バー、進行状況を報告する必要があります。 進行状況を報告するために次のコードのコメントを解除、`OnStartSearch`のメソッド、`TestSearchTask`クラス。  
  
    ```csharp  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  次の行のコメントを解除する進行状況を処理するための十分な速度の遅いバーが表示されて、`OnStartSearch`のメソッド、`TestSearchTask`クラス。  
  
    ```csharp  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  ソリューションをリビルドして、debugb を開始して、新しい設定をテストします。  
  
     進行状況バー、検索ウィンドウとして表示されます (検索テキスト ボックスの下の青い線) たびに検索を実行することです。  
  
## <a name="to-enable-users-to-refine-their-searches"></a>検索を絞り込むのにを有効にするには  
 ユーザーをなどのオプションを使用して、検索を絞り込むことができます**大文字小文字を**または**単語単位**です。 オプションは、チェック ボックスまたはボタンとして表示されるコマンドとして表示される、ブール値で指定できます。 このチュートリアルでは、ブール型のオプションを作成します。  
  
1.  TestSearch.cs ファイル内に次のコードを追加、`TestSearch`クラスです。 コードは、`SearchOptionsEnum`メソッドで、指定したオプションがオンかオフかどうかを検出するために検索を実装できるようにします。 内のコード`SearchOptionsEnum`大文字小文字にするためのオプションを追加、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>列挙子。 ケースに一致するオプションも使用可能になりますとして、`MatchCaseOption`プロパティです。  
  
    ```csharp  
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
  
2.  `TestSearchTask`クラス、matchCase 行のコメントを解除、`OnStartSearch`メソッド。  
  
    ```csharp  
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
  
         **大文字小文字を** チェック ボックスが表示されます。  
  
    3.  選択、**大文字小文字を**チェック ボックスをオンし、いくつかの検索を実行します。  
  
## <a name="to-add-a-search-filter"></a>検索フィルターを追加するには  
 一連の検索対象を絞り込むためのユーザーに許可する検索フィルターを追加することができます。 たとえばにそれらが最近変更された日付とファイル名拡張子で、ファイル エクスプ ローラーでファイルをフィルターできます。 このチュートリアルでは、偶数行だけのフィルターを追加します。 そのフィルターを選択すると、search ホストは、検索クエリを指定する文字列を追加します。 検索、メソッド内のこれらの文字列を識別し、それに応じて、検索対象をフィルター処理できます。  
  
1.  TestSearch.cs ファイル内に次のコードを追加、`TestSearch`クラスです。 コードを実装して`SearchFiltersEnum`追加することによって、<xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>を偶数行のみが表示されるように、検索結果をフィルター処理を指定します。  
  
    ```csharp  
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
  
     検索コントロールに検索フィルターが表示されます`Search even lines only`です。 ユーザーが、フィルター文字列を選択すると`lines:"even"`検索ボックスに表示されます。 他の検索条件でフィルターと同時に表示されます。 検索文字列が、フィルターの前に、フィルター、またはその両方の後に表示されます。  
  
2.  TestSearch.cs ファイル内に次のメソッドを追加、`TestSearchTask`では、クラス、`TestSearch`クラスです。 これらのメソッドのサポート、`OnStartSearch`メソッドで、次の手順で変更してみます。  
  
    ```csharp  
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
  
3.  `TestSearchTask`クラス、更新、`OnStartSearch`メソッドを次のコード。 この変更は、フィルターをサポートするためにコードを更新します。  
  
    ```csharp  
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
  
5.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスのツール ウィンドウを開き検索コントロールの下向き矢印をクリックします。  
  
     **大文字小文字を** チェック ボックスおよび**偶数行のみを検索**フィルターが表示されます。  
  
6.  フィルターを選択します。  
  
     検索ボックスには、**行:「でも」**、され、次の結果が表示されます。  
  
     適切な 2  
  
     4 な  
  
     6 goodbye  
  
7.  削除`lines:"even"`[検索] ボックスから選択、**大文字小文字を**チェック ボックスをオンにし、入力`g`検索ボックスにします。  
  
     次の結果が表示されます。  
  
     1 します。  
  
     適切な 2  
  
     5 goodbye  
  
8.  検索ボックスの右側にある X を選択します。  
  
     検索はクリアされ、元の内容が表示されます。 ただし、**大文字小文字を** チェック ボックスが選択されています。