---
title: "チュートリアル: SharePoint Designer の再利用可能なワークフローの Visual Studio へのインポート"
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
  - "VS.SharePointTools.WSPImport.ImportWF"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio での SharePoint 開発、インポート (再利用可能なワークフローを)"
  - "再利用可能なワークフロー [Visual Studio での SharePoint 開発]"
ms.assetid: a6550615-4433-4aba-8bdf-0fcbf8dbcf97
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# チュートリアル: SharePoint Designer の再利用可能なワークフローの Visual Studio へのインポート
  このチュートリアルでは、SharePoint Designer 2010 で作成した再利用可能なワークフローを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint ワークフロー プロジェクトにインポートする方法について説明します。  
  
 SharePoint Designer で作成したワークフロー \(*宣言型のワークフロー*\) は、コードではなく [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ステートメントで構成されます。  SharePoint Designer 2010 には、*再利用可能なワークフロー*が導入されています。これは、汎用性のある宣言型のワークフローであり、SharePoint サイトの各種リストで使用できます。  
  
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]で \(シーケンシャル ワークフロー、ステート マシン ワークフローなど、作成されたワークフローは、*コード ワークフローと*呼ばれます。  コード ワークフローは XML ファイルとコード モジュールで構成され、ユーザーがワークフローの動作をカスタマイズできます。  
  
 Visual Studio では、SharePoint Designer 2010 で作成した再利用可能なワークフローをインポートし、SharePoint サイトで使用するためのコード ワークフローに変換することができます。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   単純な再利用可能なワークフローを SharePoint Designer で作成する。  
  
-   SharePoint Designer の再利用可能なワークフローを .wsp ファイルと SharePoint にエクスポートする。  
  
-   再利用可能なワークフローのインポート プロジェクトを使用して、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] に .wsp ファイルをインポートする。  
  
-   コードを追加してワークフローを変更する。  
  
-   インポートしたワークフローを SharePoint サイトで使用する。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] および SharePoint。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   Visual Studio  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010。  
  
## 対象の SharePoint サブサイトの作成  
 まず、SharePoint のサブサイトを新たに 2 つ作成します。1 つは、SharePoint Designer で作成した再利用可能なワークフローをホストするためのサブサイトで、もう 1 つは変換後のワークフローをホストするためのサブサイトです。  
  
#### SharePoint のサブサイトを作成するには  
  
1.  SharePoint Designer 2010 では、メニュー バーで、**\[新しい空白の Web サイト\]\[ファイル\]** をクリックします。  
  
