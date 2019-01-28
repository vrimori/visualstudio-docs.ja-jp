---
title: 'チュートリアル: SharePoint Designer の再利用可能なワークフローを Visual Studio にインポート |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83da0474a156ae714de1e713a1122ceac9fdce23
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875408"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>チュートリアル: SharePoint Designer の再利用可能なワークフローを Visual Studio にインポートします。
  SharePoint Designer 2010 で作成した再利用可能なワークフローをインポートする方法についても説明、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint ワークフロー プロジェクトです。  
  
 SharePoint Designer で作成されたワークフローまたは*宣言型ワークフロー*から成る[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]コードではなくステートメント。 SharePoint Designer 2010 で導入*再利用可能なワークフロー*、SharePoint サイトで別のリストで使用できる移植可能な宣言型ワークフローであります。  
  
 作成されたワークフロー [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]、シーケンシャル、ステート マシン ワークフローと呼ばれる*ワークフロー コード*します。 コード ワークフローは、XML ファイル、ユーザーがワークフローの動作をカスタマイズできるコード モジュールで構成されます。  
  
 Visual Studio を使用すると、SharePoint Designer 2010 で作成された再利用可能なワークフローをインポートし、SharePoint サイトで使用するためのコードのワークフローに変換できます。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
- SharePoint Designer で再利用可能な単純なワークフローを作成します。  
  
- SharePoint Designer の再利用可能なワークフローをエクスポート、 *.wsp*ファイルおよび SharePoint にします。  
  
- インポート、 *.wsp*ファイルを[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]再利用可能なワークフローのインポート プロジェクトを使用しています。  
  
- コードを追加して、ワークフローを変更します。  
  
- SharePoint サイトでは、インポートしたワークフローを使用します。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]および SharePoint。  
  
-   Visual Studio  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010。  
  
## <a name="create-target-sharepoint-subsites"></a>ターゲットの SharePoint サブサイトを作成します。
 最初に 2 つの新しい SharePoint サブサイトを作成します。 変換済みのワークフローをホストする SharePoint designer の再利用可能なワークフローをホストする 1 つ。  
  
#### <a name="to-create-sharepoint-subsites"></a>SharePoint のサブサイトを作成するには  
  
1. SharePoint Designer 2010 でのメニュー バーで選択**ファイル** > **空の Web サイトを新しい**します。  
  
2. **空の Web サイトを新しい**ダイアログ ボックスで、ワークフローを作成または http:// の値を使用する SharePoint サイトへの参照<em>SystemName</em>/選択し、 **OK**ボタンをクリックします。  
  
    ホーム ページが表示されます。  
  
3. **サブサイト**セクションで、選択、**新規**ボタンをクリックします。  
  
4. **新規** ダイアログ ボックスで、選択**SharePoint テンプレート**左側のウィンドウで、一覧から選択**チーム サイト**右側のウィンドウで、一覧から。  
  
5. **Web サイトの場所を指定**ボックスに、単語に置き換えた**サブサイト**URL の先頭で**SPD1**、選択し、 **[ok]** ボタンをクリックします。  
  
    SharePoint Designer に新しいサイトが開きます。 SharePoint Designer のインスタンスを閉じるし、最初のインスタンス (最上位のサイト) に戻ります。  
  
6. 手順 3 ~ 5 を 2 つ目のサブサイトを作成するには、この時間がという単語を置き換える**サブサイト**で、[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]で**SPD2**します。  
  
## <a name="create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Designer の再利用可能なワークフローを作成します。
 SharePoint にこの例で使用できる再利用可能なワークフローが含まれていないために、1 つを作成します。 この単純なワークフローでは、ユーザーが特定のタイトルを持つタスク リストで新しいタスクに入ったとき、タスクがそのユーザーに割り当てられます。  
  
#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Designer の再利用可能なワークフローを作成するには
  
1.  **サブサイト**セクションで、選択、 **SPD1**サイトを変更します。  
  
