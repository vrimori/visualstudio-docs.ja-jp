---
title: "チュートリアル : SharePoint ワークフロー ソリューションの作成とデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Workflow.WorkflowConditions"
  - "VS.SharePointTools.Workflow.WorkflowList"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での SharePoint 開発, ワークフロー"
  - "ワークフロー [Visual Studio での SharePoint 開発]"
ms.assetid: 81756490-ab5a-4fa4-96c6-eed2cfbf8374
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# チュートリアル : SharePoint ワークフロー ソリューションの作成とデバッグ
  このチュートリアルでは、基本的なシーケンシャル ワークフロー テンプレートを作成する方法について説明します。  ワークフローは、共有ドキュメント ライブラリのプロパティをチェックして、ドキュメントの校閲が終了しているかどうかを確認します。  ドキュメントの校閲が終了している場合、ワークフローは完了します。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   SharePoint リスト定義シーケンシャル ワークフロー プロジェクトを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で作成する。  
  
-   ワークフロー アクティビティを作成する。  
  
-   ワークフロー アクティビティのイベントを処理する。  
  
> [!NOTE]  
>  このチュートリアルではシーケンシャル ワークフロー プロジェクトを使用していますが、ステート マシン ワークフロー プロジェクトでも手順は同じです。  
>   
>  また、次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前または場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   Visual Studio  
  
## SharePoint 共有ドキュメント ライブラリへのプロパティの追加  
 **共有ドキュメント** ライブラリでドキュメントの校閲ステータスを追跡するため、SharePoint サイトの共有ドキュメントに、`Status`、`Assignee`、および `Review Comments` という新しいプロパティを 3 つ作成します。  これらのプロパティは**共有ドキュメント** ライブラリで定義します。  
  
#### SharePoint 共有ドキュメント ライブラリにプロパティを追加するには  
  
1.  SharePoint サイトを、Web ブラウザーで http:\/\/system\<\>\< システム名 \>\/SitePages\/Home.aspx など\) を開きます。  
  
2.  クイック起動バーに、**\[ドキュメント\]** を **\[共有\]** をクリックします。  
  
3.  **\[ライブラリ ツール\]** のリボンに **\[ライブラリ\]** をクリックします、新しい列を作成するには、リボンの **\[列の作成\]** ボタンをクリックします。  
  
4.  列に" Document Status "という名前を付け、**\[選択肢 \(メニューから選択\)\]** に設定され、次の 3 種類の選択を指定し、**\[OK\]** ボタンを選択する:  
  
    -   **Review Needed**  
  
    -   **Review Complete**  
  
    -   **Changes Requested**  
  
5.  Assignee と Review Comments という名前でさらに 2 つの列を作成します。  \[Assignee\] 列はテキストを 1 行だけ表示するように設定し、\[Review Comments\] 列は複数行のテキストを表示するように設定します。  
  
## チェックアウトせずにドキュメントを編集できるようにする  
 チェックアウトせずにドキュメントを編集できると、ワークフロー テンプレートのテストが容易になります。  次の手順では、これを行うことができるように SharePoint サイトを構成します。  
  
#### チェックアウトせずにドキュメントを編集できるようにするには  
  
1.  クイック起動バーに、**\[共有ドキュメント\]** リンクをクリックします。  
  
2.  **\[ライブラリ ツール\]** のリボンで、**\[ライブラリ\]** タブをクリックし、**\[ドキュメント ライブラリの設定\]** ページを表示するに **\[ライブラリの設定\]** ボタンをクリックします。  
  
3.  **\[全般設定\]** セクションで、**\[バージョン設定\]** ページを表示するに **\[バージョン設定\]** リンクをクリックします。  
  
4.  **\[ドキュメントを編集する前に必ずチェックアウトする\]** の設定が **\[いいえ\]** であることを確認します。  そうでない場合は、**\[いいえ\]** に変更し、**\[OK\]** ボタンをクリックします。  
  
5.  ブラウザーを閉じます。  
  
