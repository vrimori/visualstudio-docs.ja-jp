---
title: 'チュートリアル: を作成して、SharePoint ワークフロー ソリューションのデバッグ |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c254f6f3e044f938ed2749567d66ee7a313081e7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "42626489"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>チュートリアル: 作成し、SharePoint ワークフロー ソリューションのデバッグ
  このチュートリアルでは、基本的なシーケンシャル ワークフロー テンプレートを作成する方法を示します。 ワークフローは、ドキュメントが確認されたかどうかを判断する共有ドキュメント ライブラリのプロパティを確認します。 ドキュメントをレビューすると、ワークフローが終了します。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   SharePoint リスト定義シーケンシャル ワークフロー プロジェクトを作成する[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。  
  
-   ワークフロー アクティビティを作成します。  
  
-   ワークフロー アクティビティのイベントを処理します。  
  
> [!NOTE]  
>  このチュートリアルでは、シーケンシャル ワークフロー プロジェクトでは、プロセスはステート マシンのワークフロー プロジェクトに同じです。  
>   
>  また、コンピューター可能性がありますさまざまな名前や場所が一部の Visual Studio のユーザー インターフェイス要素次の手順で。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。  
  
-   Visual Studio  
  
## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>SharePoint の共有ドキュメント ライブラリにプロパティを追加します。
 内のドキュメントのレビュー状況を追跡するために、**共有ドキュメント**ライブラリ、SharePoint サイトで共有ドキュメントの 3 つの新しいプロパティを作成します: `Status`、 `Assignee`、および`Review Comments`します。 これらのプロパティを定義、 **Shared Documents**ライブラリ。  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>SharePoint の共有にプロパティを追加するには、と、ドキュメント ライブラリ  
  
1.  Http:// などの SharePoint サイトを開きます。\<システム名 >/SitePages/Home.aspx、Web ブラウザーでします。  
  
2.  クイック起動バーで、次のように選択します。 **SharedDocuments**します。  
  
3.  選択**ライブラリ**上、**ライブラリ ツール**リボンをクリックして、**列の作成**新しい列を作成するには、リボン ボタンをクリックします。  
  
4.  列の名前**Document Status**、その型に設定**選択肢 (メニューから選択する)**、次の 3 つの選択肢を指定し、選択、 **OK**ボタン。  
  
    -   **確認が必要な**  
  
    -   **確認完了**  
  
    -   **要求された変更**  
  
5.  2 つの列を作成し、名前を付けます**担当者**と**レビュー コメント**します。 複数行のテキストとして、テキストの単一行として担当者列の型と、レビュー コメント列の型を設定します。  
  
## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>チェック アウトを必要とせずに編集するドキュメントを有効にします。
 その内容を確認することがなく、ドキュメントを編集するときに、ワークフロー テンプレートをテストしやすくなります。次の手順では、オプションを有効にする SharePoint サイトを構成します。  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>それらをチェック アウトしないで編集するドキュメントを有効にするには  
  
1.  クイック起動バーで、 **Shared Documents**リンク。  
  
2.  **ライブラリ ツール**リボンで、選択、**ライブラリ**タブをクリックして、**ライブラリの設定**を表示するボタン、 **ドキュメントライブラリの設定**ページ。  
  
3.  **全般設定**セクションで、選択、**バージョン設定**表示へのリンク、**バージョン設定**ページ。  
  
4.  いることを確認の設定**ドキュメントを編集する前にチェック アウトを必要と**は**いいえ**します。 そうでない場合に変更して**いいえ**選択し、 **OK**ボタン。  
  
5.  ブラウザーを閉じます。  
  
## <a name="create-a-sharepoint-sequential-workflow-project"></a>SharePoint シーケンシャル ワークフロー プロジェクトを作成します。
 シーケンシャル ワークフローは、最後のアクティビティが終了するまで順番に実行する一連の手順を実行します。 この手順では、共有ドキュメント、リストに適用されるシーケンシャル ワークフローを作成します。 ワークフロー ウィザードでは、サイト定義またはリスト定義のいずれかでワークフローを関連付けることができ、ワークフローを開始するかを判断することができます。  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>SharePoint シーケンシャル ワークフロー プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで、**ファイル** > **新規** > **プロジェクト**を表示する、**新しいプロジェクト** ダイアログ ボックス。  
  
3.  展開、 **SharePoint**のどちらかのノード**Visual c#** または**Visual Basic**を選択し、 **2010**ノード。  
  
4.  **テンプレート**ウィンドウで、選択、 **SharePoint 2010 プロジェクト**テンプレート。  
  
5.  **名前**ボックスに、入力**MySharePointWorkflow**選択し、 **OK**ボタン。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
6.  **デバッグのサイトとセキュリティのレベルを指定**ページで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックして、 **[完了]** ボタンをクリックします信頼レベルと既定のサイトです。  
  
     この手順では、ファーム ソリューションでは、ワークフロー プロジェクトでのみ利用可能なオプションとして、ソリューションの信頼レベルを設定します。 詳細については、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)します。  
  
