---
title: "チュートリアル: を作成して、SharePoint ワークフロー ソリューションのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
ms.assetid: 81756490-ab5a-4fa4-96c6-eed2cfbf8374
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d64c0767cce43d5b157fca82cc3e1e210a2f8c58
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-and-debugging-a-sharepoint-workflow-solution"></a>チュートリアル : SharePoint ワークフロー ソリューションの作成とデバッグ
  このチュートリアルでは、基本的なシーケンシャル ワークフロー テンプレートを作成する方法を示します。 ワークフローでは、ドキュメントが確認されていないかどうかを決定する共有ドキュメント ライブラリのプロパティを確認します。 ドキュメントをレビューすると、ワークフローが終了します。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   SharePoint リスト定義シーケンシャル ワークフロー プロジェクトを作成する[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
-   ワークフロー アクティビティを作成します。  
  
-   ワークフロー アクティビティのイベントを処理しています。  
  
> [!NOTE]  
>  このチュートリアルでは、シーケンシャル ワークフロー プロジェクトでは、プロセスはステート マシン ワークフロー プロジェクトに同じです。  
>   
>  コンピューター可能性があります異なる名前や場所がいくつかの Visual Studio ユーザー インターフェイス要素次の手順でします。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   Visual Studio  
  
## <a name="adding-properties-to-the-sharepoint-shared-documents-library"></a>プロパティを SharePoint に追加する共有ドキュメント ライブラリ  
 内のドキュメントの確認の状態を追跡するために、 **Shared Documents**ライブラリの SharePoint サイトで共有ドキュメントの次の 3 つの新しいプロパティを作成します: `Status`、 `Assignee`、および`Review Comments`です。 これらのプロパティを定義して、 **Shared Documents**ライブラリです。  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>SharePoint の共有にプロパティを追加するには、と、ドキュメント ライブラリ  
  
1.  Http:// など、SharePoint サイトを開きます。\<システム名 >/SitePages/Home.aspx、Web ブラウザーでします。  
  
2.  クイック起動バーで、次のように選択します。 **SharedDocuments**です。  
  
3.  選択**ライブラリ**で、**ライブラリ ツール**のリボンし、を選択し、**列の作成**新しい列を作成するには、リボンのボタンをクリックします。  
  
4.  列の名前**ドキュメントの状態**、その型に設定**選択肢 (メニューから選択)**、次の 3 つのオプションを指定し、選択、 **OK**ボタン。  
  
    -   **必要なレビュー**  
  
    -   **確認の完了**  
  
    -   **要求された変更**  
  
5.  2 つ以上の列を作成し、名前を付ける**担当者**と**レビュー コメント**です。 複数行のテキストとしての割り当て先列の型を 1 行のテキスト、およびレビューのコメント列のデータ型を設定します。  
  
## <a name="enabling-documents-to-be-edited-without-requiring-a-check-out"></a>ドキュメントをチェック アウトを必要とせずに編集できるを有効にします。  
 チェック アウトすることがなく、ドキュメントを編集するときに、ワークフロー テンプレートをテストする簡単です。次の手順では、実現するために、SharePoint サイトを構成します。  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>それらをチェック アウトしないで編集するドキュメントを有効にするには  
  
1.  クイック起動バーで、選択、 **Shared Documents**リンクします。  
  
2.  **ライブラリ ツール**リボンで、選択、**ライブラリ** タブをクリックして、**ライブラリの設定**を表示するボタン、 **ドキュメントライブラリの設定**ページ。  
  
3.  **全般設定**セクションで、選択、**バージョン設定**表示へのリンク、**バージョン設定**ページ。  
  
4.  いることを確認の設定**ドキュメントを編集する前にチェック アウトを必要と**は**いいえ**です。 そうでない場合に変更して**いいえ**を選択し、 **OK**ボタンをクリックします。  
  
5.  ブラウザーを閉じます。  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>SharePoint シーケンシャル ワークフロー プロジェクトを作成します。  
 シーケンシャル ワークフローは、最後のアクティビティが終了するまで順番に実行する手順のセットです。 この手順が、共有ドキュメント リストに適用されるシーケンシャル ワークフローを作成します。 ワークフロー ウィザードでのサイト定義、または、リスト定義、ワークフローを関連付けることができ、ワークフローを開始する場合を判断できます。  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>SharePoint シーケンシャル ワークフロー プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで、次のように選択します。**ファイル**、**新規**、**プロジェクト**を表示する、**新しいプロジェクト** ダイアログ ボックス。  
  
3.  展開、 **SharePoint**ノード**Visual c#**または**Visual Basic**を選択し、 **2010**ノード。  
  
4.  **テンプレート** ウィンドウで、選択、 **SharePoint 2010 プロジェクト**テンプレート。  
  
5.  **名前**ボックスに、入力**MySharePointWorkflow**を選択し、 **OK**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
6.  **デバッグのサイトとセキュリティ レベルを指定して**ページで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックして、**完了**ボタンをクリックして、信頼レベルと既定のサイトです。  
  
     この手順では、ファーム ソリューションでは、ワークフロー プロジェクトでのみ使用可能なオプションとして、ソリューションの信頼レベルを設定します。 詳細については、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)です。  
  