2.  リボンで、選択、**再利用可能なワークフロー**ボタンをクリックします。  
  
     再利用可能なワークフローの作成ウィザードが表示されます。  
  
3.  **名前**ボックスに、入力**SPD タスク ワークフロー**します。  
  
4.  **コンテンツの種類**一覧で、選択**タスク**、選択し、 **OK**ボタン。  
  
     ワークフローは、SharePoint Designer ワークフロー デザイナーで開きます。  
  
5.  ワークフロー デザイナーで手順 1 を選択して、次に、リボンで、次のように選択します。、**条件**ボタンをクリックします。  
  
6.  条件の一覧で選択**項目の現在のフィールド値に等しい場合**します。  
  
     この手順では、という条件を追加します。**フィールド値に等しい場合**します。  
  
7.  **フィールド値に等しい場合**条件で、選択、**フィールド**リンク。  
  
8.  値の一覧で選択**タイトル**します。  
  
9. **フィールド値に等しい場合**条件で、選択、**値**リンク。  
  
10. ボックスで、次のように入力します。**新しいタスク**します。  
  
     条件ステートメントを今すぐ**と等しい新しいタスクの場合の現在の項目: タイトル**します。  
  
11. 条件ステートメントでは、下にある行を選択し、その後、リボンで、次のように選択します。、**アクション**ボタンをクリックします。  
  
12. アクションの一覧で選択**現在のアイテム セット フィールド**します。  
  
13. **セットのフィールドを値**アクション選択、**フィールド**リンク、およびその後、一覧で、次のように選択します。**に割り当てられている**します。  
  
14. **セットのフィールドを値**アクション選択、**値**リンク、およびその後、既存のユーザーとグループの一覧で次のように選択します。**項目を作成したユーザー**します。  
  
15. 選択、**追加**ボタンをクリックし、、 **OK**ボタンをクリックします。  
  
     アクションのステートメントを今すぐ**設定割り当てに現在の項目: CreatedBy に**します。  
  
## <a name="save-and-deploy-the-reusable-workflow"></a>保存し、再利用可能なワークフローの配置
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]のみインポートできます *.wsp*ファイルとして再利用可能なワークフローを保存する必要があります、 *.wsp*ファイルにインポートする前に SharePoint にデプロイ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。  
  
> [!IMPORTANT]  
>  SharePoint サイトにアクセス権があるシステム上の手順を実行する必要が、次の手順を実行するランタイム エラーが発生した場合。  
  
#### <a name="to-save-and-deploy-the-reusable-workflow"></a>保存して再利用可能なワークフローをデプロイするには  
  
1.  SharePoint Designer の上部にある次のように選択します、**保存**、進捗を保存してボタンをクリックし、選択し、**発行**にワークフローを展開する ボタン、 **SPD1** SharePoint サイト.  
  
2.  ナビゲーション ウィンドウで選択、**ワークフロー**オブジェクト。  
  
3.  **再利用可能なワークフロー**、選択**SPD タスク ワークフロー**します。  
  
4.  リボンで、選択、**テンプレートとして保存**としてワークフローを保存するボタン、 *.wsp*ファイル。  
  
5.  開く、 **SPD1**を表示するブラウザーで SharePoint サイト、 *.wsp* SharePoint 内のファイル。  
  
6.  クイック起動バーで、**ライブラリ**リンク。  
  
7.  **ドキュメント ライブラリ**セクションで、選択、**サイト資産を**リンク。  
  
     **SPD タスク ワークフロー**サイト資産を他のファイルが表示されます。  
  
8.  ファイルの一覧で、そのファイルの名前を選択します。  
  
9. **ファイルのダウンロード** ダイアログ ボックスで、選択、**保存**を保存するボタン、 *.wsp*ローカル システム上のファイル。  
  