7.  **ソリューション エクスプ ローラー**をプロジェクト ノードを選択し、メニュー バーで、次のように選択します。**プロジェクト** > **新しい項目の追加**します。  
  
8.  いずれかで**Visual c#** または**Visual Basic**、展開、 **SharePoint**ノードを選択し、 **2010**ノード。  
  
9. **テンプレート**ウィンドウで、選択、**シーケンシャル ワークフロー (ファーム ソリューションのみ)** テンプレートを選択し、**追加**ボタン。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
10. **デバッグ ワークフローの名前を指定** ページで、既定の名前 (**MySharePointWorkflow - Workflow1**)。 既定のワークフロー テンプレートの型値の保持**リスト ワークフロー**、選択し、 **[次へ]** ボタンをクリックします。  
  
11. **Visual Studio デバッグ セッションでワークフローを自動的に関連付けるようでしょうか。** ページで、選択、**次**ボタンの既定の設定のままにします。  
  
     この手順は、共有ドキュメント ライブラリを自動的にワークフローを関連付けます。  
  
12. **、ワークフローを開始する方法についての条件を指定する** ページで、既定のオプションで選択したままにして、**ワークフローの開始をする方法でしょうか**セクションと、選択、 **の完了。** ボタンをクリックします。  
  
     このページでは、ワークフローの開始を指定することができます。 既定では、ユーザー手動での開始時に、SharePoint またはワークフローが関連付けられている項目が作成されたときにいずれかのワークフローを開始します。  
  
## <a name="create-workflow-activities"></a>ワークフロー アクティビティを作成します。
 1 つ以上のワークフローが含まれて*アクティビティ*を実行するアクションを表します。 ワークフロー デザイナーを使用すると、ワークフローのアクティビティを調整します。 この手順では、ワークフローに 2 つのアクティビティをいく予定: HandleExternalEventActivity と OnWorkFlowItemChanged です。 これらのアクティビティ内のドキュメントのレビュー状況の監視、 **Shared Documents**一覧  
  
#### <a name="to-create-workflow-activities"></a>ワークフロー アクティビティを作成するには  
  
1.  ワークフローは、ワークフロー デザイナーに表示する必要があります。 そうでない場合は、開く、か**Workflow1.cs**または**Workflow1.vb**で**ソリューション エクスプ ローラー**します。  
  
2.  デザイナーで、選択、 **OnWorkflowActivated1**アクティビティ。  
  
3.  **プロパティ**ウィンドウで、入力**onWorkflowActivated**横に、 **Invoked**プロパティ、Enter キーを押します。  
  
     コード エディターが開き、され、onWorkflowActivated という名前のイベント ハンドラー メソッドは、Workflow1 のコード ファイルに追加されます。  
  
