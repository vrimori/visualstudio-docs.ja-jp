---
title: "チュートリアル: プロジェクト タスク リスト定義の配置"
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
  - "Visual Studio での SharePoint 開発, 配置"
ms.assetid: 18b62016-ed30-4dd1-9dfc-0d7e82c6767f
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# チュートリアル: プロジェクト タスク リスト定義の配置
  このチュートリアルでは、SharePoint リストを作成、カスタマイズ、デバッグ、および、プロジェクト タスクを追跡するために配置する際に [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] を使用する方法を示します。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   [SharePoint リストの作成](#CreatingListDef)。  
  
-   [SharePoint リストの作成](#CreatingListDef)。  
  
-   [イベント レシーバーの追加](#AddEventRcvr)。  
  
-   [プロジェクト タスク リスト フィーチャーのカスタマイズ](#CustomizeFeature)。  
  
-   [プロジェクト タスク リストのビルドとテスト](#BuildTest)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)] または Visual Studio アプリケーション ライフサイクル管理 \(ALM\) のエディション  
  
##  <a name="CreatingListDef"></a> SharePoint リストの作成  
 SharePoint リストのプロジェクトが作成され、そのリスト定義をタスクに関連付けます。  
  
#### SharePoint リストのプロジェクトを作成するには  
  
1.  **\[新しいプロジェクト\]** ダイアログ ボックスを開き、**\[SharePoint\]** ノードを展開し、**2010** ノードを選択します。  
  
2.  **\[テンプレート\]** のペインで、**\[SharePoint 2010 プロジェクト\]** のテンプレートを選択して、プロジェクト ProjectTaskList を付けておくと、**\[OK\]** ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
3.  サイトが、**\[ファーム ソリューションとして配置する\]** のオプション ボタンをクリックし、デバッグに使用するローカル SharePoint を指定し、**\[完了\]** ボタンをクリックします。  
  
4.  プロジェクトのショートカット メニューを開き、**\[新しいアイテム\]**、**\[追加\]** をクリックします。  
  
5.  **\[テンプレート\]** のペインで、**\[リスト\]** テンプレートを選択し、**\[追加\]** ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
6.  **\[リストに表示する名前\]** ボックスで、プロジェクトのタスク リストを入力します。  
  
7.  次に **\[既存のリストの種類に基づくカスタマイズできないリストを作成\]** のオプション ボタンを選択し、一覧で、**\[タスク\]** をクリックします、次へをクリックします **\[完了\]** ボタンをクリックします。  
  
     リスト、フィーチャーおよびパッケージが **\[ソリューション エクスプローラー\]** に表示されます。  
  
##  <a name="AddEventRcvr"></a> イベント レシーバーの追加  
 タスク一覧で、自動的にタスクの期限と説明を設定するイベント レシーバーを追加できます。  次の手順では、イベント レシーバーとして単純なイベント ハンドラーをリスト インスタンスに追加します。  
  
#### イベント レシーバーを追加するには  
  
1.  プロジェクト ノードのショートカット メニューを開き、**\[追加\]** をクリックし、**\[新しい項目\]** を選択します。  
  
2.  SharePoint テンプレートの一覧で、**\[イベント レシーバー\]** テンプレートを選択し、**ProjectTaskListEventReceiver**という名前を付けます。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
3.  **\[イベント レシーバー設定の選択\]** ページで、イベント レシーバーの種類として **\[使用するイベント レシーバーの種類\]** 型の一覧を **\[リスト項目イベント\]** をクリックします。  
  
4.  **\[イベント ソースとなる項目\]** の一覧で、**\[タスク\]** をクリックします。  
  
5.  処理するイベントの一覧で、必要チェック ボックスを **\[項目が追加されました\]** の横にし、**\[完了\]** ボタンをクリックします。  
  
     新しいイベント レシーバー ノードが、**ProjectTaskListEventReceiver** という名前のコード ファイルと共にプロジェクトに追加されます。  
  
6.  **ProjectTaskListEventReceiver** コード ファイルで、`ItemAdded` メソッドにコードを追加します。  新しいタスクが追加されるたびに、既定の期限および説明がタスクに追加されます。  既定の期限は 2009 年 7 月 1 日です。  
  
     [!code-csharp[SPProjectTaskList#1](../snippets/csharp/VS_Snippets_OfficeSP/spprojecttasklist/cs/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]
     [!code-vb[SPProjectTaskList#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spprojecttasklist/vb/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]  
  
##  <a name="CustomizeFeature"></a> プロジェクト タスク リスト フィーチャーのカスタマイズ  
 SharePoint ソリューションを作成すると、既定のプロジェクト項目のフィーチャーが自動的に作成されます。  SharePoint サイトのプロジェクト タスク リスト設定をカスタマイズするには、フィーチャー デザイナーを使用します。  
  
#### プロジェクト タスク リスト フィーチャーをカスタマイズするには  
  
1.  **ソリューション エクスプローラー**で、**\[フィーチャー\]** を展開します。  
  
2.  **\[Feature1\]** のショートカット メニューを開き、**\[デザイナーの表示\]** をクリックします。  
  
3.  **\[タイトル\]** ボックスで、**プロジェクト タスク リスト フィーチャーの**を入力します。  
  
4.  **\[スコープ\]** の一覧で、**\[Web\]** をクリックします。  
  
5.  **\[プロパティ\]** ウィンドウで、**\[バージョン\]** のプロパティの値として **1.0.0.0** を入力します。  
  
##  <a name="CustomizePackage"></a> プロジェクト タスク リスト パッケージのカスタマイズ  
 SharePoint プロジェクトを作成すると、既定のプロジェクト項目を含んだフィーチャーが、Visual Studio によって自動的にパッケージへと追加されます。  SharePoint サイトのプロジェクト タスク リスト設定をカスタマイズするには、パッケージ デザイナーを使用します。  
  
#### プロジェクト タスク リスト パッケージをカスタマイズするには  
  
1.  **\[ソリューション\]\[エクスプローラ\]** で、**\[パッケージ\]** のショートカット メニューを開き、**\[デザイナーの表示\]** をクリックします。  
  
2.  **\[名前\]** ボックスで、**ProjectTaskListPackage**を入力します。  
  
3.  **\[Web サーバーのリセット\]** チェック ボックスをオンにします。  
  
##  <a name="BuildTest"></a> プロジェクト タスク リストのビルドとテスト  
 プロジェクトを実行すると、SharePoint サイトが開きます。  ただし、タスク リストの場所には手動で移動する必要があります。  
  
#### プロジェクト タスク リストをテストするには  
  
1.  プロジェクトのタスク リストをビルドおよび配置するには、F5 キーを押します。  
  
     SharePoint サイトが開きます。  
  
2.  **\[ホーム\]** タブをクリックします。  
  
3.  左サイドバーでは、**\[プロジェクト計画 タスク リスト\]** リンクをクリックします。  
  
     \[プロジェクト タスク リスト\] ページが表示されます。  
  
4.  **\[リスト ツール\]** タブで、**\[項目\]** タブをクリックします。  
  
5.  **\[項目\]** グループでは、**\[新しいアイテム\]** ボタンをクリックします。  
  
6.  **\[タイトル\]** のテキスト ボックスに" Task1 "と入力します。  
  
7.  **\[保存\]** ボタンをクリックします。  
  
     サイトを更新すると、2009 年 7 月 1 日を期限とする **Task1** というタスクが表示されます。  
  
8.  **\[Task1\]** をクリックします。  
  
     タスクの詳細表示になり、"This is a critical task." という説明が表示されます。  
  
##  <a name="Deploy"></a> プロジェクト タスク リストの配置  
 ビルドおよびテストが済んだプロジェクト タスク リストは、*ローカル システム*または*リモート システム*に配置できます。  ローカル システムはソリューションの開発に使用したコンピューターであり、リモート システムはそれとは別のコンピューターです。  
  
#### プロジェクト タスク リストをローカル システムに配置するには  
  
1.  Visual Studio のメニュー バーで、**\[ソリューションの配置\]\[ビルド\]** をクリックします。  
  
     Visual Studio によって IIS アプリケーション プールがリサイクルされ、ソリューションの既存のバージョンがすべて取り消され、ソリューション パッケージ \(.wsp\) ファイルが SharePoint にコピーされ、そのフィーチャーがアクティブ化されます。  これで、SharePoint でソリューションを使用する準備が整いました。  配置構成手順の詳細については、「[方法: SharePoint の配置構成を編集する](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)」を参照してください。  
  
#### プロジェクト タスク リストをリモート システムに配置するには  
  
1.  Visual Studio のメニュー バーで、**\[発行\]\[ビルド\]** をクリックします。  
  
2.  **\[発行\]** ダイアログ ボックスで、**\[ファイル システムに発行する\]** のオプション ボタンを選択します。  
  
     省略記号ボタンをクリックして、別の場所に移動し、**\[発行\]** ![省略記号アイコン](~/sharepoint/media/ellipsisicon.gif "省略記号アイコン") ダイアログ ボックスのターゲットの場所を変更できます。  
  
3.  **\[発行\]** ボタンをクリックします。  
  
     .wsp ファイルがソリューションに作成されます。  
  
4.  .wsp ファイルをリモートの SharePoint システムにコピーします。  
  
5.  PowerShell の `Add-SPUserSolution` コマンドを使用して、リモートの SharePoint インストール環境にパッケージをインストールします\(ファーム ソリューションの場合は `Add-SPSolution` コマンドを使用します\)。  
  
     たとえば、`Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp` のようにします。  
  
6.  PowerShell の `Install-SPUserSolution` コマンドを使用して、ソリューションを配置します\(ファーム ソリューションの場合は `Install-SPSolution` コマンドを使用します\)。  
  
     たとえば、`Install-SPUserSolution –Identity ProjectTaskList.wsp –Site http://NewSiteName` のようにします。  
  
     リモート配置の詳細については、[ソリューションを使用する](http://go.microsoft.com/fwlink/?LinkId=217680) 参照します [SharePoint 2010 の PowerShell の追加、配置のソリューション](http://go.microsoft.com/fwlink/?LinkId=217682)。  
  
## 次の手順  
 SharePoint ソリューションのカスタマイズ方法と配置方法の詳細については、次のトピックを参照してください。  
  
-   [チュートリアル: SharePoint のサイト列、コンテンツ タイプ、およびリストの作成](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)  
  
-   [方法: イベント レシーバーを作成する](../sharepoint/how-to-create-an-event-receiver.md)  
  
-   [SharePoint Server 2010 の Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=217684)  
  
## 参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  