7.  **ソリューション エクスプ ローラー**、プロジェクト ノードを選択し、次に、メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
8.  いずれかで**Visual c#**または**Visual Basic**、展開、 **SharePoint**  ノードを選択し、 **2010**ノード。  
  
9. **テンプレート** ウィンドウで、選択、**シーケンシャル ワークフロー (ファーム ソリューションのみ)**テンプレートを選択し、**追加**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
10. **デバッグのワークフローの名前を指定** ページで、既定の名前 (**MySharePointWorkflow - Workflow1**)。 既定値の保持ワークフロー テンプレートの種類、**リスト ワークフロー**を選択し、**次**ボタンをクリックします。  
  
11. **Visual Studio でデバッグ セッションでワークフローを自動的に関連付けたいですか?**ページで、選択、 **[次へ]**ボタンをクリックしてすべての既定の設定。  
  
     この手順は、共有ドキュメント ライブラリにワークフローを自動的に関連付けます。  
  
12. **ワークフローの開始方法に関する条件の指定** ページで、選択を受け入れ、既定で、**ワークフローの開始をする方法ですか?**セクションし、選択、 **の完了**ボタンをクリックします。  
  
     このページでは、ワークフローの開始時を指定することができます。 既定では、ユーザー手動での開始時に、SharePoint またはワークフローが関連付けられている項目が作成されたときにいずれかのワークフローを開始します。  
  
## <a name="creating-workflow-activities"></a>ワークフロー アクティビティを作成します。  
 1 つ以上のワークフローが含まれて*アクティビティ*を実行するアクションを表すです。 ワークフロー デザイナーを使用すると、ワークフローのアクティビティを調整します。 この手順では 2 つのアクティビティに追加ワークフロー: HandleExternalEventActivity と OnWorkFlowItemChanged です。 これらのアクティビティ内のドキュメントのレビュー状態の監視、 **Shared Documents**一覧  
  
#### <a name="to-create-workflow-activities"></a>ワークフロー アクティビティを作成するには  
  
1.  ワークフローは、ワークフロー デザイナーに表示する必要があります。 そうでない場合を開き、 **Workflow1.cs**または**Workflow1.vb**で**ソリューション エクスプ ローラー**です。  
  
2.  デザイナーで、選択、 **OnWorkflowActivated1**アクティビティ。  
  
3.  **プロパティ**ウィンドウで、入力**onWorkflowActivated**  の横に、 **Invoked**プロパティ、し、Enter キーを押します。  
  
     コード エディターが開き、onWorkflowActivated を名前付きイベント ハンドラー メソッドが Workflow1 コード ファイルに追加します。  
  
4.  ワークフロー デザイナーに戻り、ツールボックスを開きの順に展開、 **Windows Workflow v3.0**ノード。  
  
