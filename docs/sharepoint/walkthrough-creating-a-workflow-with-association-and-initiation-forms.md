---
title: "チュートリアル: 関連付けフォームと開始フォームをワークフローの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
ms.assetid: c8666d8c-b173-4245-8014-9c1cd6acb071
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b3178c330d34570d1406a1b63368537bc7f66887
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-workflow-with-association-and-initiation-forms"></a>チュートリアル: 関連付けフォームと開始フォームを持つワークフローの作成
  このチュートリアルでは、関連付けフォームと開始フォームの使用が組み込まれている基本的なシーケンシャル ワークフローを作成する方法を示します。 これらは、最初は SharePoint 管理者 (関連付けフォーム) が関連付けられている場合、およびユーザー (開始フォーム) によって、ワークフローの開始時にワークフローに追加するパラメーターを有効にする ASPX フォームです。  
  
 このチュートリアルでは、ユーザーが、次の要件のある経費報告書についての承認ワークフローを作成するシナリオについて概説します。  
  
-   ワークフローが一覧に関連付けられている場合は、管理者は経費報告書について、上限の金額を入力する関連フォームを求められます。  
  
-   従業員は、共有ドキュメント の一覧に、経費報告書をアップロードしたり、ワークフローを開始、経費のワークフロー開始フォームの合計を入力します。  
  
