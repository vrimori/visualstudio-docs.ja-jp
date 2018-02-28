---
title: "チュートリアル: プロジェクト タスク リスト定義を展開する |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 4d91b1b40ac99ca3984f772b77a16258a1bddf51
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-deploying-a-project-task-list-definition"></a>チュートリアル: プロジェクト タスク リスト定義の配置
  このチュートリアルで使用する方法[!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]を作成、カスタマイズ、デバッグ、およびプロジェクトのタスクを追跡するために SharePoint リストを展開します。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   [SharePoint リストを作成する](#CreatingListDef)です。  
  
-   [SharePoint リストを作成する](#CreatingListDef)です。  
  
-   [イベント レシーバーの追加](#AddEventRcvr)です。  
  
-   [プロジェクト タスク リストの機能をカスタマイズする](#CustomizeFeature)です。  
  
-   [タスク一覧のビルドとテスト プロジェクト](#BuildTest)です。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)]版の Visual Studio アプリケーション ライフ サイクル管理 (ALM) のいずれか。  
  
##  <a name="CreatingListDef"></a>SharePoint リストを作成します。  
 SharePoint リスト プロジェクトを作成し、タスクと、リスト定義を関連付けます。  
  
#### <a name="to-create-a-sharepoint-list-project"></a>SharePoint リスト プロジェクトを作成するには  
  
1.  開く、**新しいプロジェクト** ダイアログ ボックスで、展開、 **SharePoint**  ノードを選択し、 **2010**ノード。  
  
2.  **テンプレート** ウィンドウで、選択、 **SharePoint 2010 プロジェクト**名では、プロジェクト テンプレートは、 **ProjectTaskList**を選択し、 **OK**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
3.  デバッグに使用するローカル SharePoint サイトを指定してを選択、**ファーム ソリューションとして配置**オプション ボタンをクリックして、**完了**ボタンをクリックします。  
  
4.  プロジェクトのショートカット メニューを開き、選択**追加**、**新しい項目の**します。  
  
5.  **テンプレート** ウィンドウで、選択、**リスト**テンプレートを選択し、**追加**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
6.  **リストの表示する名前?**ボックスに、入力**プロジェクト タスク リスト**です。  
  
7.  選択、**の既存のリストの種類に基づくカスタマイズ不可のリストを作成する**オプション ボタン、およびその後、その一覧で次のように選択します。**タスク**、を選択し、**完了**ボタンをクリックします。  
  
     表示されるボックスの一覧、機能、およびパッケージ**ソリューション エクスプ ローラー**です。  
  
##  <a name="AddEventRcvr"></a>イベント レシーバーの追加  
 タスク一覧に自動的に期限を設定するイベント レシーバーを追加できます日付とタスクの説明。 次の手順では、イベント レシーバーとして、リスト インスタンスを単純なイベント ハンドラーを追加します。  
  
#### <a name="to-add-an-event-receiver"></a>イベント レシーバーを追加するには  
  
1.  プロジェクト ノードのショートカット メニューを開き、選択**追加**を選択し**新しい項目の**します。  
  
2.  SharePoint テンプレートの一覧で選択、**イベント レシーバー**テンプレート、し、名前を**ProjectTaskListEventReceiver**です。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
3.  **[イベント レシーバー設定**ページで、選択**リスト項目イベント**でイベント レシーバーの種類として、**イベント レシーバーの種類をクリックしてください**] ボックスの一覧です。  
  
4.  **イベント ソースとなる項目**一覧で、選択**タスク**です。  
  
5.  処理するイベントの一覧で、、の横にチェック ボックス**項目が追加されました**を選択し、**完了**ボタンをクリックします。  
  
     新しいイベント レシーバーのノードがというコード ファイルをプロジェクトに追加**ProjectTaskListEventReceiver**です。  
  
6.  コードを追加して、`ItemAdded`メソッドで、 **ProjectTaskListEventReceiver**コード ファイル。 新しいタスクを追加すると、たびに、既定の期限の日付と説明が、タスクに追加します。 既定の期限の日付が 2009 年 7 月 1 日です。  
  
     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]  
  
##  <a name="CustomizeFeature"></a>プロジェクト タスク リストの機能をカスタマイズします。  
 SharePoint ソリューションを作成するときに Visual Studio に自動的に特徴を作成、既定のプロジェクト項目です。 SharePoint サイトのプロジェクト タスク リストの設定をカスタマイズするには、フィーチャー デザイナーを使用します。  
  
#### <a name="to-customize-the-project-task-list-feature"></a>プロジェクト タスク リストの機能をカスタマイズするには  
  
1.  **ソリューション エクスプ ローラー**、展開**機能**します。  
  
2.  ショートカット メニューを開き、 **Feature1**を選択し**ビュー デザイナー**です。  
  
3.  **タイトル**ボックスに、入力**プロジェクト タスク リスト フィーチャー**です。  
  
4.  **スコープ**一覧で、選択**Web**です。  
  
5.  **プロパティ**ウィンドウで、入力**1.0.0.0**の値として、**バージョン**プロパティです。  
  
##  <a name="CustomizePackage"></a>プロジェクト タスク リストのパッケージをカスタマイズします。  
 SharePoint プロジェクトを作成するときに Visual Studio は自動的にパッケージする既定のプロジェクト項目を含む機能を追加します。 パッケージ デザイナーを使用して、SharePoint サイト用のプロジェクト タスク リストの設定をカスタマイズすることができます。  
  
#### <a name="to-customize-the-project-task-list-package"></a>プロジェクト タスク リストのパッケージをカスタマイズするには  
  
1.  **SolutionExplorer**、ショートカット メニューを開き、**パッケージ**を選択し**ビュー デザイナー**です。  
  
2.  **名前**ボックスに、入力**ProjectTaskListPackage**です。  
  
3.  選択、 **Web サーバーのリセット**チェック ボックスをオンします。  
  
##  <a name="BuildTest"></a>ビルドとテスト プロジェクトのタスク一覧  
 プロジェクトを実行すると、SharePoint サイトが開きます。 ただし、タスク リストの場所に、手動で移動する必要があります。  
  
#### <a name="to-test-the-project-task-list"></a>プロジェクトのタスクの一覧をテストするには  
  
1.  ビルドして、プロジェクト タスク リストを展開するには、F5 キーを選択します。  
  
     SharePoint サイトが開きます。  
  
2.  選択、**ホーム**タブです。  
  
3.  左のサイドバーで、選択、**プロジェクト タスク リスト**リンクします。  
  
     プロジェクトのタスク一覧 ページが表示されます。  
  
4.  **リスト ツール** タブで、選択、**項目**タブです。  
  
5.  **項目**グループで、選択、**新しい項目の**ボタンをクリックします。  
  
6.  **タイトル**テキスト ボックスに、入力**Task1**です。  
  
7.  選択、**保存**ボタンをクリックします。  
  
     サイトが更新された後、 **Task1** 2009 年 7 月 1 日の期限のタスクが表示されます。  
  
8.  選択**Task1**です。  
  
     タスクの詳細なビューが表示され、「これは、重要なタスクです」です説明の表示  
  
##  <a name="Deploy"></a>プロジェクトのタスクの一覧を展開します。  
 ビルドしてテスト プロジェクト タスク リストの後に展開できます、*ローカル システム*または*リモート システム*です。 ローカル システムは、別のコンピューターのリモート システムには、ソリューションを開発する同じコンピューターです。  
  
#### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>ローカル システムにプロジェクトのタスクの一覧を展開するには  
  
1.  Visual Studio メニュー バーで、**ビルド**、**ソリューションの配置**です。  
  
     Visual Studio で、IIS アプリケーション プールがリサイクルされる、ソリューションの既存のバージョンはすべて取り消されます、SharePoint にソリューション パッケージ (.wsp) ファイルをコピー、およびし、その機能をアクティブにします。 SharePoint のソリューションを使えるようになりました。 展開の構成手順の詳細については、次を参照してください。[する方法: SharePoint の配置構成を編集](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)です。  
  
#### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>リモート システムにプロジェクトのタスクの一覧を展開するには  
  
1.  Visual Studio メニュー バーで、**ビルド**、**発行**です。  
  
2.  **発行** ダイアログ ボックスで、選択、**ファイル システムに公開**オプション ボタンをクリックします。  
  
     ターゲットの場所を変更することができます、**発行**省略記号ボタンをクリックしてダイアログ ボックス![省略記号アイコン](../sharepoint/media/ellipsisicon.gif "省略記号アイコン")とし、別の場所に移動します。  
  
3.  選択、**発行**ボタンをクリックします。  
  
     ソリューションの .wsp ファイルが作成されます。  
  
4.  .Wsp ファイルをリモートの SharePoint のシステムにコピーします。  
  
5.  PowerShell を使用して`Add-SPUserSolution`をリモートの SharePoint のインストール パッケージをインストールするコマンド。 (ファーム ソリューションを使用して、`Add-SPSolution`コマンドです)。  
  
     たとえば、`Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp` のようにします。  
  
6.  PowerShell を使用して`Install-SPUserSolution`ソリューションを配置するコマンド。 (ファーム ソリューションを使用して、`Install-SPSolution`コマンドです)。  
  
     たとえば、`Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName` のようにします。  
  
     リモート展開の詳細については、次を参照してください。[を使用してソリューション](http://go.microsoft.com/fwlink/?LinkId=217680)と[の追加および SharePoint 2010 で PowerShell を使用したソリューションの配置](http://go.microsoft.com/fwlink/?LinkId=217682)です。  
  
## <a name="next-steps"></a>次の手順  
 カスタマイズし、次のトピックからの SharePoint ソリューションを展開する方法の詳細を学習できます。  
  
-   [チュートリアル: SharePoint のサイト列、コンテンツ タイプ、およびリストの作成](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)  
  
-   [方法: イベント レシーバーを作成する](../sharepoint/how-to-create-an-event-receiver.md)  
  
-   [SharePoint Server 2010 用の Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=217684)  
  
## <a name="see-also"></a>参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  