4.  ワークフロー デザイナーに戻り、ツールボックスを開き、展開、 **Windows Workflow v3.0**ノード。  
  
5.  **Windows Workflow v3.0**のノード、**ツールボックス**、次の一連の手順のいずれかを実行します。  
  
    1.  ショートカット メニューを開き、**中**アクティビティを選び、**コピー**します。 ワークフロー デザイナーで下にある行のショートカット メニューを開き、 **onWorkflowActivated1**アクティビティを選び、**貼り付け**。  
  
    2.  ドラッグ、**中**からのアクティビティ、**ツールボックス**をワークフロー デザイナーでは、下の行に、アクティビティを接続し、 **onWorkflowActivated1**アクティビティ。  
  
6.  選択、 **WhileActivity1**アクティビティ。  
  
7.  **プロパティ**ウィンドウで、設定**条件**コード条件をします。  
  
8.  展開、**条件**プロパティ、入力**isWorkflowPending** 、子の横にある**条件**プロパティ、Enter キーを押します。  
  
     コード エディターが開き isWorkflowPending という名前のメソッドは、Workflow1 のコード ファイルに追加されます。  
  
9. ワークフロー デザイナーに戻り、ツールボックスを開き、展開、 **SharePoint ワークフロー**ノード。  
  
10. **SharePoint ワークフロー**のノード、**ツールボックス**、次の一連の手順のいずれかを実行します。  
  
    -   ショートカット メニューを開き、 **OnWorkflowItemChanged**アクティビティを選び、**コピー**します。 内の行のショートカット メニューを開き、ワークフロー デザイナーで、 **whileActivity1**アクティビティを選び、**貼り付け**します。  
  
    -   ドラッグ、 **OnWorkflowItemChanged**からのアクティビティ、**ツールボックス**をワークフロー デザイナーでは、内の行に、アクティビティを接続し、 **whileActivity1**アクティビティ。  
  
11. 選択、 **onWorkflowItemChanged1**アクティビティ。  
  
12. **プロパティ**ウィンドウは、次の表に示すように、プロパティを設定します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**correlationToken**|**workflowToken**|  
    |**呼び出される**|**さらに onWorkflowItemChanged**|  
  
## <a name="handle-activity-events"></a>アクティビティ イベントを処理します。
 最後に、各アクティビティからドキュメントの状態を確認します。 ドキュメントをレビューすると、ワークフローが完了しました。  
  
#### <a name="to-handle-activity-events"></a>アクティビティ イベントを処理するには  
  
1.  *Workflow1.cs*または*Workflow1.vb*の先頭に次のフィールドを追加、`Workflow1`クラス。 このフィールドは、ワークフローが終了したかどうかを確認するアクティビティで使用されます。  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  `Workflow1` クラスに次のメソッドを追加します。 このメソッドの値をチェックする、`Document Status`ドキュメントが確認されたかどうかを判断するドキュメントの一覧のプロパティ。 場合、`Document Status`プロパティに設定されて`Review Complete`、`checkStatus`メソッドのセット、`workflowPending`フィールドを**false**ワークフローが完了する準備であることを示します。  
  
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
  
3.  次のコードを追加、`onWorkflowActivated`と`onWorkflowItemChanged`メソッドを呼び出す、`checkStatus`メソッド。 ワークフローの開始時、`onWorkflowActivated`メソッドの呼び出し、`checkStatus`ドキュメントが既に確認されているかどうかを判断するメソッド。 かどうか確認されていませんが、ワークフローが続行されます。 ドキュメントが保存されると、`onWorkflowItemChanged`メソッドの呼び出し、`checkStatus`メソッドは、ドキュメントが確認されたかどうかを確認します。 中に、`workflowPending`にフィールドが設定されている**true**ワークフローが実行を継続します。  
  
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
  
