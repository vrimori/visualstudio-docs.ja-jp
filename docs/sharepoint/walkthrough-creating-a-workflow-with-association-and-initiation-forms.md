---
title: 'チュートリアル: 関連付けと開始フォームを持つワークフローを作成する |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c9878da7c1384dec8d0c8aa863b0eff4252e9efe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824737"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>チュートリアル: ワークフロー関連付けフォームと開始フォームを作成します。
  このチュートリアルでは、アソシエーションと開始フォームの使用方法が組み込まれている基本的なシーケンシャル ワークフローを作成する方法を示します。 これらは、まず、SharePoint 管理者 (関連付けフォーム) が関連付けられているとき、およびユーザー (開始フォーム) が、ワークフローを開始、ワークフローに追加するパラメーターを有効にする ASPX フォームです。  
  
 このチュートリアルでは、ユーザーが、次の要件を含む経費報告書の承認ワークフローを作成するシナリオについて概説します。  
  
- ワークフローが一覧に関連付けられた場合は、管理者に経費報告書について上限金額を入力する関連付けフォームが表示されます。  
  
- 従業員 Shared Documents の一覧に、経費報告書をアップロードするには、ワークフローを開始および経費のワークフロー開始フォームの合計を入力します。  
  
- 合計従業員経費報告書は、管理者の定義済みの制限を超えている場合、経費報告書を承認する従業員のマネージャーのタスクを作成します。 ただし、従業員の経費レポートの合計が経費の上限以下の場合は、ワークフローの履歴リストに、自動承認のメッセージが書き込まれます。  
  
  このチュートリアルでは、次の作業について説明します。  
  
- SharePoint リスト定義シーケンシャル ワークフロー プロジェクトを作成する[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。  
  
- ワークフローのスケジュールを作成します。  
  
- ワークフロー アクティビティのイベントを処理します。  
  
- ワークフロー関連付けフォームと開始フォームを作成します。  
  
- ワークフローの関連付け。  
  
- ワークフローを手動で開始します。  
  
> [!NOTE]  
>  このチュートリアルでは、シーケンシャル ワークフロー プロジェクトは使用して、プロセスはステート マシン ワークフローで同じです。  
>   
>  別の名前または場所の一部でも、コンピューターを表示可能性があります、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]次の手順でユーザー インターフェイス要素です。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]所有しているエディションと使用する設定は、これらの要素を決定します。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]および SharePoint。  
  
-   Visual Studio  
  