-   合計従業員経費報告書は、管理者の定義済みの上限を超えている場合は、経費報告書を承認する従業員のマネージャーのタスクが作成されます。 ただし、従業員の経費レポートの合計が経費の上限に等しいまたはそれよりも小さい場合は、ワークフローの履歴リストに、自動承認メッセージが書き込まれます。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   SharePoint リスト定義シーケンシャル ワークフロー プロジェクトを作成する[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
-   ワークフローのスケジュールを作成しています。  
  
-   ワークフロー アクティビティのイベントを処理しています。  
  
-   ワークフロー関連付けフォームと開始フォームを作成します。  
  
-   ワークフローを関連付けます。  
  
-   ワークフローを手動で開始します。  
  
> [!NOTE]  
>  このチュートリアルでは、シーケンシャル ワークフロー プロジェクトが、プロセスは、ステート マシン ワークフローで同じです。  
>   
>  別の名前または場所の一部で、コンピューターを表示する場合がありますも、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]次の手順でユーザー インターフェイス要素です。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]のエディションと使用する設定は、これらの要素を決定します。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]および SharePoint。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   Visual Studio  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>SharePoint シーケンシャル ワークフロー プロジェクトを作成します。  
 シーケンシャル ワークフロー プロジェクトを最初に、作成[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 シーケンシャル ワークフローは、最後のアクティビティが終了するまで順番に実行される一連の手順です。 この手順では、SharePoint のドキュメントの共有 の一覧に適用されるシーケンシャル ワークフローを作成します。 ワークフローのウィザードでは、サイトまたはリストの定義とワークフローを関連付けることができ、ワークフローを開始する場合を判断できます。  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>SharePoint シーケンシャル ワークフロー プロジェクトを作成するには  
  
1.  メニュー バーで、次のように選択します。**ファイル**、**新規**、**プロジェクト**を表示する、**新しいプロジェクト** ダイアログ ボックス。  
  
2.  展開、 **SharePoint**ノード**Visual c#**または**Visual Basic**を選択し、 **2010**ノード。  
  
3.  **テンプレート** ウィンドウで、選択、 **SharePoint 2010 プロジェクト**プロジェクト テンプレート。  
  
4.  **名前**ボックスに、入力**ExpenseReport**を選択し、 **OK**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
5.  **デバッグのサイトとセキュリティ レベルを指定して**ページで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックして、**完了**ボタンをクリックして、信頼レベルと既定のサイトです。  
  
     また、この手順は、ワークフロー プロジェクトでのみ使用可能なオプションは、ファーム ソリューションとして、ソリューションの信頼レベルを設定します。  
  
6.  **ソリューション エクスプローラー**で、プロジェクト ノードを選択します。  
  
7.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
8.  いずれかで**Visual c#**または**Visual Basic**、展開、 **SharePoint**  ノードを選択し、 **2010**ノード。  
  
9. **テンプレート** ウィンドウで、選択**シーケンシャル ワークフロー (ファーム ソリューションのみ)**テンプレートを選択し、**追加**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
10. **デバッグのワークフローの名前を指定** ページで、既定の名前 (**ExpenseReport - Workflow1**)。 既定のワークフロー テンプレート型の値を保持 (**リスト ワークフロー)**です。 **[次へ]** ボタンをクリックします。  
  
11. **Visual Studio でデバッグ セッションでワークフローを自動的に関連付けたいですか?**  ページで、ボックスがオンの場合、ワークフロー テンプレートを自動的に関連付けますをオフにします。  
  
     この手順では、手動での関連付けフォームを表示する共有ドキュメント一覧を後でワークフローを関連付けることができます。  
  
12. 選択、**完了**ボタンをクリックします。  
  
## <a name="adding-an-association-form-to-the-workflow"></a>ワークフロー関連付けフォームの追加  
 次に、作成します。ASPX の関連付けフォームを最初に、SharePoint 管理者は、経費報告書ドキュメントにワークフローを関連付ける際に表示されます。  
  
#### <a name="to-add-an-association-form-to-the-workflow"></a>ワークフロー関連付けフォームを追加するには  
  
1.  選択、 **Workflow1**内のノード**ソリューション エクスプ ローラー**です。  
  
2.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**を表示する、**新しい項目の追加** ダイアログ ボックス。  
  
3.  ダイアログ ボックスのツリー ビューのいずれかを展開**Visual c#**または**Visual Basic** (、プロジェクト言語に応じて)、展開、 **SharePoint**  ノード、を選択し**2010**ノード。  
  
4.  テンプレートの一覧で選択、**ワークフロー関連付けフォーム**テンプレート。  
  
5.  **名前**テキスト ボックスに、入力**ExpenseReportAssocForm.aspx**です。  
  
6.  選択、**追加**フォームをプロジェクトに追加するボタンをクリックします。  
  
## <a name="designing-and-coding-the-association-form"></a>設計とコーディングの関連付けフォーム  
 この手順では、コントロールとコードを追加で関連付けフォームに機能を紹介します。  
  
#### <a name="to-design-and-code-the-association-form"></a>デザインとの関連付けフォームのコーディング  
  
1.  関連付けフォーム (ExpenseReportAssocForm.aspx) では、検索、`asp:Content`を持つ要素`ID="Main"`です。  
  
2.  このコンテンツの要素の最初の行のすぐ後に、ラベルと経費承認制限の入力を求めるテキスト ボックスを作成する次のコードを追加 (*AutoApproveLimit*)。  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  展開、 **ExpenseReportAssocForm.aspx**ファイル**ソリューション エクスプ ローラー**をその依存ファイルを表示します。  
  
    > [!NOTE]  
    >  場合は、プロジェクトが含まれて[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]を選択する必要があります、**ビューのすべてのファイル**この手順を実行するボタンをクリックします。  
  
4.  ExpenseReportAssocForm.aspx ファイルのショートカット メニューを開き**コードの表示**です。  
  
5.  置換、`GetAssociationData`を持つメソッド。  
  
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
  
## <a name="adding-an-initiation-form-to-the-workflow"></a>ワークフロー開始フォームを追加します。  
 次に、ユーザーの経費報告書に対するワークフローを実行するときに表示される開始フォームを作成します。  
  
#### <a name="to-create-an-initiation-form"></a>開始フォームを作成するには  
  
1.  選択、 **Workflow1**内のノード**ソリューション エクスプ ローラー**です。  
  
2.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**表示、**新しい項目の追加** ダイアログ ボックス。  
  
3.  ダイアログ ボックスのツリー ビューのいずれかを展開**Visual c#**または**Visual Basic** (、プロジェクト言語に応じて)、展開、 **SharePoint**  ノード、を選択し**2010**ノード。  
  
4.  テンプレートの一覧で選択、**ワークフロー開始フォーム**テンプレート。  
  
5.  **名前**テキスト ボックスに、入力**ExpenseReportInitForm.aspx**です。  
  
6.  選択、**追加**フォームをプロジェクトに追加するボタンをクリックします。  
  
## <a name="designing-and-coding-the-initiation-form"></a>設計とコーディングの開始フォーム  
 次に、コントロールとコードを追加して開始フォームに機能を紹介します。  
  
#### <a name="to-code-the-initiation-form"></a>開始フォームをコーディングするには  
  
1.  開始フォーム (ExpenseReportInitForm.aspx) を見つけて、`asp:Content`要素を含む`ID="Main"`です。  
  
2.  直接このコンテンツの要素の最初の行の後のラベルと経費承認制限を表示するテキスト ボックスを作成する次のコードを追加 (*AutoApproveLimit*) 関連付けフォームと別のラベルに入力したと経費精算の合計を要求するテキスト ボックス (*ExpenseTotal*)。  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  展開、 **ExpenseReportInitForm.aspx**ファイル**ソリューション エクスプ ローラー**をその依存ファイルを表示します。  
  
4.  ExpenseReportInitForm.aspx ファイルのショートカット メニューを開き**コードの表示**です。  
  
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
  
## <a name="customizing-the-workflow"></a>ワークフローのカスタマイズ  
 次に、ワークフローをカスタマイズします。 後で、次の 2 つのフォームをワークフローに関連付けます。  
  
#### <a name="to-customize-the-workflow"></a>ワークフローをカスタマイズするには  
  
1.  プロジェクトで Workflow1 を開くことで、ワークフロー デザイナーでワークフローを表示します。  
  
2.  **ツールボックス**、展開、 **Windows Workflow v3.0**ノードを検索し、 **IfElse**アクティビティ。  
  
3.  次の手順のいずれかの操作を実行することによってこのアクティビティをワークフローに追加します。  
  
    -   ショートカット メニューを開き、 **IfElse** 、アクティビティを選択**コピー**、下にある行のショートカット メニューを開き、 **onWorkflowActivated1**ワークフロー デザイナーでアクティビティクリックして**貼り付け**です。  
  
    -   ドラッグ、 **IfElse**からアクティビティを**ツールボックス**、下の行に接続し、 **onWorkflowActiviated1**ワークフロー デザイナーでアクティビティ。  
  
4.  ツールボックスで、展開、 **SharePoint ワークフロー**ノードを検索し、 **CreateTask**アクティビティ。  
  
5.  次の手順のいずれかの操作を実行することによってこのアクティビティをワークフローに追加します。  
  
    -   ショートカット メニューを開き、 **CreateTask**アクティビティを選択して**コピー**、ショートカット メニューを開き、2 つのいずれかの**ここにアクティビティをドロップ**内の領域**IfElseActivity1**ワークフロー デザイナーで選択し**貼り付け**です。  
  
    -   ドラッグ、 **CreateTask**からアクティビティを**ツールボックス**、2 つのいずれかに**ここにアクティビティをドロップ**内の領域**IfElseActivity1**です。  
  
6.  **プロパティ** ウィンドウのプロパティ値を入力*taskToken*の**CorrelationToken**プロパティです。  
  
7.  展開、 **CorrelationToken**プラス記号を選択してプロパティ (![TreeView 正符号](../sharepoint/media/plus.gif "TreeView 正符号"))、横にあります。  
  
8.  ドロップダウン矢印を選択して、 **OwnerActivityName** sub プロパティ、および設定、 *Workflow1*値。  
  
9. 選択、 **TaskId**プロパティを選択し、省略記号 (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円"))、を表示するにはボタン**プロパティのバインド** ダイアログ ボックス。  
  
10. 選択、**新しいメンバーへのバインド** タブで、選択、**フィールドの作成**オプション ボタンをクリックして、 **OK**ボタンをクリックします。  
  
11. 選択、 **TaskProperties**プロパティを選択し、省略記号 (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円"))、を表示するボタンをクリックします。**プロパティはバインド** ダイアログ ボックス。  
  
12. 選択、**新しいメンバーへのバインド** タブで、選択、**フィールドの作成**オプション ボタンをクリックして、 **OK**ボタンをクリックします。  
  
13. **ツールボックス**、展開、 **SharePoint ワークフロー**  ノードを検索し、 **LogToHistoryListActivity**アクティビティ。  
  
14. 次の手順のいずれかの操作を実行することによってこのアクティビティをワークフローに追加します。  
  
    -   ショートカット メニューを開き、 **LogToHistoryListActivity** 、アクティビティを選択**コピー**、ショートカット メニューを開き、他の**ここにアクティビティをドロップ**内の領域**IfElseActivity1**ワークフロー デザイナーで選択し**貼り付け**です。  
  
    -   ドラッグ、 **LogToHistoryListActivity**からアクティビティを**ツールボックス**、し、他のドロップ**ここにアクティビティをドロップ**内の領域**IfElseActivity1**.  
  
## <a name="adding-code-to-the-workflow"></a>ワークフローにコードを追加します。  
 次に、コードを必要な機能をワークフローに追加します。  
  
#### <a name="to-add-code-to-the-workflow"></a>ワークフローにコードを追加するには  
  
1.  ショートカット メニューを開き、 **createTask1**ワークフロー デザイナーでアクティビティを選択し**コードの表示**です。  
  
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
    >  コードでは、置換`somedomain\\someuser`作成対象となるタスクはのように、ドメインとユーザー名と"`Office\\JoeSch`"です。 テストを開発しているアカウントを使用する最も簡単です。  
  
3.  下、`MethodInvoking`メソッドでは、次の例を追加します。  
  
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
  
5.  **プロパティ** ウィンドウのドロップダウン矢印をクリックして、**条件**プロパティ、および設定、*コード条件*値。  
  
6.  展開、**条件**プラス記号を選択してプロパティ (![TreeView 正符号](../sharepoint/media/plus.gif "TreeView 正符号"))、横にあるし、その値に設定および*checkApprovalNeeded*.  
  
7.  ワークフロー デザイナーでのショートカット メニューを開き、 **logToHistoryListActivity1** 、アクティビティを選択し**生成ハンドラー**の空のメソッドを生成する、`MethodInvoking`イベント。  
  
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
  
9. プログラムをデバッグする F5 キーを押します。  
  
     これは、アプリケーションをコンパイル、ようにパッケージ、展開、その機能をアクティブに、リサイクル、[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]アプリケーション プール、およびで指定された場所に、ブラウザー、開始、**サイト Url**プロパティです。  
  
## <a name="associating-the-workflow-to-the-documents-list"></a>ドキュメントの一覧に、ワークフローの関連付け  
 次に、ワークフローに関連付けることによって、ワークフローの関連付けフォームを表示、 **SharedDocuments** SharePoint サイト上のリスト。  
  
#### <a name="to-associate-the-workflow"></a>ワークフローを関連付ける  
  
1.  選択、 **Shared Documents**クイック起動バー上にリンクします。  
  
2.  選択、**ライブラリ**リンクを**ライブラリ ツール**タブを選び、**ライブラリ設定**リボン ボタンをクリックします。  
  
3.  **権限と管理**セクションで、選択、**ワークフロー設定**リンクしを選択し、 **、ワークフローの追加**リンクを**のワークフロー**ページ。  
  
4.  一覧で、最上位ワークフロー設定 ページで、選択、 **ExpenseReport - Workflow1**テンプレート。  
  
5.  次のフィールドに入力**ExpenseReportWorkflow**を選択し、**次**ボタンをクリックします。  
  
     これは、ワークフローに関連付けます、 **Shared Documents**を一覧表示し、ワークフローの関連付けフォームを表示します。  
  
6.  **自動承認制限**テキスト ボックスに、入力**1200**を選択し、**関連付けるワークフロー**ボタンをクリックします。  
  
## <a name="starting-the-workflow"></a>ワークフローの開始  
 次に、内のドキュメントのいずれかにワークフローを関連付ける、 **Shared Documents**ワークフロー開始フォームを表示するリスト。  
  
#### <a name="to-start-the-workflow"></a>ワークフローを開始するには  
  
1.  [SharePoint] ページで、選択、**ホーム**ボタンをクリックします。  
  
2.  選択、 **Shared Documents** 、クイック起動バーを表示するリンク、 **Shared Documents**  ボックスの一覧です。  
  
3.  選択、**ドキュメント**リンクを**ライブラリ ツール**、ページの上部にあるタブを選び、**ドキュメントのアップロード**に新しいドキュメントをアップロードするには、リボンのボタンをクリックします**Shared Documents**  ボックスの一覧です。  
  
4.  **ドキュメントのアップロード** ダイアログ ボックスで、選択、**参照**ボタン、任意のドキュメント ファイルを選択して、選択、**開く**ボタンをクリックしを選択し、 **ok**ボタンをクリックします。  
  
     このダイアログ ボックスで、ドキュメントの設定を変更できますが、値のままにして、既定値を選択して、**保存**ボタンをクリックします。  
  
5.  アップロードしたドキュメントの選択が表示されたらを選択し、ドロップダウン矢印を選択して、**ワークフロー**項目。  
  
6.  ExpenseReportWorkflow の横にあるイメージを選択します。  
  
     ワークフロー開始フォームが表示されます。 (注値に表示される、**自動承認制限**関連付けフォームで入力したためボックスは読み取り専用です)。  
  
7.  **経費合計**テキスト ボックスに、入力**1600**を選択し、**ワークフローの開始**ボタンをクリックします。  
  
     これが表示されます、 **Shared Documents**一覧を再度表示します。 という名前の新しい列**ExpenseReportWorkflow**値を持つ**完了**ワークフローを開始した項目に追加します。  
  
8.  アップロードしたドキュメントの横にあるドロップダウン矢印を選択し、[、**ワークフロー**ワークフローの状態] ページを表示する項目。 選択、**完了**値の下にある**完了したワークフロー**です。 タスクに表示される、**タスク**セクションです。  
  
9. そのタスクの詳細を表示するタスクのタイトルを選択します。  
  
10. 戻り、 **SharedDocuments**を一覧表示し、同じドキュメントまたは別のいずれかを使用して、ワークフローを再起動します。  
  
11. アソシエーション ページで入力した値以下である開始 ページで、金額を入力 (**1200**)。  
  
     この場合、タスクではなく、履歴リスト内のエントリが作成されます。 エントリに表示、**ワークフロー履歴**ワークフローの状態 ページのセクションです。 内のメッセージに注意してください、**結果**履歴イベントの列にします。 入力したテキストが含まれている、`logToHistoryListActivity1.MethodInvoking`イベントを自動承認されました、量が含まれています。  
  
## <a name="next-steps"></a>次の手順  
 これらのトピックからワークフロー テンプレートを作成する方法の詳細を学習できます。  
  
-   SharePoint ワークフローの詳細については、次を参照してください。 [Windows SharePoint Services でのワークフロー](http://go.microsoft.com/fwlink/?LinkID=166275)です。  
  
## <a name="see-also"></a>参照  
 [SharePoint ワークフロー ソリューションを作成します。](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [チュートリアル: ワークフローへのアプリケーション ページの追加](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  