## SharePoint シーケンシャル ワークフロー プロジェクトの作成  
 シーケンシャル ワークフローは、最後のアクティビティが完了するまで順番に実行される一連の手順です。  この手順では、共有ドキュメント リストに適用するシーケンシャル ワークフローを作成します。  ワークフロー ウィザードを使用すると、サイト定義とリスト定義のいずれかにワークフローを関連付け、ワークフローを開始するタイミングを指定することができます。  
  
#### SharePoint シーケンシャル ワークフロー プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  メニュー バーで、**\[新しいプロジェクト\]** ダイアログ ボックスを表示するには、**\[新規作成\]**、**\[プロジェクト\]\[ファイル\]** をクリックします。  
  
3.  **\[SharePoint\]** ノードを **\[Visual C\#\]** または **\[Visual Basic\]** で展開し、**2010** ノードを選択します。  
  
4.  **\[テンプレート\]** のペインで、**\[SharePoint 2010 プロジェクト\]** テンプレートを選択します。  
  
5.  **\[名前\]** ボックスで、MySharePointWorkflow "と入力し、**\[OK\]** ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
6.  **\[デバッグのサイトとセキュリティ レベルの指定\]** ページで、**\[ファーム ソリューションとして配置する\]** のオプション ボタンを選択し、信頼レベルと既定のサイトを受け入れるように **\[完了\]** ボタンをクリックします。  
  
     また、この段階で、ソリューションの信頼レベルがファーム ソリューション \(ワークフロー プロジェクトではこれ以外は選択できません\) として設定されます。  詳細については、「[サンドボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)」を参照してください。  
  
7.  次に **\[ソリューション エクスプローラー\]** で、プロジェクト ノードを選択し、メニュー バーで、**\[プロジェクト\]** をクリックします、**\[新しいアイテムの追加\]** を選択します。  
  
8.  **\[Visual C\#\]** または **\[Visual Basic\]** で、**\[SharePoint\]** ノードを展開し、**2010** ノードを選択します。  
  
9. **\[テンプレート\]** のペインで、**\[シーケンシャル ワークフロー \(ファーム ソリューションのみ\)\]** テンプレートを選択し、**\[追加\]** ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
10. **\[デバッグのワークフロー名の指定\]** ページで、既定の名前 \(**MySharePointWorkflow \- Workflow1**\) を受け入れます。  既定のワークフロー テンプレートの種類、**\[リスト ワークフロー\]** を保持し、次へ **\[次へ\]** ボタンをクリックします。  
  
11. **\[デバッグ セッション中に Visual Studio によってワークフローが自動的に関連付けられるようにする\]** ページで、既定の設定を受け入れるように **\[次へ\]** ボタンをクリックします。  
  
     この段階で、ワークフローが共有ドキュメント ライブラリに自動的に関連付けられます。  
  
12. **\[ワークフローの開始方法に関する条件の指定\]** ページで、既定のオプションを選択 **\[ワークフローの開始方法\]** セクションのままにし、**\[完了\]** ボタンをクリックします。  
  
     このページでは、ワークフローを開始するタイミングを指定できます。  既定では、ユーザーが SharePoint でワークフローを手動で開始すると、またはワークフローが関連付けられている項目が作成されると、ワークフローが開始します。  
  
## ワークフロー アクティビティの作成  
 ワークフローには、実行するアクションを表す*アクティビティ*が 1 つ以上含まれています。  ワークフローのアクティビティを調整するには、ワークフロー デザイナーを使用します。  この手順では、HandleExternalEventActivity と OnWorkFlowItemChanged の 2 つのアクティビティをワークフローに追加します。  これらのアクティビティは、**共有ドキュメント** リスト内のドキュメントの校閲ステータスを監視します。  
  
#### ワークフロー アクティビティを作成するには  
  
1.  ワークフロー デザイナーにワークフローが表示されている必要があります。  そうでない場合は、**\[ソリューション エクスプローラー\]** の **\[Workflow1.cs\]** または **\[Workflow1.vb\]** を開きます。  
  
2.  デザイナーで、**\[OnWorkflowActivated1\]** アクティビティをクリックします。  
  
3.  **\[プロパティ \]** ウィンドウで、**\[呼び出される\]** のプロパティの横に" onWorkflowActivated "と入力し、Enter キーを押します。  
  
     コード エディターが開き、onWorkflowActivated という名前のイベント ハンドラー メソッドが Workflow1 コード ファイルに追加されます。  
  
4.  ワークフロー デザイナーに戻り、ツールボックスを開いて、**\[Windows Workflow v3.0\]** ノードを展開します。  
  
5.  **\[ツールボックス\]** の **\[Windows Workflow v3.0\]** ノードで、手順の次の 1 組の実行:  
  
    1.  **\[While\]** アクティビティのショートカット メニューを開き、**\[コピー\]** をクリックします。  ワークフロー デザイナーで、行のショートカット メニューを **\[onWorkflowActivated1\]** アクティビティで開き、**\[貼り付け\]** をクリックします。  
  
    2.  **\[ツールボックス\]** からワークフロー デザイナーに **\[While\]** アクティビティをドラッグし、行に **\[onWorkflowActivated1\]** アクティビティでアクティビティを追加します。  
  
6.  **\[WhileActivity1\]** アクティビティをクリックします。  
  
7.  **\[プロパティ\]** ウィンドウで、条件をコードに **\[条件\]** を設定します。  
  
8.  **\[条件\]** のプロパティを展開し、子の **\[条件\]** のプロパティの横に" isWorkflowPending "と入力し、Enter キーを押します。  
  
     コード エディターが開き、isWorkflowPending という名前のメソッドが Workflow1 コード ファイルに追加されます。  
  
9. ワークフロー デザイナーに戻り、ツールボックスを開いて、**\[SharePoint ワークフロー\]** ノードを展開します。  
  
10. **\[ツールボックス\]** の **\[SharePoint ワークフロー\]** ノードで、手順の次の 1 組の実行:  
  
    -   **\[OnWorkflowItemChanged\]** アクティビティのショートカット メニューを開き、**\[コピー\]** をクリックします。  ワークフロー デザイナーで、**\[whileActivity1\]** アクティビティ内の行のショートカット メニューを開き、**\[貼り付け\]** をクリックします。  
  
    -   **\[ツールボックス\]** からワークフロー デザイナーに **\[OnWorkflowItemChanged\]** アクティビティをドラッグし、**\[whileActivity1\]** アクティビティ内の行にアクティビティを追加します。  
  
11. **\[onWorkflowItemChanged1\]** アクティビティをクリックします。  
  
12. **\[プロパティ\]** ウィンドウで、次の表に示すようにプロパティを設定します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Invoked**|**onWorkflowItemChanged**|  
  
## アクティビティのイベントの処理  
 最後に、各アクティビティからドキュメントのステータスをチェックします。  ドキュメントの校閲が終了している場合、ワークフローは完了します。  
  
#### アクティビティのイベントを処理するには  
  
1.  Workflow1.cs または Workflow1.vb で、`Workflow1` クラスの先頭に次のフィールドを追加します。  アクティビティ内のこのフィールドを使用して、ワークフローを完了させるかどうかを判断します。  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  `Workflow1` クラスに次のメソッドを追加します。  このメソッドは、Documents リストの `Document Status` プロパティの値をチェックして、ドキュメントの校閲が終了しているかどうかを確認します。  `Document Status` プロパティが `Review Complete` に設定されている場合、`checkStatus` メソッドは `workflowPending` フィールドに **false** を設定し、ワークフロー完了の準備が整っていることを示します。  
  
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
  
3.  `onWorkflowActivated` メソッドと `onWorkflowItemChanged` メソッドに次のコードを追加して、`checkStatus` メソッドを呼び出します。  ワークフローが開始すると、`onWorkflowActivated` メソッドは `checkStatus` メソッドを呼び出して、ドキュメントの校閲が既に行われているかどうかを確認します。  まだ校閲が行われていない場合は、ワークフローは続行します。  ドキュメントが保存されると、`onWorkflowItemChanged` メソッドはもう一度 `checkStatus` メソッドを呼び出して、ドキュメントの校閲が行われたかどうかを確認します。  `workflowPending` フィールドが **true** に設定されている間は、ワークフローは処理を続行します。  
  
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
  
4.  `isWorkflowPending` メソッドに次のコードを追加して、`workflowPending` プロパティのステータスをチェックします。  ドキュメントが保存されるたびに、**whileActivity1** アクティビティは `isWorkflowPending` メソッドを呼び出します。  このメソッドは、<xref:System.Workflow.Activities.ConditionalEventArgs> オブジェクトの <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> プロパティを調べて、**WhileActivity1** アクティビティを続行すべきか完了すべきかを判断します。  プロパティが **true** に設定されていると、アクティビティは続行します。  それ以外の場合は、アクティビティが完了し、ワークフローも完了します。  
  
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
  
## SharePoint ワークフロー テンプレートのテスト  
 デバッガーを起動すると、ワークフロー テンプレートが [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって SharePoint サーバーに配置され、ワークフロー が**共有ドキュメント** リストに関連付けられます。  ワークフローをテストするため、**共有ドキュメント** リスト内のドキュメントからワークフローのインスタンスを起動します。  
  
#### SharePoint ワークフロー テンプレートをテストするには  
  
1.  Workflow1.cs または Workflow1.vb で **onWorkflowActivated** メソッドの横にブレークポイントを設定します。  
  
2.  ソリューションをビルドして実行するには、F5 キーを押します。  
  
     SharePoint サイトが表示されます。  
  
3.  SharePoint のナビゲーション ペインで、**\[共有ドキュメント\]** リンクをクリックします。  
  
4.  **\[共有ドキュメント\]** ページで、**\[ライブラリ ツール\]** タブの **\[ドキュメント\]** リンクを選択し、**\[ドキュメントのアップロード\]** ボタンをクリックします。  
  
5.  **\[ドキュメントのアップロード\]** ダイアログ ボックスで、**\[参照\]** ボタンを選択し、ドキュメント ファイルを選択し、**\[開く\]** ボタンをクリックし、**\[OK\]** ボタンをクリックします。  
  
     選択されたドキュメントが**共有ドキュメント** リストにアップロードされ、ワークフローが開始します。  
  
6.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で、`onWorkflowActivated` メソッドの横に指定したブレークポイントでデバッガーが停止することを確認します。  
  
7.  実行を継続する、F5 キーを押します。  
  
8.  ドキュメントの設定をここに変更できますが既定値で **\[保存\]** ボタンをクリックして、それらを今は残ります。  
  
     既定の SharePoint Web サイトの **\[共有ドキュメント\]** ページに戻ります。  
  
9. **\[共有ドキュメント \]** ページで、**\[MySharePointWorkflow – Workflow1\]** 列の下にある値が **\[処理中\]** に設定されていることを確認します。  これは、ワークフローが処理中であり、ドキュメントが校閲待ちの状態であることを示します。  
  
10. **\[共有ドキュメント\]** ページのドキュメントを選択し、表示をクリックして **\[プロパティの編集\]** メニュー項目を選択すると、矢印を。  
  
11. **\[ドキュメントの状態\]** を **\[レビューの完了\]** に設定し、**\[保存\]** ボタンをクリックします。  
  
     既定の SharePoint Web サイトの **\[共有ドキュメント\]** ページに戻ります。  
  
12. **\[共有ドキュメント \]** ページで、**\[ドキュメントの状態\]** 列の下にある値が **\[レビューの完了\]** に設定されていることを確認します。  **\[共有ドキュメント\]** でページを更新し、**\[MySharePointWorkflow – Workflow1\]** 列の下にある値が **\[完了\]** に設定されていることを確認します。  これは、ワークフローが完了し、ドキュメントが校閲済みであることを示します。  
  
## 次の手順  
 ワークフロー テンプレートの作成方法の詳細については、以下のトピックを参照してください。  
  
-   SharePoint ワークフロー アクティビティの詳細については、"参照してください [SharePoint Foundation のワークフロー アクティビティの概要](http://go.microsoft.com/fwlink/?LinkId=178992)。  
  
-   Windows Workflow Foundation アクティビティの詳細については、"参照してください [System.Workflow.Activities 名前空間](http://go.microsoft.com/fwlink/?LinkId=178993)。  
  
## 参照  
 [SharePoint ワークフロー ソリューションの作成](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  