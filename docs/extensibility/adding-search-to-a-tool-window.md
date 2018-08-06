---
title: ツール ウィンドウに検索の追加 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b060261bec61859f33d99ec3f666e1285413592
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498565"
---
# <a name="add-search-to-a-tool-window"></a>検索ツール ウィンドウを追加します。
作成または拡張機能でツール ウィンドウを更新するときは、Visual Studio の他の場所に表示される同じ検索機能を追加できます。 この機能には、次の機能が含まれています。  
  
-   常に、ツールバーのカスタムの領域にある検索ボックス。  
  
-   検索ボックス自体に重ねて表示する進行状況インジケーター。  
  
-   (クイック検索) の各文字を入力するとすぐ、または選択した後にのみ結果を表示する機能、 **Enter**キー (オンデマンドでの検索)。  
  
-   した最近検索した用語を示す一覧です。  
  
-   特定のフィールド、または検索対象の関連で検索をフィルター処理する権限です。  
  
このチュートリアルでは、次のタスクを実行する方法について説明します。  
  
1.  VSPackage プロジェクトを作成します。  
  
2.  読み取り専用テキスト ボックスにユーザー コントロールを含むツール ウィンドウを作成します。  
  
3.  ツール ウィンドウには、検索ボックスを追加します。  
  
4.  検索の実装を追加します。  
  
5.  インスタント検索と進行状況バーの表示を有効にします。  
  
6.  追加、**大文字**オプション。  
  
7.  追加、**偶数行のみを検索**フィルター。  
  
## <a name="to-create-a-vsix-project"></a>VSIX プロジェクトを作成するには  
  
1.  という名前の VSIX プロジェクトを作成する`TestToolWindowSearch`というツール ウィンドウと**TestSearch**します。 この作業の説明を必要がある場合は、次を参照してください。[ツール ウィンドウで、拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)します。  
  
## <a name="to-create-a-tool-window"></a>ツール ウィンドウを作成するには  
  
1.  `TestToolWindowSearch`プロジェクトを開き、 *TestSearchControl.xaml*ファイル。  
  
2.  既存`<StackPanel>`読み取り専用を追加します。 次のブロックとブロック<xref:System.Windows.Controls.TextBox>を、<xref:System.Windows.Controls.UserControl>ツール ウィンドウにします。  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  *TestSearchControl.xaml.cs*ファイルに追加し、次のステートメントを使用します。  
  
    ```csharp  
    using System.Text;  
    ```  
  
4.  削除、`button1_Click()`メソッド。  
  
     **TestSearchControl**クラスで、次のコードを追加します。  
  
     このコードは追加パブリック<xref:System.Windows.Controls.TextBox>という名前のプロパティ**SearchResultsTextBox**という名前のパブリック文字列プロパティと**SearchContent**します。 コンス トラクターの SearchResultsTextBox が、テキスト ボックスに設定されているし、SearchContent は改行で区切られた一連の文字列に初期化されます。 テキスト ボックスのコンテンツは、一連の文字列にも初期化されます。  
  
     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
6.  メニュー バーで、**ビュー** > **その他の Windows** > **TestSearch**します。  
  
     ツール ウィンドウが表示されますが、検索コントロールがまだ表示されません。  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>ツール ウィンドウに検索ボックスを追加するには  
  
