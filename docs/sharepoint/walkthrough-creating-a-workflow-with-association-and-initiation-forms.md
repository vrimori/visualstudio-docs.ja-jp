---
title: "チュートリアル: 関連付けフォームと開始フォームを持つワークフローの作成"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "関連付けフォーム [Visual Studio での SharePoint 開発]"
  - "開始フォーム [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, ワークフロー関連付けフォーム"
  - "Visual Studio での SharePoint 開発, ワークフロー開始フォーム"
  - "Visual Studio での SharePoint 開発, ワークフロー"
  - "ワークフロー [Visual Studio での SharePoint 開発]"
ms.assetid: c8666d8c-b173-4245-8014-9c1cd6acb071
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# チュートリアル: 関連付けフォームと開始フォームを持つワークフローの作成
  このチュートリアルでは、組み込まれたかたちで関連付けフォームと開始フォームを使用する基本的なシーケンシャル ワークフローの作成方法について説明します。  関連付けフォームと開始フォームは、それぞれ、SharePoint 管理者が初めてワークフローの関連付けを行うときと、ユーザーがワークフローを開始するときに、ワークフローにパラメーターが追加されるようにする ASPX フォームです。  
  
 このチュートリアルでは、次の要件を満たす経費明細書承認ワークフローを作成します。  
  
-   管理者がワークフローをリストに関連付けようとすると、関連付けフォームが表示され、経費明細書の上限金額を入力するよう求められます。  
  
-   従業員は各自の経費明細書を共有ドキュメント リストにアップロードしてワークフローを開始し、経費の合計をワークフローの開始フォームに入力します。  
  
-   従業員の経費明細書の合計が、管理者によってあらかじめ定義された上限を超えている場合は、その従業員の上司が経費明細書を承認するためのタスクが作成されます。  従業員の経費明細書の合計が経費の上限と等しい場合、またはそれよりも少ない場合は、自動承認メッセージがワークフローの履歴リストに書き込まれます。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   SharePoint リスト定義シーケンシャル ワークフロー プロジェクトを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で作成する。  
  
-   ワークフロー スケジュールを作成する。  
  
-   ワークフロー アクティビティのイベントを処理する。  
  
-   ワークフローの関連付けフォームと開始フォームを作成する。  
  
-   ワークフローを関連付ける。  
  
-   ワークフローを手動で開始する。  
  
> [!NOTE]  
>  このチュートリアルではシーケンシャル ワークフロー プロジェクトを使用していますが、ステート マシン ワークフローでも手順は同じです。  
>   
>  また、次の手順で参照している [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前または場所が異なる場合があります。  これらの要素は、使用する [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] および SharePoint。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   Visual Studio  
  
## SharePoint シーケンシャル ワークフロー プロジェクトの作成  
 まず、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] でシーケンシャル ワークフロー プロジェクトを作成します。  シーケンシャル ワークフローは、最後のアクティビティが完了するまで順番に実行される一連の手順です。  この手順では、SharePoint の共有ドキュメント リストに適用するシーケンシャル ワークフローを作成します。  ワークフローのウィザードを使用すると、サイト定義またはリスト定義のいずれかにワークフローを関連付けることができ、またワークフローを開始するタイミングを指定することができます。  
  
#### SharePoint シーケンシャル ワークフロー プロジェクトを作成するには  
  
1.  メニュー バーで、**\[新しいプロジェクト\]** ダイアログ ボックスを表示するには、**\[新規作成\]**、**\[プロジェクト\]\[ファイル\]** をクリックします。  
  