2.  **\[新しい空白の Web サイト\]** ダイアログ ボックスで、ワークフローを作成するフォルダーに移動し、または http:\/\/*SystemName*\/使用し、の値を次に **\[OK\]** をクリックして、SharePoint サイトに。  
  
     ホーム ページが表示されます。  
  
3.  **\[サブサイト\]** セクションで、**\[新規作成\]** ボタンをクリックします。  
  
4.  **\[新規作成\]** ダイアログ ボックスで、左ペインの一覧から **\[SharePoint テンプレート\]** をクリックします、右ペインの一覧から **\[チーム サイト\]** をクリックします。  
  
5.  **\[Web サイトの場所を指定してください\]** ボックスで、URL の"を **\[subsite\]** SPD1 で置き換えて、**\[OK\]** ボタンをクリックします。  
  
     これで SharePoint Designer に新しいサブサイトが表示されます。  SharePoint Designer のこのインスタンスを閉じ、1 つ目のインスタンス \(最上位のサイト\) に戻ります。  
  
6.  手順 3. から手順 5. を繰り返して、2 つ目のサブサイトを作成します。今回は、[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] の **"subsite"** の部分を「SPD2」に置き換えます。  
  
## SharePoint Designer の再利用可能なワークフローの作成  
 SharePoint には、この例に使用できる再利用可能なワークフローが付属していないため、独自に 1 つ作成します。  この単純なワークフローでは、特定のタイトルのタスク リストにユーザーが新しいタスクを入力すると、そのユーザーがタスクに対して割り当てられます。  
  
#### SharePoint Designer の再利用可能なワークフローを作成するには  
  
1.  **\[サブサイト\]** セクションで、サイズを変更するに **\[SPD1\]** サイトを選択します。  
  
2.  リボンで、**\[再利用可能なワークフロー\]** ボタンをクリックします。  
  
     再利用可能なワークフローの作成ウィザードが表示されます。  
  
3.  **\[名前\]** ボックスで SPD Task Workflow を入力します。  
  
4.  **\[コンテンツ タイプ\]** の一覧で、**\[タスク\]** をクリックします、**\[OK\]** ボタンをクリックします。  
  
     SharePoint Designer ワークフロー デザイナーでワークフローが開きます。  
  
5.  次に、ワークフロー デザイナーで、手順 1 を、リボンで選択して **\[条件\]** ボタンをクリックします。  
  
6.  条件の一覧で、**\[現在のアイテム フィールドと値が等しいかどうか\]** をクリックします。  
  
     この手順では **\[フィールドと値が等しいかどうか\]** という条件を追加します。  
  
7.  **\[フィールドと値が等しいかどうか\]** の状態では、**\[フィールド\]** リンクをクリックします。  
  
8.  値ボックスの一覧で、**\[タイトル\]** をクリックします。  
  
9. **\[フィールドと値が等しいかどうか\]** の状態では、**\[値\]** リンクをクリックします。  
  
10. ボックスに「New task」と入力します。  
  
     条件ステートメントに、**"現在の Item:Title が New task と等しいとき"** と表示されます。  
  
11. 次の行を条件のステートメントでは、リボンをクリックし、**\[アクション\]** ボタンをクリックします。  
  
12. 操作ボックスで、**\[現在のアイテムにフィールドを設定する\]** をクリックします。  
  
13. 次に **\[評価するフィールドを設定します。\]** の操作では、**\[フィールド\]** リンクを、一覧で、**\[担当者\]** をクリックしますを選択します。  
  
14. 次に **\[評価するフィールドを設定します。\]** の操作では、既存のユーザーの一覧の **\[値\]** リンクを選択してグループは、**\[アイテムを作成したユーザー\]** をクリックします。  
  
15. **\[追加\]** をクリックし、**\[OK\]** をクリックします。  
  
     これで、アクション ステートメントには、"**担当者を Current Item:CreatedBy に設定する**" と表示されます。  
  
## 再利用可能なワークフローの保存と配置  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] でインポートできるのは .wsp ファイルだけなので、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] にインポートする前に、再利用可能なワークフローを .wsp ファイルとして保存し、SharePoint に配置する必要があります。  
  
> [!IMPORTANT]  
>  次の手順を実行する途中でランタイム エラーが発生する場合は、SharePoint サイトへのアクセス権があるシステム上で実行してください。  
  
#### 再利用可能なワークフローを保存して配置するには  
  
1.  SharePoint Designer の前に、進行状況を保存するに **\[保存\]** ボタンを選択して、**\[SPD1\]** SharePoint サイトにワークフローを配置するに **\[発行\]** ボタンをクリックします。  
  
2.  ナビゲーション ペインで、**\[ワークフロー\]** オブジェクトを選択します。  
  
3.  **\[再利用可能なワークフロー\]** で、**\[SPD Task Workflow\]** をクリックします。  
  
4.  リボンで、ワークフローを保存するに **\[テンプレートとして保存\]** ボタンを .wsp ファイルを選択します。  
  
5.  **SPD1** SharePoint サイトをブラウザーで開き、.wsp ファイルを SharePoint で表示します。  
  
6.  クイック起動バーに、**\[ライブラリ\]** リンクをクリックします。  
  
7.  **\[ドキュメント ライブラリ\]** セクションで、**\[サイトのリソース ファイル\]** リンクをクリックします。  
  
     **SPD Task Workflow** ファイルが他のサイト資産と共に一覧に表示されます。  
  
8.  ファイルの一覧で、ファイルの名前を選択します。  
  
9. **\[ファイルのダウンロード\]** ダイアログ ボックスで、ローカル システムで .wsp ファイルを保存するに **\[保存\]** ボタンをクリックします。  
  
## Visual Studio への .wsp ファイルのインポート  
 再利用可能なワークフローのインポート プロジェクトを使用して、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] に .wsp ファイルをインポートします。  宣言型の再利用可能なワークフローは、このプロジェクトによってコード ワークフローに変換されます。  ワークフローの変換後は、コードを使用してその動作を変更できます。  
  
#### ワークフローを .wsp ファイルからインポートして変更するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]のメニュー バーで、**\[新規作成\]**、**\[プロジェクト\]\[ファイル\]** をクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[SharePoint\]** ノードを **\[Visual C\#\]** または **\[Visual Basic\]** で展開し、**2010** ノードを選択します。  
  
3.  **\[テンプレート\]** のペインで、**\[再利用可能な SharePoint 2010 ワークフローのインポート\]** テンプレートを選択し、**\[WorkflowImportProject1\]** としてプロジェクトの名前をそのままにし、次へ **\[OK\]** ボタンをクリックします。  
  
     SharePoint カスタマイズ ウィザードが表示されます。  
  
4.  **\[デバッグのサイトとセキュリティ レベルの指定\]** ページで、先ほど作成した二つ目の SharePoint サブサイト 2 の [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] を入力する: http:\/\/*system name*\/SPD2。  
  
5.  **\[この SharePoint ソリューションの信頼レベル\]** セクションで、**\[ファーム ソリューションとして配置する\]** のオプション ボタンを選択し、**\[次へ\]** ボタンをクリックします。  
  
     サンドボックス ソリューションとファーム ソリューションの違いの詳細については、「[サンドボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)」を参照してください。  
  
6.  **\[新しいプロジェクト ソースの指定\]** ページで、先ほど .wsp ファイルを保存したシステム上の場所に、開くファイルを選択します **\[次へ\]** ボタンを参照してください。  
  
    > [!NOTE]  
    >  .wsp ファイルで使用できるすべての項目をインポートするに **\[完了\]** ボタンをクリックします。  
  
     この操作で、インポートに再利用可能なワークフローの一覧が表示されます。  
  
7.  **\[インポートする項目の選択\]** ボックスで、**\[SPD Task Workflow\]** のワークフローを選択し、**\[完了\]** ボタンをクリックします。  
  
     インポート操作が完了すると、**SPD\_Workflow\_TestFT** という名前のワークフローを含んだ **WorkflowImportProject1** という名前のプロジェクトが作成されます。  このフォルダーには、Elements.xml という名前のワークフローの定義ファイル、およびワークフロー デザイナー ファイル \(.xoml\) が格納されています。  デザイナーには、規則ファイル \(.rules\) と、プロジェクトのプログラミング言語に応じた分離コード ファイル \(.cs または .vb\) の 2 つのファイルが含まれています。  
  
8.  **\[ソリューション エクスプローラー\]** で、**\[インポートされた他のファイル\]** フォルダーを削除します。  
  
9. Elements.xml ファイルで、`InstantiationURL="_layouts/IniErkflIP.sspx"`を削除します。  
  
10. 次に **\[ソリューション エクスプローラー\]** で、メニュー バーで、スタートアップ プロジェクトとして **\[WorkflowImportProject1\]** を設定するに **\[プロジェクト\]** をクリックします、**\[スタートアップ プロジェクトに設定\]\[WorkflowImportProject1\]** をクリックします。  
  
     この設定で、プロジェクトをデバッグすると一覧が表示されるようになります。  
  
11. **\[再利用可能な SharePoint 2010 ワークフローのインポート\]** のテンプレートがインポートされたワークフローの関連プロパティ値がインポートされないため、入力する必要があります。  この操作を行うには、次の手順を実行します。  
  
    1.  **\[ソリューション エクスプローラー\]** で、**\[SPD\_Workflow\_TestFT\]** ノードを選択します。  
  
    2.  **\[ターゲット リスト\]** のプロパティなどの一覧のプロパティのうちの 1 つがの横にある省略記号 \(![ASP.NET モバイル デザイナー楕円](~/docs/sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円")\) ボタンを選択します。  
  
    3.  SharePoint カスタマイズ ウィザードの不足している値を入力し、**\[完了\]** ボタンをクリックします。  
  
12. 次に .xoml ファイルを選択し、メニュー バーで選択し、ワークフロー デザイナーでインポートしたワークフローを表示するには、**\[デザイナー\]\[表示\]** をクリックします。  
  
13. **\[ツールボックス\]** の **\[Windows Workflow v3.0\]** ノードで、次の手順の実行: 1  
  
    -   **\[コード\]** アクティビティのショートカット メニューを開き、**\[コピー\]** をクリックします。  ワークフロー デザイナーで、行のショートカット メニューを **\[SequenceActivity1\]** アクティビティで開き、**\[貼り付け\]** をクリックします。  
  
    -   **\[ツールボックス\]** からワークフロー デザイナーに **\[コード\]** アクティビティをドラッグし、行に **\[SequenceActivity1\]** アクティビティの下に接続します。  
  
     これで、**CodeActivity1** という名前のアクティビティがワークフロー デザイナーに追加されます。  このアクティビティでは、ユーザーによってワークフローが開始されたときに \[お知らせ\] ボックスにお知らせを作成するコード アクションを追加します。  
  
14. 次のいずれかの操作を実行します。  
  
    -   **\[CodeActivity1\]** をダブルクリックし、イベント ハンドラーを生成してコードを表示します。  
  
    -   **\[CodeActivity1\]** の **\[プロパティ\]** ウィンドウで、**\[codeActivity\_ExecuteCode\]** に **\[ExecuteCode\]** のプロパティの値を設定します。  
  
15. 既存の **using** ステートメントまたは **Imports** ステートメントの下に次を追加します。  
  
     [!code-csharp[SP_SPDWFImport#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_spdwfimport/cs/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_spdwfimport/vb/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. `codeActivity1_ExecuteCode` を次の内容に置き換えます。  
  
     [!code-csharp[SP_SPDWFImport#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_spdwfimport/cs/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_spdwfimport/vb/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## プロジェクトの配置とワークフローの関連付け  
 次に、WorkflowImportProject1 を実行して SharePoint サイトに配置し、さらに、そのワークフローをタスク一覧に関連付けて、変更された変換済みのワークフローを表示し、テストします。  
  
#### プロジェクトを配置してワークフローを関連付けるには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]の変換済みのワークフロー プロジェクトを実行するには、F5 キーを押します。  
  
2.  クイック起動バーに、タスク一覧を表示するに **\[タスク\]** リンクをクリックします。  
  
3.  **\[リスト ツール\]** タブで、**\[項目\]** をクリックし、**\[新しいアイテム\]** ボタンをクリックします。  
  
     **\[タスク\-新しい項目\]** ダイアログ ボックスが表示されます。  
  
4.  **\[タイトル\]** ボックスに" New task "と入力し、**\[保存\]** ボタンをクリックします。  
  
5.  **\[リスト ツール\]** タブで、**\[リスト\]** をクリックし、**\[リストの設定\]** ボタンをクリックします。  
  
     **\[リストの設定\]** ページが表示されます。  
  
6.  **\[権限と管理\]** セクションで、**\[ワークフロー設定\]** リンクをクリックします。  
  
     **\[ワークフロー設定\]** ページが表示されます。  
  
7.  **\[ワークフローの追加\]** リンクをクリックします。  
  
8.  **\[ワークフロー\]** の一覧で、**\[WorkflowImportProject1 \- Workflow Test\]** をクリックします。  
  
9. **\[名前\]** ボックスで SPD Workflow Test を入力し、**\[OK\]** ボタンをクリックします。  
  
10. クイック起動バーには、**\[タスク\]** の一覧を選択します。  
  
11. 下向き矢印を **\[新しいタスク\]** の横に、一覧で選択し、**\[ワークフロー\]** をクリックします。  
  
12. **\[新しいワークフローの開始\]** セクションで、**\[SPD Workflow Test\]** のリンクをクリックし、ワークフローを開始する **\[開始\]** ボタンをクリックします。  
  
    > [!NOTE]  
    >  ワークフロー設定ウィザードを実行し、ワークフローを自動的に関連付けるように設定にすることによって、リストにワークフローを自動的に関連付けることもできます。  
  
     ワークフローによって 2 つのアクションが実行されます。担当者の名前がタスクの **\[担当者\]** 列に表示され、お知らせが **\[お知らせ\]** ボックスに表示されます。  
  
## 参照  
 [既存の SharePoint サイトからのアイテムのインポート](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  