## <a name="import-the-wsp-file-into-visual-studio"></a>Visual Studio に .wsp ファイルをインポートします。
 インポート、 *.wsp*ファイルを[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]再利用可能なワークフローのインポート プロジェクトを使用しています。 このプロジェクトは、再利用可能な宣言型ワークフローをワークフロー コード ワークフローに変換します。 ワークフローが変換された後は、その動作を変更するのにコードを使用します。  
  
#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>.Wsp ファイルからワークフローをインポートし、それを変更するには  
  
1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、メニュー バーで、**ファイル** > **新規** > **プロジェクト**します。  
  
2. **新しいプロジェクト** ダイアログ ボックスで、展開、 **SharePoint**のどちらかのノード**Visual c#** または**Visual Basic**、を選択し、**2010**ノード。  
  
3. **テンプレート**ウィンドウで、選択、**再利用可能な SharePoint 2010 ワークフローのインポート**テンプレートとしてプロジェクトの名前をそのまま**WorkflowImportProject1**、選択し、**OK**ボタンをクリックします。  
  
    SharePoint カスタマイズ ウィザードが表示されます。  
  
4. **デバッグのサイトとセキュリティのレベルを指定**ページで、入力、[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]以前に作成した 2 番目の SharePoint サブサイトの: http://<em>システム名</em>/SPD2 します。  
  
5. **この SharePoint ソリューションの信頼レベルとは何ですか?** セクションで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックして、**次**ボタン。  
  
    サンド ボックスの詳細については、ファーム ソリューションではなく、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)します。  
  
6. **新しいプロジェクトのソースを指定** ページで、以前に保存する場所、システム上の場所を参照、 *.wsp*ファイル、ファイルを開いて、および選択し、**次**ボタンをクリックします。  
  
   > [!NOTE]  
   >  選択、**完了**で利用可能なすべての項目をインポートする ボタン、 *.wsp*ファイル。  
  
    これには、インポートするために使用できる、再利用可能なワークフローの一覧が表示されます。  
  
7. **をインポートする項目の選択**ボックスで、選択、 **SPD タスク ワークフロー**ワークフローを選択し、 **[完了]** ボタン。  
  
    プロジェクトの名前、インポート操作が完了すると、 **WorkflowImportProject1**という名前のワークフローを含む作成**SPD_Workflow_TestFT**します。 このフォルダーには、ワークフローの定義ファイルが*Elements.xml*とワークフロー デザイナー ファイル (*.xoml*)。 デザイナーには、2 つのファイルが含まれています。 ルール ファイル (.rules) と分離コード ファイル (いずれか *.cs*または *.vb*プロジェクトのプログラミング言語に応じて、)。  
  
8. **ソリューション エクスプ ローラー**、削除、**インポートされたファイルの他の**フォルダー。  
  
9. *Elements.xml*ファイルで、削除`InstantiationURL="_layouts/IniErkflIP.sspx"`します。  
  
10. **ソリューション エクスプ ローラー**、選択**WorkflowImportProject1**、メニュー バーで、次のように選択します**プロジェクト** > **スタートアップ プロジェクトとして設定。** を設定する**WorkflowImportProject1**スタートアップ アイテムとして。  
  
     プロジェクトをデバッグするときにすぐに、一覧が表示されます。  
  
