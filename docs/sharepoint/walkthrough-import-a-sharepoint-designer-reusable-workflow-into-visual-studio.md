---
title: 'チュートリアル: SharePoint Designer の再利用可能なワークフローの Visual Studio へのインポート |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 443502fdb6b018772e4dde833c5d53d27a68dbe8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>チュートリアル: SharePoint Designer の再利用可能なワークフローの Visual Studio へのインポート
  このチュートリアルは、SharePoint Designer 2010 で作成した再利用可能なワークフローをインポートする方法を示します、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint ワークフロー プロジェクトです。  
  
 SharePoint Designer で作成したワークフローまたは*宣言型ワークフロー*から成る[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]コードの代わりにステートメントです。 SharePoint Designer 2010 が導入されています*再利用可能なワークフロー*、SharePoint サイトで、異なる一覧がで使用できるポータブル、宣言型のワークフローがあります。  
  
 作成したワークフロー [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]、シーケンシャル、およびステート マシン ワークフローなどと呼ばれます*コード ワークフロー*です。 コード ワークフローでは、XML ファイルとコード モジュールをユーザーがワークフローの動作をカスタマイズするので構成されます。  
  
 Visual Studio を使用すると、SharePoint Designer 2010 で作成した再利用可能なワークフローをインポートし、それらを SharePoint サイトで使用するためのコードのワークフローに変換できます。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   SharePoint Designer の再利用可能な単純なワークフローを作成しています。  
  
-   .Wsp ファイルに、SharePoint には、SharePoint Designer の再利用可能なワークフローをエクスポートします。  
  
-   .Wsp ファイルをインポートする[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]再利用可能なワークフローのインポート プロジェクトを使用しています。  
  
-   コードを追加することによって、ワークフローを変更してください。  
  
-   SharePoint サイトにインポートされたワークフローを使用します。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]および SharePoint。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   Visual Studio  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010。  
  
## <a name="create-target-sharepoint-subsites"></a>ターゲット SharePoint サブサイトを作成します。  
 2 つの新しい SharePoint サブサイトを作成する最初: SharePoint Designer から、変換後のワークフローをホストする別の再利用可能なワークフローをホストするいずれか。  
  
#### <a name="to-create-sharepoint-subsites"></a>SharePoint サブサイトを作成するには  
  
1.  SharePoint Designer 2010 で、メニュー バーで、選択**ファイル**、**空の Web サイトを新しい**です。  
  
2.  **空の Web サイトを新しい**ダイアログ ボックスで、ワークフローを作成または http:// の値を使用する SharePoint サイトへの参照*SystemName*/を選択し、 **OK**ボタンをクリックします。  
  
     ホーム ページが表示されます。  
  
3.  **サブサイト**セクションで、選択、**新規**ボタンをクリックします。  
  
4.  **新規** ダイアログ ボックスで、選択**SharePoint テンプレート**左側のウィンドウで、一覧から選択**チーム サイト**右側のウィンドウで、一覧からです。  
  
5.  **、Web サイトの場所の指定**ボックスに、単語を置換**サブサイト**を使用して URL で**SPD1**を選択し、 **[ok]**ボタンをクリックします。  
  
     SharePoint Designer に新しいサイトが開きます。 SharePoint Designer のインスタンスを閉じるし、最初のインスタンス (最上位のサイト) に戻ります。  
  
6.  手順 3 ~ 5 サブサイトを作成する、2 番目、今度は、単語を置き換える**サブサイト**で、[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]で**SPD2**です。  
  
## <a name="create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Designer の再利用可能なワークフローを作成します。  
 SharePoint にこの例で使用できる再利用可能なワークフローが含まれていないために、1 つを作成します。 この単純なワークフローでは、ユーザーが特定のソフトウェア タイトルを含むタスクの一覧で新しいタスクを入力すると、タスクがそのユーザーに割り当てられます。  
  
#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Designer の再利用可能なワークフローを作成するには  
  