4.  次のコードを追加、`isWorkflowPending`の状態を確認する方法、`workflowPending`プロパティ。 ドキュメントが保存されるたびに、 **whileActivity1**アクティビティが呼び出す、`isWorkflowPending`メソッド。 このメソッドは、検査、<xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A>のプロパティ、<xref:System.Workflow.Activities.ConditionalEventArgs>を決定するオブジェクトかどうか、 **WhileActivity1**アクティビティの続行または完了する必要があります。 プロパティ設定されている場合**true**アクティビティが継続します。 それ以外の場合、アクティビティが完了し、ワークフローは完了します。  
  
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
  
## <a name="test-the-sharepoint-workflow-template"></a>SharePoint ワークフロー テンプレートをテストします。
 デバッガーを起動するときに[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、SharePoint サーバーにワークフロー テンプレートをデプロイし、使用して、ワークフローを関連付けます、 **Shared Documents**一覧。 ワークフローをテストするには、内のドキュメントから、ワークフローのインスタンスを開始、 **Shared Documents**一覧。  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>SharePoint ワークフロー テンプレートをテストするには  
  
1.  *Workflow1.cs*または*Workflow1.vb*、横にブレークポイントを設定、 **onWorkflowActivated**メソッド。  
  
2.  選択、 **F5**キー、ソリューションをビルドして実行します。  
  
     SharePoint サイトが表示されます。  
  
3.  SharePoint でのナビゲーション ウィンドウで、 **Shared Documents**リンク。  
  
4.  **Shared Documents**ページで、選択、**ドキュメント**リンクを**ライブラリ ツール**タブをクリックして、**ドキュメントのアップロード**ボタン.  
  
5.  **ドキュメントのアップロード** ダイアログ ボックスで、選択、**参照**ボタン、任意のドキュメント ファイルを選択して、選択、**オープン**ボタンをクリックし、選択し、 **ok**ボタンをクリックします。  
  
     選択したドキュメントをアップロード、 **Shared Documents**ボックスの一覧し、ワークフローを開始します。  
  
6.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、デバッガーをブレークポイントで横に中断することを確認、`onWorkflowActivated`メソッド。  
  
7.  選択、 **F5**キーの実行を続行します。  
  
8.  ここでは、ドキュメントの設定を変更できますが、値のままにして、既定ここでを選択して、**保存**ボタンをクリックします。  
  
     戻ります、 **Shared Documents**既定の SharePoint Web サイトのページ。  
  
9. **Shared Documents**ことを確認します ページで、下にある値、 **MySharePointWorkflow - Workflow1**に設定されている列**で進行状況**します。 これは、ワークフローが進行中であると、ドキュメントが確認を待っていることを示します。  
  
10. **Shared Documents**  ページで、ドキュメントが表示されたらを選択し、矢印を選択、**プロパティの編集**メニュー項目。  
  
11. 設定**Document Status**に**Review Complete**、選択し、**保存**ボタンをクリックします。  
  
     戻ります、 **Shared Documents**既定の SharePoint Web サイトのページ。  
  
12. **Shared Documents**ことを確認します ページで、下にある値、 **Document Status**に設定されている列**Review Complete**します。 更新、 **Shared Documents**ページおよびことを確認します下にある値、 **MySharePointWorkflow - Workflow1**に設定されている列**完了**します。 これが示すワークフローが完了し、ドキュメントを確認します。  
  
## <a name="next-steps"></a>次の手順
 これらのトピックからワークフロー テンプレートを作成する方法の詳細を確認できます。  
  
-   SharePoint ワークフロー アクティビティの詳細については、次を参照してください。 [SharePoint Foundation のワークフロー アクティビティ](http://go.microsoft.com/fwlink/?LinkId=178992)します。  
  
-   Windows Workflow Foundation アクティビティの詳細については、次を参照してください。 [System.Workflow.Activities Namespace](http://go.microsoft.com/fwlink/?LinkId=178993)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint ワークフロー ソリューションを作成します。](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