11. **再利用可能な SharePoint 2010 ワークフローのインポート**テンプレートは、インポートしたワークフローの関連付けプロパティの値をインポートしない、これらを入力する必要があります。 この操作を行うには、次の手順を実行します。  
  
    1.  **ソリューション エクスプ ローラー**、選択、 **SPD_Workflow_TestFT**ノード。  
  
    2.  省略記号 (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円")) など、一覧のプロパティの横にあるボタン、**ターゲット リスト**プロパティ。  
  
    3.  SharePoint カスタマイズ ウィザードの欠損値を入力し、、**完了**ボタンをクリックします。  
  
12. .Xoml ファイルを選択し、次に、メニュー バーで、次のように選択します。**ビュー** > **デザイナー**をワークフロー デザイナーで、インポートされたワークフローを表示します。  
  
13. **Windows Workflow v3.0**のノード、**ツールボックス**、次の手順のいずれかを実行します。  
  
    - ショートカット メニューを開き、**コード**アクティビティを選び、**コピー**します。 ワークフロー デザイナーで下にある行のショートカット メニューを開き、 **SequenceActivity1**アクティビティを選び、**貼り付け**。  
  
    - ドラッグ、**コード**からのアクティビティ、**ツールボックス**をワークフロー デザイナー、および下にある行への接続、 **SequenceActivity1**アクティビティ。  
  
      これは、という名前のワークフロー デザイナーにアクティビティが追加されます**CodeActivity1**します。 このアクティビティでは、ユーザー、ワークフローの開始時に、お知らせリストにお知らせを作成するコードをアクションを追加します。  
  
14. 次のいずれかの操作を実行します。  
  
    -   ダブルクリック**CodeActivity1**をイベント ハンドラーを生成して、コードを表示します。  
  
    -   **プロパティ**ウィンドウ**CodeActivity1**の値を設定、 **ExecuteCode**プロパティを**codeActivity_ExecuteCode**します。  
  
15. 既存の下に次の追加**を使用して**または**Imports**ステートメント。  
  
     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. 置換`codeActivity1_ExecuteCode`次。  
  
     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## <a name="deploy-the-project-and-associate-the-workflow"></a>プロジェクトを配置して、ワークフローの関連付け
 次に、WorkflowImportProject1 を実行する SharePoint サイトにデプロイし、タスク リストを表示および変更、テスト、ワークフローを関連付ける変換ワークフロー。  
  
#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>プロジェクトを配置し、ワークフローを関連付ける  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、選択、 **F5**実行し、変換後のワークフロー プロジェクトを配置するキー。  
  
2.  クイック起動バーで、**タスク**タスク一覧を表示するリンク。  
  
3.  **リスト ツール** タブで、選択、**項目**ボタンをクリックし、選択、**新しい項目の**ボタンをクリックします。  
  
     **タスク - 新しい項目の** ダイアログ ボックスが表示されます。  
  
4.  **タイトル**ボックスに、入力**新しいタスク**、選択し、**保存**ボタンをクリックします。  
  
5.  **リスト ツール**] タブで、選択、**一覧**ボタンをクリックし、[、**一覧の設定**ボタンをクリックします。  
  
     **一覧の設定**ページが表示されます。  
  
6.  **権限と管理**セクションで、選択、**ワークフロー設定**リンク。  
  
     **ワークフロー設定**ページが表示されます。  
  
7.  選択、**ワークフローに追加**リンク。  
  
8.  **ワークフロー**一覧で、選択**WorkflowImportProject1 - SPD ワークフロー テスト**します。  
  
9. **名前**ボックスに、入力**SPD ワークフロー テスト**、選択し、 **OK**ボタン。  
  
10. クイック起動バーで、選択、**タスク**一覧。  
  
11. 横にある矢印を選択**新しいタスク**、一覧で、次のように選択します。**ワークフロー**します。  
  
12. **新しいワークフローを開始**セクションで、リンクを選択**SPD ワークフロー テスト**、選択し、**開始**ワークフローを開始するボタンをクリックします。  
  
    > [!NOTE]  
    >  またはを自動的に関連付けますワークフロー一覧がワークフロー設定ウィザードの実行を自動的に関連付けるワークフローを設定します。  
  
     2 つのアクションは、ワークフローによって実行されたことに注意してください: で、タスクの表示名**に割り当てられている**列とお知らせが表示されます、**お知らせ**一覧。  
  
## <a name="see-also"></a>関連項目
 [既存の SharePoint サイトからアイテムをインポートします。](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [SharePoint ソリューションを開発します。](../sharepoint/developing-sharepoint-solutions.md)   
 [Web パーツまたはアプリケーション ページの再利用可能なコントロールを作成します。](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