5.  **Windows Workflow v3.0**のノード、**ツールボックス**のいずれか、次の手順を実行します。  
  
    1.  ショートカット メニューを開き、**中**、アクティビティを選択し**コピー**です。 ワークフロー デザイナーで下にある行のショートカット メニューを開き、 **onWorkflowActivated1** 、アクティビティを選択し**貼り付け**です。  
  
    2.  ドラッグ、**中**からアクティビティを**ツールボックス**ワークフロー デザイナーに下にある行に、アクティビティを接続し、 **onWorkflowActivated1**アクティビティ。  
  
6.  選択、 **WhileActivity1**アクティビティ。  
  
7.  **プロパティ**ウィンドウで、設定**条件**コードの状態にします。  
  
8.  展開、**条件**プロパティ、入力**isWorkflowPending**子の横にある**条件**プロパティ、し、Enter キーを押します。  
  
     コード エディターが開き、isWorkflowPending をという名前のメソッドは、Workflow1 コード ファイルに追加します。  
  
9. ワークフロー デザイナーに戻り、ツールボックスを開きの順に展開、 **SharePoint ワークフロー**ノード。  
  
10. **SharePoint ワークフロー**のノード、**ツールボックス**のいずれか、次の手順を実行します。  
  
    -   ショートカット メニューを開き、 **OnWorkflowItemChanged** 、アクティビティを選択し**コピー**です。 ワークフロー デザイナーで内部の行のショートカット メニューを開き、 **whileActivity1**アクティビティを選択し**貼り付け**です。  
  
    -   ドラッグ、 **OnWorkflowItemChanged**からアクティビティを**ツールボックス**ワークフロー デザイナーに内部の行に、アクティビティを接続し、 **whileActivity1**アクティビティ。  
  
11. 選択、 **onWorkflowItemChanged1**アクティビティ。  
  
12. **プロパティ** ウィンドウでは、次の表に示すようにプロパティを設定します。  
  
    |プロパティ|値|  
    |--------------|-----------|  
    |**CorrelationToken**|**workflowToken**|  
    |**呼び出される**|**onWorkflowItemChanged**|  
  
## <a name="handling-activity-events"></a>アクティビティ イベントの処理  
 最後に、各活動からのドキュメントの状態を確認します。 ドキュメントをレビューすると、ワークフローは終了します。  
  
#### <a name="to-handle-activity-events"></a>アクティビティのイベントを処理するには  
  
1.  Workflow1.cs または Workflow1.vb、内の先頭に次のフィールドを追加、`Workflow1`クラスです。 このフィールドは、ワークフローが完了したかどうかを決定するアクティビティで使用されます。  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  `Workflow1` クラスに次のメソッドを追加します。 このメソッドは、の値を調べて、`Document Status`ドキュメントが確認されていないかどうかを決定するドキュメントの一覧のプロパティです。 場合、`Document Status`プロパティに設定されている`Review Complete`、`checkStatus`メソッドのセット、`workflowPending`フィールドを**false**ワークフローが完了する準備完了であることを示します。  
  
    ```vb  
    Private Sub checkStatus()  
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then  
            workflowPending = False  
        End If  
    End Sub   
    ```  
  
    ```csharp  
    private void checkStatus()  
    {  
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")  
        workflowPending = false;  
    }  
    ```  
  
3.  次のコードを追加、`onWorkflowActivated`と`onWorkflowItemChanged`メソッドを呼び出して、`checkStatus`メソッドです。 ワークフローの開始時、`onWorkflowActivated`メソッドの呼び出し、`checkStatus`ドキュメントが既に確認されているかどうかを調べます。 かどうか確認されていませんが、ワークフローを続行します。 ドキュメントを保存すると、`onWorkflowItemChanged`メソッドの呼び出し、`checkStatus`メソッド ドキュメントが確認されていないかどうかを確認します。 中に、`workflowPending`にフィールドが設定されている**true**ワークフローは引き続き実行します。  
  
    ```vb  
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
  
    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
    ```  
  
    ```csharp  
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
  
    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
    ```  
  