1.  *TestSearch.cs*ファイルに、次のコードを追加、`TestSearch`クラス。 コードは、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>プロパティ get アクセサーが返されるように`true`します。  
  
     検索を有効にするをオーバーライドする必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>プロパティ。 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>クラスが実装する<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>し検索では、既定の実装を提供します。  
  
    ```csharp  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
3.  Visual Studio の実験用インスタンスの開く**TestSearch**します。  
  
     ツール ウィンドウの上部にある検索コントロールが表示されます、**検索**透かしと拡大ガラス アイコン。 ただし、検索では、検索のプロセスが実装されていないため、機能しませんまだ。  
  
## <a name="to-add-the-search-implementation"></a>検索の実装を追加するには  
 検索を有効にすると、 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>、前の手順で、ツール ウィンドウが検索ホストを作成します。 このホストを設定し、バック グラウンド スレッドに常に発生する検索のプロセスを管理します。 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>クラスを検索の検索のホストと設定の作成を管理する、のみ検索タスクを作成し、検索メソッドを提供する必要があります。 検索プロセスがバック グラウンド スレッドで発生し、ツール ウィンドウのコントロールへの呼び出しが UI スレッドで発生します。 したがって、使用する必要があります、<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>メソッドを呼び出し、コントロールに対処することを管理します。  
  
1.  *TestSearch.cs*ファイルで、次の追加`using`ステートメント。  
  
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
  
    -   上書き、<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>テキスト ボックスの状態を復元する方法。 ユーザーが検索タスクと、ユーザーが設定または解除オプションやフィルターをキャンセルすると、このメソッドが呼び出されます。 両方<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>は UI スレッドで呼び出されます。 そのためのテキスト ボックスにアクセスする必要はありません、<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>メソッド。  
  
    -   という名前のクラスを作成する`TestSearchTask`から継承する<xref:Microsoft.VisualStudio.Shell.VsSearchTask>の既定の実装を提供する<xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>します。  
  
         `TestSearchTask`、コンス トラクターは、ツール ウィンドウを参照するプライベート フィールドを設定します。 オーバーライドする検索メソッドを提供する、<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>と<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>メソッド。 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>メソッドには検索プロセスを実装します。 このプロセスには、検索を実行する、テキスト ボックスで、検索結果を表示および検索が完了したことを報告するには、このメソッドの基本クラス実装を呼び出すことが含まれています。  
  
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
  
    2.  Visual Studio の実験用インスタンスのツール ウィンドウをもう一度開く、[検索] ウィンドウで、検索テキストを入力およびクリックして**ENTER**します。  
  
         正しい結果が表示されます。  
  
## <a name="to-customize-the-search-behavior"></a>検索動作をカスタマイズするには  
 検索設定を変更するには、検索コントロールの表示方法と、検索の実行方法でさまざまな変更を行うことができます。たとえば、基準値 (検索ボックスに表示される既定のテキスト)、最小値と、検索コントロールの最大の幅および進行状況バーを表示するかどうかを変更できます。 (オンデマンドまたはクイック検索) 上に表示される検索結果を起動し、最近検索した用語の一覧を表示するかどうかの点を変更することもできます。 設定の完全な一覧を見つけることができます、<xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>クラス。  
  
1.  * TestSearch.cs* ファイルに、次のコードを追加、`TestSearch`クラス。 このコードにより、オンデマンドでの検索ではなく、クイック検索 (クリックするユーザーが持っていないことを意味**ENTER**)。 コードは、`ProvideSearchSettings`メソッドで、`TestSearch`クラスで、既定の設定を変更する必要があります。  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  新しいテスト ソリューションをリビルドし、デバッガーを再起動して設定します。  
  
     検索結果は、毎回を表示、検索ボックスに文字を入力してください。  
  
3.  `ProvideSearchSettings`メソッド、進行状況バーを表示するように、次の行を追加します。  
  
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
  
     進行状況バーが表示される進行状況を報告する必要があります。 進行状況を報告するには、次のコードのコメントを解除、`OnStartSearch`のメソッド、`TestSearchTask`クラス。  
  
    ```csharp  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  次の行のコメントを解除する進行状況を処理するための十分な速度の遅いバーが表示されて、`OnStartSearch`のメソッド、`TestSearchTask`クラス。  
  
    ```csharp  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  ソリューションをリビルドし、デバッグを開始して、新しい設定をテストします。  
  
     進行状況バー、検索ウィンドウとして表示されます (検索テキスト ボックスの下の青色の線) たびに検索を実行します。  
  
## <a name="to-enable-users-to-refine-their-searches"></a>検索を絞り込むにユーザーを有効にするには  
 ユーザーをなどのオプションを使用して、検索を絞り込むことができます**大文字**または**単語単位**します。 オプションは、チェック ボックス、またはコマンドのボタンとして表示されるとして表示される、ブール値で指定できます。 このチュートリアルでは、ブール型のオプションを作成します。  
  
1.  *TestSearch.cs*ファイルに、次のコードを追加、`TestSearch`クラス。 コードは、`SearchOptionsEnum`メソッドで、指定したオプションがオンかオフかどうかを検出するために、検索を実装できるようにします。 コードでは、`SearchOptionsEnum`ケースに一致するようにオプションが追加、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>列挙子。 ケースに一致するオプションも利用可能になってとして、`MatchCaseOption`プロパティ。  
  
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
  
2.  `TestSearchTask`クラスで、次のコメントを解除します線、`OnStartSearch`メソッド。  
  
    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```
  
3.  オプションをテストします。  
  
    1.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
    2.  ツール ウィンドウで、テキスト ボックスの右側にある下矢印を選択します。  
  
         **大文字**チェック ボックスが表示されます。  
  
    3.  選択、**大文字**チェック ボックスをオンし、いくつかの検索を実行します。  
  
## <a name="to-add-a-search-filter"></a>検索フィルターを追加するには  
 許可をユーザーに一連の検索対象を絞り込む検索フィルターを追加することができます。 たとえばをそれらが最近変更された日付とファイル名拡張子をファイル エクスプ ローラーでファイルをフィルター処理できます。 このチュートリアルでは、偶数行のみのフィルターを追加します。 ユーザーは、そのフィルターが、検索ホストは、検索クエリに指定する文字列を追加します。 検索メソッド内でこれらの文字列を識別し、検索対象をそれに応じてフィルター処理します。  
  
1.  *TestSearch.cs*ファイルに、次のコードを追加、`TestSearch`クラス。 コードを実装して`SearchFiltersEnum`を追加して、<xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>偶数行のみが表示されるように、検索結果をフィルター処理を指定します。  
  
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
  
     検索コントロールは、検索フィルターを表示します。 これで`Search even lines only`します。 ユーザーが、フィルター文字列を選択したときに`lines:"even"`検索ボックスに表示されます。 他の検索条件、フィルターとして同時に表示できます。 検索文字列が、フィルター、またはその両方の後に、フィルターの前にあります。  
  
2.  *TestSearch.cs*ファイルで、次のメソッドを追加、`TestSearchTask`では、クラス、`TestSearch`クラス。 これらのメソッドのサポート、`OnStartSearch`メソッドで、次の手順で変更します。  
  
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
  
5.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスのツール ウィンドウが開きと検索コントロールの下矢印をクリックします。  
  
     **大文字** チェック ボックスと**偶数行のみを検索**フィルターが表示されます。  
  
6.  フィルターを選択します。  
  
     検索ボックスには**行:「偶数」**、し、次の結果が表示されます。  
  
     優れた 2  
  
     4 な  
  
     6 つの別れ  
  
7.  削除`lines:"even"`、検索ボックスから選択、**大文字**チェック ボックスをオンにし、入力`g`検索ボックスにします。  
  
     次の結果が表示されます。  
  
     1 を移動します。  
  
     優れた 2  
  
     5 つの別れ  
  
8.  検索ボックスの右側にある X を選択します。  
  
     検索をオフにされ、元の内容が表示されます。 ただし、**大文字** チェック ボックスが選択されたままです。