## <a name="create-a-sharepoint-sequential-workflow-project"></a>SharePoint シーケンシャル ワークフロー プロジェクトを作成します。
 最初に、シーケンシャル ワークフロー プロジェクトを作成[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 シーケンシャル ワークフローは、最後のアクティビティが終了するまでの順序で実行される一連の手順です。 この手順では、SharePoint での Shared Documents の一覧に適用されるシーケンシャル ワークフローを作成します。 ワークフローのウィザードでは、サイトまたはリスト定義のいずれかでワークフローを関連付けることができ、ワークフローを開始するかを判断することができます。  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>SharePoint シーケンシャル ワークフロー プロジェクトを作成するには  
  
1.  メニュー バーで、**ファイル** > **新規** > **プロジェクト**を表示する、**新しいプロジェクト** ダイアログ ボックス。  
  
2.  展開、 **SharePoint**のどちらかのノード**Visual c#** または**Visual Basic**を選択し、 **2010**ノード。  
  
3.  **テンプレート**ウィンドウで、選択、 **SharePoint 2010 プロジェクト**プロジェクト テンプレート。  
  
4.  **名前**ボックスに、入力**ExpenseReport**選択し、 **OK**ボタン。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
5.  **デバッグのサイトとセキュリティのレベルを指定**ページで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックして、 **[完了]** ボタンをクリックします信頼レベルと既定のサイトです。  
  
     また、この手順は、ファーム ソリューションは、ワークフロー プロジェクトに対してのみ使用できるオプションとして、ソリューションの信頼レベルを設定します。  
  
6.  **ソリューション エクスプローラー**で、プロジェクト ノードを選択します。  
  
7.  メニュー バーで **[プロジェクト]** > **[新しい項目の追加]** の順に選択します。  
  
8.  いずれかで**Visual c#** または**Visual Basic**、展開、 **SharePoint**ノードを選択し、 **2010**ノード。  
  
9. **テンプレート**ウィンドウで、選択**シーケンシャル ワークフロー (ファーム ソリューションのみ)** テンプレートを選択し、**追加**ボタン。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
10. **デバッグ ワークフローの名前を指定** ページで、既定の名前 (**ExpenseReport - Workflow1**)。 既定のワークフロー テンプレート型の値の保持 (**リスト ワークフロー)** します。 **[次へ]** ボタンをクリックします。  
  
11. **Visual Studio デバッグ セッションでワークフローを自動的に関連付けるを希望しますか?**  ページで、ボックスがオンの場合、ワークフロー テンプレートを自動的に関連付けられますをオフにします。  
  
     この手順を使用して、手動で関連付けフォームを表示する共有ドキュメントのリストを後でワークフローを関連付けることができます。  
  
12. 選択、**完了**ボタンをクリックします。  
  
## <a name="add-an-association-form-to-the-workflow"></a>関連付けフォームをワークフローに追加します。
 次に、作成します。まず、SharePoint 管理者は、経費報告書ドキュメントをワークフローを関連付けますときに表示される ASPX 関連付けフォーム。  
  
#### <a name="to-add-an-association-form-to-the-workflow"></a>ワークフロー関連付けフォームを追加するには  
  
1.  選択、 **Workflow1**ノード**ソリューション エクスプ ローラー**します。  
  
2.  メニュー バーで、**プロジェクト** > **新しい項目の追加**を表示する、**新しい項目の追加** ダイアログ ボックス。  
  
3.  ダイアログ ボックスのツリー ビューのいずれかを展開**Visual c#** または**Visual Basic** (プロジェクト言語) に応じて、展開、 **SharePoint**ノード、を選択し**2010**ノード。  
  
4.  テンプレートの一覧で選択、**ワークフロー関連付けフォーム**テンプレート。  
  
5.  **名前**テキスト ボックスに、入力**ExpenseReportAssocForm.aspx**します。  
  
6.  選択、**追加**フォームをプロジェクトに追加するボタンをクリックします。  
  
## <a name="designing-and-coding-the-association-form"></a>設計とコーディングの関連付けフォーム
 この手順では、コントロールとコードを追加で関連付けフォームの機能を紹介します。  
  
#### <a name="to-design-and-code-the-association-form"></a>デザインおよびコーディング関連付けフォーム  
  
1.  関連付けフォーム (ExpenseReportAssocForm.aspx) では、検索、`asp:Content`要素を持つ`ID="Main"`します。  
  
2.  このコンテンツの要素の最初の行の直後後には、ラベルと経費承認の制限の入力を求めるテキスト ボックスを作成する次のコードを追加 (*AutoApproveLimit*)。  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  展開、 **ExpenseReportAssocForm.aspx**ファイル**ソリューション エクスプ ローラー**をその依存ファイルを表示します。  
  
    > [!NOTE]  
    >  プロジェクトの場合[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]、選択する必要があります、**ビューのすべてのファイル**この手順を実行するボタンをクリックします。  
  
4.  ExpenseReportAssocForm.aspx ファイルのショートカット メニューを開いて**コードの表示**します。  
  
5.  置換、`GetAssociationData`メソッド。  
  
    ```vb  
    Private Function GetAssociationData() As String  
        ' TODO: Return a string that contains the association data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return Me.AutoApproveLimit.Text  
    End Function  
    ```  
  
    ```csharp  
    private string GetAssociationData()  
    {  
        // TODO: Return a string that contains the association data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.AutoApproveLimit.Text;  
    }  
    ```  
  
## <a name="add-an-initiation-form-to-the-workflow"></a>ワークフロー開始フォームを追加します。
 次に、ユーザーに対する経費報告書のワークフローを実行するときに表示される開始フォームを作成します。  
  
#### <a name="to-create-an-initiation-form"></a>開始フォームを作成するには  
  
1.  選択、 **Workflow1**ノード**ソリューション エクスプ ローラー**します。  
  
2.  メニュー バーで、**プロジェクト** > **新しい項目の追加**表示、**新しい項目の追加** ダイアログ ボックス。  
  
3.  ダイアログ ボックスのツリー ビューのいずれかを展開**Visual c#** または**Visual Basic** (プロジェクト言語) に応じて、展開、 **SharePoint**ノード、を選択し**2010**ノード。  
  
4.  テンプレートの一覧で選択、**ワークフロー開始フォーム**テンプレート。  
  
5.  **名前**テキスト ボックスに、入力**ExpenseReportInitForm.aspx**します。  
  
6.  選択、**追加**フォームをプロジェクトに追加するボタンをクリックします。  
  
## <a name="designing-and-coding-the-initiation-form"></a>設計とコーディングの開始フォーム
 次に、コントロールとコードを追加して開始フォームの機能を紹介します。  
  
#### <a name="to-code-the-initiation-form"></a>開始フォームをコーディングするには  
  
1.  開始フォーム (ExpenseReportInitForm.aspx) では、検索、`asp:Content`要素を含む`ID="Main"`します。  
  
2.  直接このコンテンツの要素の最初の行の後に、ラベルと経費承認制限を表示するテキスト ボックスを作成する次のコードを追加 (*AutoApproveLimit*)、関連付けフォームと別のラベルに入力したと経費精算の合計を要求するテキスト ボックス (*ExpenseTotal*)。  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  展開、 **ExpenseReportInitForm.aspx**ファイル**ソリューション エクスプ ローラー**をその依存ファイルを表示します。  
  
4.  ExpenseReportInitForm.aspx ファイルのショートカット メニューを開いて**コードの表示**します。  
  
5.  置換、`Page_Load`メソッドを次の例。  
  
    ```vb  
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As   
      EventArgs) Handles Me.Load  
        InitializeParams()  
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New   
          Guid(associationGuid)).AssociationData  
        ' Optionally, add code here to pre-populate your form fields.  
    End Sub  
    ```  
  
    ```csharp  
    protected void Page_Load(object sender, EventArgs e)  
    {  
        InitializeParams();  
        this.AutoApproveLimit.Text =   
          workflowList.WorkflowAssociations[new   
          Guid(associationGuid)].AssociationData;  
    }  
    ```  
  
6.  置換、`GetInitiationData`メソッドを次の例。  
  
    ```vb  
    ' This method is called when the user clicks the button to start the workflow.  
    Private Function GetInitiationData() As String  
        Return Me.ExpenseTotal.Text  
        ' TODO: Return a string that contains the initiation data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return String.Empty  
    End Function  
    ```  
  
    ```csharp  
    // This method is called when the user clicks the button to start the workflow.          
    private string GetInitiationData()  
    {  
        // TODO: Return a string that contains the initiation data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.ExpenseTotal.Text;  
    }  
    ```  
  
## <a name="cutomize-the-workflow"></a>ワークフローをカスタマイズします
 次に、ワークフローをカスタマイズします。 後は 2 つのフォームをワークフローに関連付けます。  
  
#### <a name="to-customize-the-workflow"></a>ワークフローをカスタマイズするには  
  
1.  プロジェクトで Workflow1 を開くことで、ワークフロー デザイナーでワークフローを表示します。  
  
2.  **ツールボックス**、展開、 **Windows Workflow v3.0**ノードを検索し、 **IfElse**アクティビティ。  
  
3.  次の手順のいずれかの操作を実行することによってこのアクティビティをワークフローに追加します。  
  
    -   ショートカット メニューを開き、 **IfElse**アクティビティ、選択**コピー**、下にある行のショートカット メニューを開き、 **onWorkflowActivated1**ワークフロー デザイナーでアクティビティ選び、**貼り付け**します。  
  
    -   ドラッグ、 **IfElse**からのアクティビティ、**ツールボックス**、および下にある行への接続、 **onWorkflowActiviated1**ワークフロー デザイナーのアクティビティ。  
  
4.  ツールボックスで、展開、 **SharePoint ワークフロー**ノードを検索し、 **CreateTask**アクティビティ。  
  
5.  次の手順のいずれかの操作を実行することによってこのアクティビティをワークフローに追加します。  
  
    -   ショートカット メニューを開き、 **CreateTask**アクティビティ、選択**コピー**、2 つのいずれかのショートカット メニューを開き**ここにアクティビティをドロップ**内の領域**IfElseActivity1** 、ワークフロー デザイナーで選択し**貼り付け**します。  
  
    -   ドラッグ、 **CreateTask**からのアクティビティ、**ツールボックス**、2 つのいずれかに**ここにアクティビティをドロップ**内の領域**IfElseActivity1**します。  
  
6.  **プロパティ** ウィンドウのプロパティ値を入力*taskToken*の**CorrelationToken**プロパティ。  
  
7.  展開、 **CorrelationToken**プラス記号を選択してプロパティ (![TreeView 正符号](../sharepoint/media/plus.gif "TreeView 正符号")) その横にあります。  
  
8.  ドロップダウン矢印を選択、 **OwnerActivityName** sub プロパティ、および設定、 *Workflow1*値。  
  
9. 選択、 **TaskId**プロパティ、省略記号を選択し (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円"))、を表示するボタン**プロパティのバインド** ダイアログ ボックス。  
  
10. 選択、**新しいメンバーへのバインド** タブで、選択、**フィールドの作成**オプション ボタンをクリックして、 **OK**ボタンをクリックします。  
  
11. 選択、 **TaskProperties**プロパティ、省略記号を選択し (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円"))、を表示するボタンをクリックします。**プロパティをバインド** ダイアログ ボックス。  
  
12. 選択、**新しいメンバーへのバインド** タブで、選択、**フィールドの作成**オプション ボタンをクリックして、 **OK**ボタンをクリックします。  
  
13. **ツールボックス**、展開、 **SharePoint ワークフロー**ノードを探し、 **LogToHistoryListActivity**アクティビティ。  
  
14. 次の手順のいずれかの操作を実行することによってこのアクティビティをワークフローに追加します。  
  
    -   ショートカット メニューを開き、 **LogToHistoryListActivity**アクティビティ、選択**コピー**、ショートカット メニューを開き、その他の**ここにアクティビティをドロップ**内の領域**IfElseActivity1** 、ワークフロー デザイナーで選択し**貼り付け**します。  
  
    -   ドラッグ、 **LogToHistoryListActivity**からのアクティビティ、**ツールボックス**、し、もう一方にドロップ**ここにアクティビティをドロップ**内の領域**IfElseActivity1**.  
  
## <a name="add-code-to-the-workflow"></a>コードをワークフローに追加します。
 次に、コードを必要な機能をワークフローに追加します。  
  
#### <a name="to-add-code-to-the-workflow"></a>コードをワークフローに追加するには  
  
1.  ショートカット メニューを開き、 **createTask1**アクティビティ、ワークフロー デザイナーで選択し**コードの表示**します。  
  
2.  次のメソッドを追加します。  
  
    ```vb  
    Private Sub createTask1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        createTask1_TaskId1 = Guid.NewGuid  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report"  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed"  
    End Sub   
    ```  
  
    ```csharp  
    private void createTask1_MethodInvoking(object sender, EventArgs e)  
    {  
        createTask1_TaskId1 = Guid.NewGuid();  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report";  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed";  
    }   
    ```  
  
    > [!NOTE]  
    >  コードでは、置き換える`somedomain\\someuser`作成対象となるタスクは、次のように、ドメインとユーザーの名前を持つ"`Office\\JoeSch`"。 テストで開発しているアカウントを使用する最も簡単なは。  
  
3.  下、`MethodInvoking`メソッドを次の例を追加します。  
  
    ```vb  
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As   
      ConditionalEventArgs)  
        Dim approval As Boolean = False  
        If (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData)) Then  
            approval = True  
        End If  
        e.Result = approval  
    End Sub   
    ```  
  
    ```csharp  
    private void checkApprovalNeeded(object sender, ConditionalEventArgs   
      e)  
    {  
        bool approval = false;  
        if (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData))  
        {  
            approval = true;  
        }  
        e.Result = approval;  
    }   
    ```  
  
4.  ワークフロー デザイナーで、 **ifElseBranchActivity1**アクティビティ。  
  
5.  **プロパティ** ウィンドウのドロップダウン矢印を選択、**条件**プロパティ、および設定して、*コード条件*値。  
  
6.  展開、**条件**プラス記号を選択してプロパティ (![TreeView 正符号](../sharepoint/media/plus.gif "TreeView 正符号"))、その横にあるにその値を設定および*checkApprovalNeeded*.  
  
7.  ワークフロー デザイナーでのショートカット メニューを開き、 **logToHistoryListActivity1**アクティビティを選び、**ハンドラーの生成**の空のメソッドを生成する、`MethodInvoking`イベント。  
  
8.  置換、`MethodInvoking`を次のコード。  
  
    ```vb  
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto   
          approved for " + workflowProperties.InitiationData)  
    End Sub   
    ```  
  
    ```csharp  
    private void logToHistoryListActivity1_MethodInvoking(object sender,   
      EventArgs e)  
    {  
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was   
          auto approved for " + workflowProperties.InitiationData;  
    }   
    ```  
  
9. 選択、 **F5**プログラムをデバッグするキー。  
  
     これは、アプリケーションをコンパイル、ようにパッケージ化、それを展開する、その機能をアクティブ化、リサイクル、[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]アプリケーション プール、およびで指定された場所でブラウザーを開始し、**サイトの Url**プロパティ。  
  
## <a name="associating-the-workflow-to-the-documents-list"></a>ドキュメントの一覧にワークフローの関連付け
 次に、ワークフローに関連付けることによって、ワークフローの関連付けフォームを表示、 **SharedDocuments** SharePoint サイト上のリスト。  
  
#### <a name="to-associate-the-workflow"></a>ワークフローを関連付ける  
  
1.  選択、 **Shared Documents**クイック起動バーにリンクします。  
  
2.  選択、**ライブラリ**リンクを**ライブラリ ツール**タブをクリックして、**ライブラリ設定**リボン ボタンをクリックします。  
  
3.  **権限と管理**セクションで、選択、**ワークフロー設定**リンクをクリックして、**ワークフローに追加**リンクを**のワークフロー**ページ。  
  
4.  ワークフローの設定 ページの上部の一覧で選択、 **ExpenseReport - Workflow1**テンプレート。  
  
5.  [次へ] フィールドに入力**ExpenseReportWorkflow**選択し、**次**ボタン。  
  
     これでワークフローを関連付けます、 **Shared Documents**を一覧表示し、ワークフローの関連付けフォームを表示します。  
  
6.  **自動承認制限**テキスト ボックスに、入力**1200**選択し、**関連付けるワークフロー**ボタンをクリックします。  
  
## <a name="start-the-workflow"></a>ワークフローを開始します。
 次に、内のドキュメントのいずれかにワークフローを関連付ける、 **Shared Documents**ワークフロー開始フォームを表示するリスト。  
  
#### <a name="to-start-the-workflow"></a>ワークフローを開始するには  
  
1.  [SharePoint] ページで、選択、**ホーム**ボタンをクリックします。  
  
2.  選択、 **Shared Documents**リンクを表示する [quicklaunch] バーで、 **Shared Documents**一覧。  
  
3.  選択、**ドキュメント**リンクを**ライブラリ ツール**、ページの上部にあるタブをクリックして、**ドキュメントのアップロード**に新しいドキュメントをアップロードするには、リボン ボタンをクリックします**Shared Documents**一覧。  
  
4.  **ドキュメントのアップロード** ダイアログ ボックスで、選択、**参照**ボタン、任意のドキュメント ファイルを選択して、選択、**オープン**ボタンをクリックし、選択し、 **ok**ボタンをクリックします。  
  
     このダイアログ ボックスで、ドキュメントの設定を変更できますが、そのままにして、既定値を選択して、**保存**ボタンをクリックします。  
  
5.  アップロードしたドキュメントの選択が表示されたらを選択し、ドロップダウン矢印を選択して、**ワークフロー**項目。  
  
6.  ExpenseReportWorkflow の横にあるイメージを選択します。  
  
     これには、ワークフロー開始フォームが表示されます。 (に表示される値に注意してください、**自動承認制限**関連付けフォームで入力したため、ボックスは読み取り専用です)。  
  
7.  **費用合計**テキスト ボックスに、入力**1600**、選択し、**ワークフローの開始**ボタンをクリックします。  
  
     これが表示されます、 **Shared Documents**一覧を再度表示します。 という名前の新しい列**ExpenseReportWorkflow**値を持つ**完了**ワークフローが開始した項目に追加されます。  
  
8.  アップロードしたドキュメントの横にあるドロップダウン矢印を選択し、選択、**ワークフロー**ワークフローの状態 ページを表示する項目。 選択、**完了**値**完了したワークフロー**します。 タスクは、下に表示されます、**タスク**セクション。  
  
9. そのタスクの詳細を表示するタスクのタイトルを選択します。  
  
10. 戻り、 **SharedDocuments**ボックスの一覧し、同じドキュメントまたは別のアカウントを使用して、ワークフローを再開します。  
  
11. [関連付け] ページで入力した値以下である開始ページで金額を入力します (**1200**)。  
  
     この場合、タスクではなく履歴リスト内のエントリが作成されます。 エントリに表示、**ワークフローの履歴**ワークフローの状態 ページのセクション。 内のメッセージに注意してください、**結果**履歴イベントの列。 入力したテキストが含まれている、`logToHistoryListActivity1.MethodInvoking`イベントを自動承認された量が含まれます。  
  
## <a name="next-steps"></a>次の手順
 これらのトピックからワークフロー テンプレートを作成する方法の詳細を確認できます。  
  
-   SharePoint ワークフローの詳細については、次を参照してください。 [Windows SharePoint Services でのワークフロー](http://go.microsoft.com/fwlink/?LinkID=166275)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint ワークフロー ソリューションを作成します。](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [チュートリアル: ワークフローにアプリケーション ページを追加します。](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