4.  次のコードを追加、`isWorkflowPending`の状態を確認する方法を`workflowPending`プロパティです。 ドキュメントを保存するたびに、 **whileActivity1**アクティビティ呼び出し、`isWorkflowPending`メソッドです。 このメソッドは、検査、<xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A>のプロパティ、<xref:System.Workflow.Activities.ConditionalEventArgs>を決定するオブジェクトかどうか、 **WhileActivity1**アクティビティが続行するか、完了します。 プロパティ設定されている場合**true**アクティビティが継続します。 それ以外の場合、アクティビティが完了し、ワークフローは終了します。  
  
    ```vb  
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)  
        e.Result = workflowPending  
    End Sub  
    ```  
  
    ```csharp  
    private void isWorkflowPending(object sender, ConditionalEventArgs e)  
    {  
        e.Result = workflowPending;  
    }  
    ```  
  
5.  プロジェクトを保存します。  
  
## <a name="testing-the-sharepoint-workflow-template"></a>SharePoint ワークフロー テンプレートのテスト  
 デバッガーを開始するときに[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]が SharePoint サーバーに、ワークフロー テンプレートを展開し、ワークフローを関連付けます、 **Shared Documents**  ボックスの一覧です。 ワークフローをテストするには、内のドキュメントから、ワークフローのインスタンスを開始、 **Shared Documents**  ボックスの一覧です。  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>SharePoint ワークフロー テンプレートをテストするには  
  
1.  Workflow1.cs または Workflow1.vb でにブレークポイントを設定 の横に、 **onWorkflowActivated**メソッドです。  
  
2.  F5 キーをソリューションをビルドおよび実行を選択します。  
  
     SharePoint サイトが表示されます。  
  
3.  SharePoint で、ナビゲーション ウィンドウで、選択、 **Shared Documents**リンクします。  
  
4.  **Shared Documents**ページで、選択、**ドキュメント**リンクを**ライブラリ ツール** タブをクリックして、**ドキュメントのアップロード**ボタン.  
  
5.  **ドキュメントのアップロード** ダイアログ ボックスで、選択、**参照**ボタン、任意のドキュメント ファイルを選択して、選択、**開く**ボタンをクリックしを選択し、 **ok**ボタンをクリックします。  
  
     選択したドキュメントをアップロード、 **Shared Documents**を一覧表示し、ワークフローを開始します。  
  
6.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、デバッガーをブレークポイントで横に中断することを確認、`onWorkflowActivated`メソッドです。  
  
7.  実行を継続する F5 キーを押します。  
  
8.  ここでは、ドキュメントの設定を変更したが、そのままに既定値は、ここで選択して、**保存**ボタンをクリックします。  
  
     戻ります、 **Shared Documents**既定の SharePoint Web サイトのページです。  
  
9. **Shared Documents**ことを確認 ページで、下にある値、 **MySharePointWorkflow - Workflow1**に列が設定されている**進行中の**します。 これは、ワークフローが実行中であると、ドキュメントが確認を待機しているを示します。  
  
10. **Shared Documents**ページ、ドキュメントを選択、順に選択し、表示される矢印をクリックして、**プロパティの編集**メニュー項目。  
  
11. 設定**ドキュメントの状態**に**レビュー完了**を選択し、**保存**ボタンをクリックします。  
  
     戻ります、 **Shared Documents**既定の SharePoint Web サイトのページです。  
  
12. **Shared Documents**ことを確認 ページで、下にある値、**ドキュメントの状態**に設定されている列**レビュー完了**です。 更新、 **Shared Documents**  ページを確認する値の下に、 **MySharePointWorkflow - Workflow1**に設定されている列**完了**です。 これが示すワークフローが完了し、ドキュメントが確認されていません。  
  
## <a name="next-steps"></a>次の手順  
 これらのトピックからワークフロー テンプレートを作成する方法の詳細を学習できます。  
  
-   SharePoint ワークフローのアクティビティに関する詳細については、次を参照してください。 [SharePoint Foundation のワークフロー活動](http://go.microsoft.com/fwlink/?LinkId=178992)です。  
  
-   Windows Workflow Foundation アクティビティに関する詳細については、次を参照してください。 [System.Workflow.Activities Namespace](http://go.microsoft.com/fwlink/?LinkId=178993)です。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint ワークフロー ソリューションを作成します。](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  