2.  **\[SharePoint\]** ノードを **\[Visual C\#\]** または **\[Visual Basic\]** で展開し、**2010** ノードを選択します。  
  
3.  **\[テンプレート\]** のペインで、**\[SharePoint 2010 プロジェクト\]** プロジェクト テンプレートを選択します。  
  
4.  **\[名前\]** ボックスで、ExpenseReport "と入力し、**\[OK\]** ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
5.  **\[デバッグのサイトとセキュリティ レベルの指定\]** ページで、**\[ファーム ソリューションとして配置する\]** のオプション ボタンを選択し、信頼レベルと既定のサイトを受け入れるように **\[完了\]** ボタンをクリックします。  
  
     また、この段階で、ソリューションの信頼レベルがファーム ソリューション \(ワークフロー プロジェクトではこれ以外は選択できません\) として設定されます。  
  
6.  **ソリューション エクスプローラー**で、プロジェクト ノードを選択します。  
  
7.  メニュー バーで **\[プロジェクト\]**、**\[新しい項目の追加\]** の順に選択します。  
  
8.  **\[Visual C\#\]** または **\[Visual Basic\]** で、**\[SharePoint\]** ノードを展開し、**2010** ノードを選択します。  
  
9. **\[テンプレート\]** のペインでテンプレートを **\[シーケンシャル ワークフロー \(ファーム ソリューションのみ\)\]** をクリックします、**\[追加\]** ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
10. **\[デバッグのワークフロー名の指定\]** ページで、既定の名前 \(**ExpenseReport \- Workflow1**\) を受け入れます。  既定のワークフロー テンプレートの種類である **\[リスト ワークフロー\]** を受け入れます。  **\[次へ\]** ボタンをクリックします。  
  
11. **\[デバッグ セッション中に Visual Studio によってワークフローが自動的に関連付けられるようにする\]** ページで、ワークフロー テンプレートを自動的に関連付けるためのチェック ボックスがオンの場合は、チェック ボックスをオフにします。  
  
     この手順によって、後で関連付けフォームを表示し、ワークフローを共有ドキュメント リストに手動で関連付けることができます。  
  
12. **\[完了\]** をクリックします。  
  
## ワークフローへの関連付けフォームの追加  
 次に、SharePoint 管理者が初めてワークフローを経費明細書ドキュメントに関連付けるときに表示される .ASPX 形式の関連付けフォームを作成します。  
  
#### ワークフローに関連付けフォームを追加するには  
  
1.  **\[ソリューション エクスプローラー\]** の **\[Workflow1\]** ノードを選択します。  
  
2.  メニュー バーで、**\[新しいアイテムの追加\]** ダイアログ ボックスを表示するには、**\[新しいアイテムの追加\]\[プロジェクト\]** をクリックします。  
  
3.  ダイアログ ボックスのツリー ビューで、**\[Visual C\#\]** または **\[Visual Basic \]**  \(プロジェクトの言語によって\) を展開し、**\[SharePoint\]** ノードを展開し、**2010** ノードを選択します。  
  
4.  テンプレートの一覧で、**\[ワークフロー関連付けフォーム\]** テンプレートを選択します。  
  
5.  **\[名前\]** のテキスト ボックスに" ExpenseReportAssocForm.aspx "と入力します。  
  
6.  プロジェクトにフォームを追加するに **\[追加\]** ボタンをクリックします。  
  
## 関連付けフォームのデザインとコーディング  
 この手順では、関連付けフォームにコントロールとコードを追加して必要な機能を組み込みます。  
  
#### 関連付けフォームのデザインとコーディングを行うには  
  
1.  関連フォーム \(ExpenseReportAssocForm.aspx\) で、`ID="Main"` の `asp:Content` 要素を特定します。  
  
2.  このコンテンツ要素の先頭行の直後に次のコードを追加して、承認する経費の上限 \(*AutoApproveLimit*\) を入力するよう求めるラベルとテキスト ボックスを作成します。  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  **ソリューション エクスプローラー**で **ExpenseReportAssocForm.aspx** ファイルを展開して、その依存ファイルを表示します。  
  
    > [!NOTE]  
    >  プロジェクトが [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]にある場合は、この手順を実行するに **\[すべてのファイルを表示します。\]** ボタンを選択する必要があります。  
  
4.  ExpenseReportAssocForm.aspx ファイルのショートカット メニューを開き、**\[コードの表示\]** をクリックします。  
  
5.  `GetAssociationData` メソッドを次のコードに置き換えます。  
  
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
  
## ワークフローへの開始フォームの追加  
 次に、ユーザーが各自の経費明細書に対してワークフローを実行すると表示される開始フォームを作成します。  
  
#### 開始フォームを作成するには  
  
1.  **\[ソリューション エクスプローラー\]** の **\[Workflow1\]** ノードを選択します。  
  
2.  メニュー バーで、**\[新しいアイテムの追加\]** の表示 **\[新しいアイテムの追加\]** ダイアログ ボックス **\[プロジェクト\]** をクリックします。  
  
3.  ダイアログ ボックスのツリー ビューで、**\[Visual C\#\]** または **\[Visual Basic \]**  \(プロジェクトの言語によって\) を展開し、**\[SharePoint\]** ノードを展開し、**2010** ノードを選択します。  
  
4.  テンプレートの一覧で、**\[ワークフロー開始フォーム\]** テンプレートを選択します。  
  
5.  **\[名前\]** のテキスト ボックスに" ExpenseReportInitForm.aspx "と入力します。  
  
6.  プロジェクトにフォームを追加するに **\[追加\]** ボタンをクリックします。  
  
## 開始フォームのデザインとコーディング  
 次に、開始フォームにコントロールとコードを追加して必要な機能を組み込みます。  
  
#### 開始フォームのコーディングをするには  
  
1.  初期化フォーム \(ExpenseReportInitForm.aspx\) で、`ID="Main"`を含む `asp:Content` 要素を見つけます。  
  
2.  このコンテンツ要素の先頭行の直後に、次のコードを追加して、関連付けフォームで入力された承認する経費の上限 \(*AutoApproveLimit*\) を表示するラベルとテキスト ボックス、および経費の合計 \(*ExpenseTotal*\) を入力するよう求めるラベルとテキスト ボックスを作成します。  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  **ソリューション エクスプローラー**で **ExpenseReportInitForm.aspx** ファイルを展開して、その依存ファイルを表示します。  
  
4.  ExpenseReportInitForm.aspx ファイルのショートカット メニューを開き、**\[コードの表示\]** をクリックします。  
  
5.  `Page_Load` メソッドを次のコード例に置き換えます。  
  
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
  
6.  `GetInitiationData` メソッドを次のコード例に置き換えます。  
  
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
  
## ワークフローのカスタマイズ  
 次に、ワークフローをカスタマイズします。  後で 2 つのフォームをワークフローに関連付けます。  
  
#### ワークフローをカスタマイズするには  
  
1.  プロジェクトの Workflow1 を起動して、ワークフロー デザイナーにワークフローを表示します。  
  
2.  **\[ツールボックス\]** で、**\[Windows Workflow v3.0\]** ノードを展開し、**\[IfElse\]** アクティビティを探します。  
  
3.  次の手順の実行 1 かによってこのアクティビティをワークフローに追加します:  
  
    -   **\[IfElse\]** アクティビティのショートカット メニューを開き、**\[コピー\]** をクリックします、行のショートカット メニューをワークフロー デザイナーの **\[onWorkflowActivated1\]** アクティビティで開き、**\[貼り付け\]** をクリックします。  
  
    -   **\[ツールボックス\]** から **\[IfElse\]** アクティビティをドラッグし、行は、ワークフロー デザイナーの **\[onWorkflowActiviated1\]** アクティビティの下に接続します。  
  
4.  ツールボックスの **\[SharePoint ワークフロー\]** ノードを展開し、**\[CreateTask\]** アクティビティを探します。  
  
5.  次の手順の実行 1 かによってこのアクティビティをワークフローに追加します:  
  
    -   **\[CreateTask\]** アクティビティのショートカット メニューを開き、**\[コピー\]** をクリックします、ワークフロー デザイナーの IfElseActivity1 内の **\[ここにアクティビティをドロップします\]** の 2 種類の領域の 1 種類のショートカット メニューを開き、**\[貼り付け\]** をクリックします。  
  
    -   IfElseActivity1 内に **\[ここにアクティビティをドロップします\]** の 2 種類の領域の 1 種類に **\[ツールボックス\]** から **\[CreateTask\]** アクティビティをドラッグします。  
  
6.  **\[プロパティ\]** ウィンドウで、**CorrelationToken** プロパティの *taskToken* のプロパティ値を入力します。  
  
7.  名の横にある正符号をクリックして **CorrelationToken** のプロパティ \(![TreeView 正符号](../sharepoint/media/plus.png "TreeView 正符号")\) を展開します。  
  
8.  **OwnerActivityName** subs プロパティのドロップダウン矢印をクリックし、*Workflow1* 値を設定します。  
  
9. **TaskId** のプロパティを選択し、**\[プロパティのバインド\]** ダイアログ ボックスを表示するには、省略記号 \(![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.png "ASP.NET モバイル デザイナー楕円")\) ボタンをクリックします。  
  
10. **\[新しいメンバーへのバインド\]** タブを選択し、**\[フィールドの作成\]** のオプション ボタンを選択し、**\[OK\]** ボタンをクリックします。  
  
11. **TaskProperties** のプロパティを選択し、**\[プロパティのバインド\]** ダイアログ ボックスを表示するには、省略記号 \(![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.png "ASP.NET モバイル デザイナー楕円")\) ボタンをクリックします。  
  
12. **\[新しいメンバーへのバインド\]** タブを選択し、**\[フィールドの作成\]** のオプション ボタンを選択し、**\[OK\]** ボタンをクリックします。  
  
13. **\[ツールボックス\]** で、**\[SharePoint ワークフロー\]** ノードを展開し、**\[LogToHistoryListActivity\]** アクティビティを探します。  
  
14. 次の手順の実行 1 かによってこのアクティビティをワークフローに追加します:  
  
    -   **\[LogToHistoryListActivity\]** アクティビティのショートカット メニューを開き、**\[コピー\]** をクリックします、ワークフロー デザイナーの IfElseActivity1 内の **\[ここにアクティビティをドロップします\]** の他の領域のショートカット メニューを開き、**\[貼り付け\]** をクリックします。  
  
    -   **\[ツールボックス\]** から **\[LogToHistoryListActivity\]** アクティビティをドラッグし、IfElseActivity1 内の **\[ここにアクティビティをドロップします\]** の他の領域にドロップします。  
  
## ワークフローへのコードの追加  
 次に、ワークフローにコードを追加して、必要な機能を実装します。  
  
#### ワークフローにコードを追加するには  
  
1.  ワークフロー デザイナーで **\[createTask1\]** アクティビティのショートカット メニューを開き、**\[コードの表示\]** をクリックします。  
  
2.  次のメソッドを追加する:  
  
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
    >  コード内の `somedomain\\someuser` の部分を、タスクの作成対象のドメインとユーザー名に置き換えます \(例: "`Office\\JoeSch`"\)。  テストの目的では、開発用のアカウントを使用するのが最も簡単です。  
  
3.  `MethodInvoking` メソッドの下に、次のコード例を追加します。  
  
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
  
4.  ワークフロー デザイナーで、**\[ifElseBranchActivity1\]** アクティビティをクリックします。  
  
5.  **\[プロパティ\]** ウィンドウで、**\[条件\]** のプロパティのドロップダウン矢印をクリックし、*Code Condition* 値を設定します。  
  
6.  **\[条件\]** のプロパティをプラス記号の選択 \(![TreeView 正符号](../sharepoint/media/plus.png "TreeView 正符号")\) によってその横の展開し、*checkApprovalNeeded*に値を設定します。  
  
7.  ワークフロー デザイナーで、**\[logToHistoryListActivity1\]** アクティビティのショートカット メニューを開き、`MethodInvoking` イベントに対する空のメソッドを生成する **\[ハンドラーの生成\]** をクリックします。  
  
8.  `MethodInvoking` コードを次の内容に置き換えます。  
  
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
  
9. プログラムをデバッグするには、F5 キーを押します。  
  
     これで、アプリケーションがコンパイルされ、パッケージ化されて配置されます。さらに、そのフィーチャーがアクティブ化され、[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] アプリケーション プールがリサイクルされて、ブラウザーが起動されます。このとき、ブラウザーには、**\[サイト URL\]** プロパティで指定されている場所が表示されます。  
  
## ドキュメント リストへのワークフローの関連付け  
 次に、SharePoint サイトの**共有ドキュメント** リストにワークフローを関連付けることによって、ワークフローの関連付けフォームを表示します。  
  
#### ワークフローを関連付けるには  
  
1.  クイック起動バーの **\[共有ドキュメント\]** リンクをクリックします。  
  
2.  **\[ライブラリ ツール\]** タブの **\[ライブラリ\]** リンクを選択し、**\[ライブラリの設定\]** のリボン ボタンをクリックします。  
  
3.  **\[権限と管理\]** セクションで、**\[ワークフロー設定\]** リンクを選択し、**\[ワークフロー\]** ページの **\[ワークフローの追加\]** リンクをクリックします。  
  
4.  ワークフローの設定の上部にある一覧で **\[ExpenseReport \- Workflow1\]** のテンプレートのページングを選択します。  
  
5.  次のフィールドに" ExpenseReportWorkflow "と入力し、**\[次へ\]** ボタンをクリックします。  
  
     これにより、ワークフローと**共有ドキュメント** リストが関連付けられ、ワークフローの関連付けフォームが表示されます。  
  
6.  **\[Auto Approval Limit\]** のテキスト ボックスに、" 1200 "と入力し、**\[ワークフローの関連付け\]** ボタンをクリックします。  
  
## ワークフローの開始  
 次に、**共有ドキュメント** リストのいずれかのドキュメントにワークフローを関連付けて、ワークフローの開始フォームを表示します。  
  
#### ワークフローを開始するには  
  
1.  SharePoint ページで、**\[ホーム\]** ボタンをクリックします。  
  
2.  **\[共有ドキュメント\]** の一覧を表示するには、クイック起動バーの **\[共有ドキュメント\]** リンクをクリックします。  
  
3.  **\[ライブラリ ツール\]** タブの **\[ドキュメント\]** リンクをページの一番上にある選択し、**\[共有ドキュメント\]** の一覧に新しいドキュメントをアップロードするに **\[ドキュメントのアップロード\]** リボンのボタンをクリックします。  
  
4.  **\[ドキュメントのアップロード\]** ダイアログ ボックスで、**\[参照\]** ボタンを選択し、ドキュメント ファイルを選択し、**\[開く\]** ボタンをクリックし、**\[OK\]** ボタンをクリックします。  
  
     このダイアログ ボックスのドキュメントの設定を変更できますが既定値で **\[保存\]** ボタンをクリックすると、これらが保存されます。  
  
5.  アップロードしたドキュメントを選択し、表示をクリックし、**\[ワークフロー\]** 項目をドロップダウン矢印をクリックします。  
  
6.  ExpenseReportWorkflow の横に表示されるイメージをクリックします。  
  
     これでワークフローの開始フォームが表示されます。**\[Auto Approval Limit\]** ボックスに表示される値は、関連付けフォームで入力された値であるため読み取り専用です。  
  
7.  **\[経費の合計\]** のテキスト ボックスに、" 1600 "と入力し、**\[ワークフローの開始\]** ボタンをクリックします。  
  
     **共有ドキュメント** リストが再度表示されます。  たった今ワークフローによって開始された項目に、**ExpenseReportWorkflow** という新しい列が追加され、列の値は **\[完了\]** になっています。  
  
8.  ドロップダウン矢印をアップロードするドキュメントの横に選択し、ワークフローの状態ページを表示するに **\[ワークフロー\]** 項目を選択します。  **\[完了したワークフロー\]** で **\[完了\]** 値を選択します。  **\[タスク\]** セクションにタスクが表示されます。  
  
9. タスクの詳細を表示するタスクのタイトルをクリックします。  
  
10. **共有ドキュメント** リストに戻り、同じドキュメントまたは別のドキュメントを使用して再度ワークフローを開始します。  
  
11. 関連付けページで入力した値 \(1200\) 以下である開始ページの金額を入力します。  
  
     この場合、タスクは作成されずに、履歴リストのエントリが作成されます。  このエントリは、ワークフローの状態ページの **\[ワークフローの履歴\]** セクションに表示されます。  履歴イベントの **\[結果\]** 列に表示されたメッセージに注目してください。  `logToHistoryListActivity1.MethodInvoking` イベントで入力したテキスト \(自動承認された金額を含む\) が出力されています。  
  
## 次の手順  
 ワークフロー テンプレートの作成方法の詳細については、以下のトピックを参照してください。  
  
-   SharePoint のワークフローの詳細については、"参照してください [Windows SharePoint Services のワークフロー](http://go.microsoft.com/fwlink/?LinkID=166275)。  
  
## 参照  
 [SharePoint ワークフロー ソリューションの作成](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [チュートリアル: ワークフローへのアプリケーション ページの追加](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  