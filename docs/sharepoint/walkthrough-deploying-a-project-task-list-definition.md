---
title: 'チュートリアル: プロジェクト タスク リスト定義の配置 |Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0e0a0338f14ecdea36c5a5678a42a76ae234bb6d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280364"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>チュートリアル: プロジェクト タスク リスト定義を展開します。

このチュートリアルは、使用する方法を示します[!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]を作成、カスタマイズ、デバッグ、およびプロジェクトのタスクを追跡するために SharePoint リストを展開します。

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必須コンポーネント

- サポート対象エディションの Microsoft Windows および SharePoint。

- Visual Studio 2017 または Azure DevOps サービスです。

## <a name="create-a-sharepoint-list"></a>SharePoint リストを作成します。

SharePoint リストのプロジェクトを作成し、リスト定義をタスクに関連付けます。

1. 開く、**新しいプロジェクト** ダイアログ ボックスで、展開、 **SharePoint**ノードを選択し、 **2010**ノード。

2. **テンプレート**ウィンドウで、選択、 **SharePoint 2010 プロジェクト**名では、プロジェクト テンプレートは、 **ProjectTaskList**、選択し、 **OK**ボタンをクリックします。

     **SharePoint カスタマイズ ウィザード**が表示されます。

3. デバッグについては、使用するローカルの SharePoint サイトを指定選択、**ファーム ソリューションとして配置**オプション ボタンをクリックして、**完了**ボタンをクリックします。

4. プロジェクトのショートカット メニューを開き、選択し、**追加** > **新しい項目の**します。

5. **テンプレート**ウィンドウで、選択、**一覧**テンプレートを選択し、**追加**ボタン。

     **SharePoint カスタマイズ ウィザード**が表示されます。

6. **の一覧を表示する名前ですか?** ボックスに、入力**プロジェクト タスク リスト**します。

7. 選択、**の既存のリストの種類を基にカスタマイズ可能なリストを作成する**オプション ボタン、およびその後、その一覧で次のように選択します。**タスク**、選択し、**完了**ボタンをクリックします。

     表示される一覧、機能、およびパッケージ**ソリューション エクスプ ローラー**します。

## <a name="add-an-event-receiver"></a>イベント レシーバーを追加します。

自動的に期限を設定するイベント レシーバーを追加するタスク一覧で日付とタスクの説明。 次の手順では、イベント レシーバーとしてリスト インスタンスに単純なイベント ハンドラーを追加します。

1. プロジェクト ノードのショートカット メニューを開き、選択**追加**を選び、**新しい項目の**します。

2. SharePoint テンプレートの一覧で選択、**イベント レシーバー**テンプレート、し、名前を**ProjectTaskListEventReceiver**します。

     **SharePoint カスタマイズ ウィザード**が表示されます。

3. **イベント レシーバー設定の選択**ページで、選択**リスト項目イベント**でイベント レシーバーの種類として、**イベント レシーバーの種類がする**一覧。

4. **イベント ソースとなる項目**一覧で、選択**タスク**します。

5. 、処理するイベントの一覧で、横にチェック ボックス**項目が追加されました**、選択し、**完了**ボタンをクリックします。

     新しいイベント レシーバーのノードがという名前のコード ファイルをプロジェクトに追加**ProjectTaskListEventReceiver**します。

6. コードを追加して、`ItemAdded`メソッドで、 **ProjectTaskListEventReceiver**コード ファイル。 新しいタスクを追加すると、毎回、期限、説明、既定値が、タスクに追加されます。 既定の期限の日付が 2009 年 7 月 1 日です。

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>プロジェクト タスク リストの機能をカスタマイズします。

SharePoint ソリューションを作成するときに自動的に作成機能は、既定のプロジェクト項目。 フィーチャー デザイナーを使用して、SharePoint サイトのプロジェクト タスク リストの設定をカスタマイズできます。

1. **ソリューション エクスプ ローラー**、展開**機能**します。

2. ショートカット メニューを開き**Feature1**を選び、**ビュー デザイナー**します。

3. **タイトル**ボックスに、入力**プロジェクト タスク リスト機能**します。

4. **スコープ**一覧で、選択**Web**します。

5. **プロパティ**ウィンドウで、入力**1.0.0.0**の値として、**バージョン**プロパティ。

## <a name="customize-the-project-task-list-package"></a>プロジェクト タスク リストのパッケージをカスタマイズします。