1.  **サブサイト**セクションで、選択、 **SPD1**サイトを変更します。  
  
2.  リボンで、選択、**再利用可能なワークフロー**ボタンをクリックします。  
  
     再利用可能なワークフローの作成ウィザードが表示されます。  
  
3.  **名前**ボックスに、入力**SPD タスク ワークフロー**です。  
  
4.  **コンテンツの種類**一覧で、選択**タスク**を選択し、 **OK**ボタンをクリックします。  
  
     ワークフローは、SharePoint Designer ワークフロー デザイナーで開きます。  
  
5.  ワークフロー デザイナーで、手順 1. をポイントし、リボンで、、**条件**ボタンをクリックします。  
  
6.  条件の一覧で選択**項目の現在のフィールドの値に等しい場合**です。  
  
     この手順で追加の名前は、条件**フィールドの値に等しい場合**です。  
  
7.  **フィールドの値に等しい場合**条件で、選択、**フィールド**リンクします。  
  
8.  値の一覧で選択**タイトル**です。  
  
9. **フィールドの値に等しい場合**条件で、選択、**値**リンクします。  
  
10. ボックスで、次のように入力します。**新しいタスク**です。  
  
     ここでの条件ステートメントを読み取ります**新しいタスクに等しい場合の現在の項目: タイトル**です。  
  
11. 条件ステートメントの下にある行を選択し、リボンで、次のように選択します。、**アクション**ボタンをクリックします。  
  
12. アクションの一覧で選択**現在のアイテム セットのフィールド**です。  
  
13. **セットのフィールドの値に**アクション、選択、**フィールド**リンク、およびその後、一覧で、次のように選択します。**に割り当てられている**です。  
  
14. **セットのフィールドの値に**アクション、選択、**値**リンク、およびその後、既存のユーザーとグループの一覧で次のように選択します。**項目を作成したユーザー**です。  
  
15. 選択、**追加**ボタンをクリックしを選択し、 **OK**ボタンをクリックします。  
  
     操作のステートメントを今すぐ**設定割り当てに現在の項目: CreatedBy に**です。  
  
## <a name="save-and-deploy-the-reusable-workflow"></a>保存し、再利用可能なワークフローの配置  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .Wsp ファイルのみをインポートすることができます、.wsp ファイルとして再利用可能なワークフローを保存しにインポートする前に SharePoint に展開する必要があります[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
> [!IMPORTANT]  
>  次の手順を実行する実行時エラーが発生した場合は、SharePoint サイトにアクセス権があるシステム上の手順を実行する必要があります。  
  
#### <a name="to-save-and-deploy-the-reusable-workflow"></a>保存して再利用可能なワークフローを展開するには  
  
1.  SharePoint Designer の上部には、選択、**保存**、進捗状況を保存するボタンをクリックしを選択し、**発行**にワークフローを展開するにはボタン、 **SPD1** SharePoint サイト.  
  
2.  ナビゲーション ウィンドウで、選択、**ワークフロー**オブジェクト。  
  
3.  **再利用可能なワークフロー**、選択**SPD タスク ワークフロー**です。  
  
4.  リボンで、選択、**テンプレートとして保存**.wsp ファイルとして、ワークフローを保存するボタンをクリックします。  
  
5.  開く、 **SPD1** .wsp ファイルを SharePoint で表示するブラウザーで SharePoint サイトです。  
  
6.  クイック起動バーで、選択、**ライブラリ**リンクします。  
  
7.  **ドキュメント ライブラリ**セクションで、選択、**サイト資産**リンクします。  
  
     **SPD タスク ワークフロー**ファイルが他のサイトのアセットを表示します。  
  
8.  ファイルの一覧でそのファイルの名前を選択します  
  
9. **ファイルのダウンロード** ダイアログ ボックスで、選択、**保存**ローカル システム上の .wsp ファイルを保存するボタンをクリックします。  
  