SharePoint プロジェクトを作成するときに Visual Studio でパッケージに既定のプロジェクト項目が含まれている機能が自動的に追加します。 パッケージ デザイナーを使用して、SharePoint サイトのプロジェクト タスク リストの設定をカスタマイズできます。

1. **SolutionExplorer**、ショートカット メニューを開き**パッケージ**を選び、**ビュー デザイナー**します。

2. **名前**ボックスに、入力**ProjectTaskListPackage**します。

3. 選択、 **Web サーバーのリセット**チェック ボックスをオンします。

## <a name="build-and-test-the-project-task-list"></a>ビルドし、テスト プロジェクトのタスク一覧

プロジェクトを実行すると、SharePoint サイトが開きます。 ただし、タスク一覧の場所に、手動で移動する必要があります。

1. 選択、 **F5**キーをビルドして、プロジェクト タスク リストを展開します。

     SharePoint サイトが開きます。

2. 選択、**ホーム**タブ。

3. 左のサイド バーで、選択、**プロジェクト タスク リスト**リンク。

     プロジェクト タスク リスト ページが表示されます。

4. **リスト ツール** タブで、選択、**項目**タブ。

5. **項目**グループで、選択、**新しい項目の**ボタンをクリックします。

6. **タイトル**テキスト ボックスに、入力**Task1**します。

7. 選択、**保存**ボタンをクリックします。

     サイトが更新された後、 **Task1**タスクは、2009 年 7 月 1 日の期限日が表示されます。

8. 選択**Task1**します。

     タスクの詳細なビューが表示されたら、説明は、「重要なタスクがこの。」を示しています。

## <a name="deploy-the-project-task-list"></a>プロジェクト タスク リストを展開します。

ビルドして、プロジェクト タスク リストをテストした後を展開、*ローカル システム*または*リモート システム*します。 ローカル システムは、別のコンピューターのリモート システムには、ソリューションを開発した同じコンピューターです。

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>ローカル システムにプロジェクトのタスクの一覧を展開するには

Visual Studio メニュー バーで、**ビルド** > **ソリューションの配置**します。

Visual Studio、IIS アプリケーション プールのリサイクル、以前のバージョンのソリューションを取り消します、ソリューション パッケージのコピー (*.wsp*) を SharePoint にファイルを開き、その機能をアクティブにします。 SharePoint でソリューションを使えるようになりました。 展開の構成手順の詳細については、次を参照してください。[方法: SharePoint の配置構成を編集](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)します。

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>リモート システムにプロジェクトのタスクの一覧を展開するには

1. Visual Studio メニュー バーで、**ビルド** > **発行**します。

2. **発行** ダイアログ ボックスで、選択、**ファイル システムに公開**オプション ボタンをクリックします。

     ターゲットの場所を変更することができます、**発行**省略記号ボタンをクリックしてダイアログ ボックス![省略記号アイコン](../sharepoint/media/ellipsisicon.gif "省略記号アイコン")別の場所に移動します。

3. 選択、**発行**ボタンをクリックします。

     A *.wsp*ソリューションのファイルが作成されます。

4. コピー、 *.wsp*リモート SharePoint システムへのファイル。

5. PowerShell を使用して`Add-SPUserSolution`リモートの SharePoint のインストール パッケージをインストールするコマンド。 (ファーム ソリューションでは、使用、`Add-SPSolution`コマンド)。

     たとえば、`Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp` のようにします。

6. PowerShell を使用して`Install-SPUserSolution`ソリューションを配置するコマンド。 (ファーム ソリューションでは、使用、`Install-SPSolution`コマンド)。

     たとえば、`Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName` のようにします。

     リモート展開の詳細については、次を参照してください。[を使用してソリューション](http://go.microsoft.com/fwlink/?LinkId=217680)と[の追加と SharePoint 2010 での PowerShell を使用したソリューションの配置](http://go.microsoft.com/fwlink/?LinkId=217682)します。

## <a name="next-steps"></a>次の手順

カスタマイズし、次のトピックからの SharePoint ソリューションをデプロイする方法の詳細を確認できます。

- [チュートリアル: SharePoint のサイト列、コンテンツの種類、および一覧を作成します。](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [方法: イベント レシーバーを作成](../sharepoint/how-to-create-an-event-receiver.md)

- [SharePoint Server 2010 用の Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=217684)

## <a name="see-also"></a>関連項目
[パッケージ化し、SharePoint ソリューションのデプロイ](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