## <a name="import-the-wsp-file-into-visual-studio"></a>Visual Studio に .wsp ファイルをインポートします。  
 .Wsp ファイルをインポート[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]再利用可能なワークフローのインポート プロジェクトを使用しています。 このプロジェクトは、再利用可能な宣言型ワークフローからワークフローをコードのワークフローに変換します。 ワークフローを変換するは、コードを使用してその動作を変更します。  
  
#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>.Wsp ファイルからワークフローをインポートし、それを変更するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、メニュー バーで、次のように選択します。**ファイル**、**新規**、**プロジェクト**です。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **SharePoint**ノード**Visual c#**または**Visual Basic**、をクリックして**2010**ノード。  
  
3.  **テンプレート** ウィンドウで、選択、**再利用可能な SharePoint 2010 ワークフローのインポート**テンプレートとプロジェクトの名前をそのまま**WorkflowImportProject1**を選択し、**OK**ボタンをクリックします。  
  
     SharePoint カスタマイズ ウィザードが表示されます。  
  
4.  **デバッグのサイトとセキュリティ レベルを指定して** ページで、入力、[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]以前に作成した 2 番目の SharePoint サブサイトの: http://*システム名*/SPD2 です。  
  
5.  **この SharePoint ソリューションの信頼レベルとは?**セクションで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックして、 **[次へ]**ボタンをクリックします。  
  
     サンド ボックスの詳細については、ファーム ソリューションではなく、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)です。  
  
6.  **新しいプロジェクトのソースを指定**ページ、.wsp ファイルを以前に保存されたシステム上の場所を参照、ファイルを開いて、およびを選択し、**次**ボタンをクリックします。  
  
    > [!NOTE]  
    >  選択、**完了**.wsp ファイル内のすべての利用可能な項目をインポートするボタンをクリックします。  
  
     これには、インポートで使用できる再利用可能なワークフローの一覧が表示されます。  
  
7.  **をインポートする項目の選択**ボックスで、選択、 **SPD タスク ワークフロー** 、ワークフローを選択し、**完了**ボタンをクリックします。  
  
     インポート操作が完了したら、プロジェクトの名前**WorkflowImportProject1**という名前のワークフローを含む作成**SPD_Workflow_TestFT**です。 このフォルダーには、ワークフローの定義ファイル Elements.xml とワークフロー デザイナー ファイル (.xoml)。 デザイナーには、2 つのファイルが含まれています: ルール ファイル (.rules) と分離コード ファイル (.cs または .vb ファイル、プロジェクトのプログラミング言語に応じて)。  
  
8.  **ソリューション エクスプ ローラー**、削除、**インポートされたファイルの他の**フォルダーです。  
  
9. Elements.xml ファイルで削除`InstantiationURL="_layouts/IniErkflIP.sspx"`です。  
  
10. **ソリューション エクスプ ローラー**、選択**WorkflowImportProject1**、その後、メニュー バーで、次のように選択します**プロジェクト**、**スタートアップ プロジェクトとして設定**に。設定**WorkflowImportProject1**スタートアップ アイテムとして。  
  
     プロジェクトをデバッグするときにすぐに、一覧が表示されます。  
  
11. **再利用可能な SharePoint 2010 ワークフローのインポート**テンプレートは、インポートしたワークフローの関連付けプロパティの値をインポートしない、これらを入力する必要があります。 手順は次のとおりです。  
  
    1.  **ソリューション エクスプ ローラー**、選択、 **SPD_Workflow_TestFT**ノード。  
  
    2.  選択、省略記号 (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円")) など、リストのプロパティの横にあるボタンをクリックして、**ターゲット リスト**プロパティです。  
  
    3.  SharePoint カスタマイズ ウィザードで欠損値を入力し、、**完了**ボタンをクリックします。  
  
12. .Xoml ファイルを選択し、メニュー バーで、次のように選択します。**ビュー**、**デザイナー**をワークフロー デザイナーで、インポートしたワークフローを表示します。  
  
13. **Windows Workflow v3.0**のノード、**ツールボックス**、次の手順のいずれかを実行します。  
  
    -   ショートカット メニューを開き、**コード**、アクティビティを選択し**コピー**です。 ワークフロー デザイナーで下にある行のショートカット メニューを開き、 **SequenceActivity1** 、アクティビティを選択し**貼り付け**です。  
  
    -   ドラッグ、**コード**からアクティビティを**ツールボックス**ワークフロー デザイナーに下にある行に接続し、 **SequenceActivity1**アクティビティ。  
  
     これは、という名前のワークフロー デザイナーにアクティビティを追加**CodeActivity1**です。 このアクティビティでは、ユーザーがワークフローを開始するときに、お知らせリストにアナウンスを作成するコード アクションを追加します。  
  
14. 次のいずれかの操作を実行します。  
  
    -   ダブルクリックして**CodeActivity1**をイベント ハンドラーを生成し、コードを表示します。  
  
    -   **プロパティ**ウィンドウ**CodeActivity1**の値を設定、 **ExecuteCode**プロパティを**codeActivity_ExecuteCode**です。  
  
15. 既存の下にある次の追加**を使用して**または**Imports**ステートメント。  
  
     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. 置き換える`codeActivity1_ExecuteCode`次。  
  
     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## <a name="deploy-the-project-and-associate-the-workflow"></a>プロジェクトを展開し、ワークフローを関連付ける  
 次に、WorkflowImportProject1 を実行する、SharePoint サイトに展開し、タスク一覧を表示および変更、テストにワークフローを関連付けるには変換ワークフローです。  
  
#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>プロジェクトを配置し、ワークフローを関連付ける  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を実行し、変換後のワークフロー プロジェクトを配置するには、F5 キーを選択します。  
  
2.  クイック起動バーで、選択、**タスク**タスク の一覧を表示するリンクです。  
  
3.  **リスト ツール** タブで、選択、**項目**ボタンをクリックしを選択し、**新しい項目の**ボタンをクリックします。  
  
     **タスク - 新しいアイテム** ダイアログ ボックスが表示されます。  
  
4.  **タイトル**ボックスに、入力**新しいタスク**を選択し、**保存**ボタンをクリックします。  
  
5.  **リスト ツール** タブで、選択、**リスト**ボタンをクリックしを選択し、**一覧の設定**ボタンをクリックします。  
  
     **一覧の設定**ページが表示されます。  
  
6.  **権限と管理**セクションで、選択、**ワークフロー設定**リンクします。  
  
     **ワークフロー設定**ページが表示されます。  
  
7.  選択、 **、ワークフローの追加**リンクします。  
  
8.  **ワークフロー**一覧で、選択**WorkflowImportProject1 - SPD ワークフロー テスト**です。  
  
9. **名前**ボックスに、入力**SPD ワークフロー テスト**を選択し、 **OK**ボタンをクリックします。  
  
10. クイック起動バーで、選択、**タスク** ボックスの一覧です。  
  
11. 横の矢印を選択**新しいタスク**、して、一覧で、次のように選択します。**ワークフロー**です。  
  
12. **新しいワークフローの開始**セクションで、リンクをクリックして**SPD ワークフロー テスト**を選択し、**開始**ワークフローを開始するボタンをクリックします。  
  
    > [!NOTE]  
    >  または、する自動的に関連付けますワークフロー リスト ワークフロー設定ウィザードを実行し、ワークフローを自動的に関連付けるを設定します。  
  
     2 つのアクションがワークフローによって行われたことに注意してください: で、タスクの名前が表示されます**に割り当てられている**に列、お知らせが表示されます、**お知らせ** ボックスの一覧です。  
  
## <a name="see-also"></a>関連項目  
 [既存の SharePoint サイトからアイテムをインポートします。](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)   
 [Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  