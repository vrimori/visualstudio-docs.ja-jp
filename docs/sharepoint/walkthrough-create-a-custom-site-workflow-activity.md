---
title: 'チュートリアル: サイトのカスタム ワークフロー アクティビティの作成 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4cf57ccb62d5a87a3dfb516cc1d7b03f45d609ad
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875187"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>チュートリアル: サイトのカスタム ワークフロー アクティビティを作成します。
  このチュートリアルを使用して、サイト レベルのワークフローのカスタム アクティビティを作成する方法について説明[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 (サイト レベルのワークフローは、サイトの一覧だけでなく、サイト全体に適用)。カスタム アクティビティは、バックアップお知らせリストを作成し、そこにお知らせリストの内容をコピーします。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
- サイト レベルのワークフローを作成します。  
  
- カスタム ワークフロー アクティビティを作成します。  
  
- 作成して、SharePoint リストを削除しています。  
  
- 別の 1 つのリストから項目をコピーします。  
  
- クイック起動バーに一覧を表示しています。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]および SharePoint。
  
-   Visual Studio  
  
## <a name="create-a-site-workflow-custom-activity-project"></a>サイト ワークフロー カスタム アクティビティ プロジェクトを作成します。
 最初に、保持し、カスタム ワークフロー アクティビティをテストするプロジェクトを作成します。  
  
#### <a name="to-create-a-site-workflow-custom-activity-project"></a>サイト ワークフロー カスタム アクティビティ プロジェクトを作成するには  
  
1.  メニュー バーで、**ファイル** > **新規** > **プロジェクト**を表示する、**新しいプロジェクト** ダイアログ ボックス。  
  
2.  展開、 **SharePoint**のどちらかのノード**Visual c#** または**Visual Basic**を選択し、 **2010**ノード。  
  
3.  **テンプレート**ウィンドウで、選択、 **SharePoint 2010 プロジェクト**テンプレート。  
  
4.  **名前**ボックスに、入力**AnnouncementBackup**、選択し、 **OK**ボタン。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
5.  **デバッグのサイトとセキュリティのレベルを指定**ページで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックして、 **[完了]** ボタンをクリックします信頼レベルと既定のサイトです。  
  
     この手順では、ファーム ソリューションでは、ワークフロー プロジェクトでのみ利用可能なオプションとして、ソリューションの信頼レベルを設定します。  
  
6.  **ソリューション エクスプ ローラー**をプロジェクト ノードを選択し、メニュー バーで、次のように選択します。**プロジェクト** > **新しい項目の追加**します。  
  
7.  いずれかで**Visual c#** または**Visual Basic**、展開、 **SharePoint**ノードを選択し、 **2010**ノード。  
  
8.  **テンプレート**ウィンドウで、選択、**シーケンシャル ワークフロー (ファーム ソリューションのみ)** テンプレートを選択し、**追加**ボタン。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
9. **デバッグ ワークフローの名前を指定** ページで、既定の名前 (AnnouncementBackup - Workflow1)。 ワークフロー テンプレートの種類に変更**サイト ワークフロー**、選択し、**次**ボタン。  
  
10. 選択、**完了**残りの既定の設定をそのまま使用するボタンをクリックします。  
  
## <a name="add-a-custom-workflow-activity-class"></a>カスタム ワークフロー アクティビティ クラスを追加します。
 次に、カスタム ワークフロー アクティビティのコードを含むプロジェクトにクラスを追加します。  
  
#### <a name="to-add-a-custom-workflow-activity-class"></a>カスタム ワークフロー アクティビティ クラスを追加するには  
  
1.  メニュー バーで、**プロジェクト** > **新しい項目の追加**を表示する、**新しい項目の追加** ダイアログ ボックス。  
  
2.  **インストールされたテンプレート**ツリー ビューで、選択、**コード**ノードを選択し、**クラス**プロジェクト項目テンプレートの一覧にテンプレート。 既定の class1 という名前を使用します。 **[追加]** ボタンをクリックします。  
  
3.  次のようにすべての Class1 コードに置き換えます。  
  
     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]  
  
4.  プロジェクトを保存し、次に、メニュー バーで、次のように選択します。**ビルド** > **ソリューションのビルド**します。  
  
     Class1 がカスタム動作として表示されます、**ツールボックス**上、 **AnnouncementBackup コンポーネント**タブ。  
  
## <a name="add-the-custom-activity-to-the-site-workflow"></a>サイト ワークフローにカスタム アクティビティを追加します。
 次に、カスタム コードを含むワークフローにアクティビティを追加します。  
  
#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>サイト ワークフローにカスタム アクティビティを追加するには
  
1.  Workflow1 をワークフロー デザイナーのデザイン ビューで開きます。  
  
2.  Class1 からドラッグして、**ツールボックス**下に表示されるので、`onWorkflowActivated1`アクティビティ、または、Class1 用に開くショートカット メニューを選択**コピー**、下にある行のショートカット メニューを開き、 `onWorkflowActivated1`アクティビティを選び、**貼り付け**します。  
  
3.  プロジェクトを保存します。  
  
## <a name="test-the-site-workflow-custom-activity"></a>サイト ワークフローのカスタム アクティビティをテストします。
 次に、プロジェクトを実行し、サイトのワークフローを開始します。 カスタム アクティビティは、バックアップお知らせリストを作成し、そこに現在のお知らせリストから内容をコピーします。 コードでは、バックアップ リストが 1 つを作成する前に既に存在するかどうかも確認します。 バックアップのリストが既に存在する場合は削除されます。 また、リンクを SharePoint サイトのクイック起動バーに新しいリストに追加します。  
  
#### <a name="to-test-the-site-workflow-custom-activity"></a>サイト ワークフローのカスタム アクティビティをテストするには  
  
1.  選択、 **F5**プロジェクトを実行し、SharePoint に配置するキー。  
  
2.  クイック起動バーで、**一覧**すべての SharePoint サイトで使用可能な一覧を表示するリンク。 お知らせという名前のリストを 1 つだけが**お知らせ**します。  
  
3.  SharePoint web ページの上部にある選択、**サイト ワークフロー**リンク。  
  
4.  開始新しいワークフローのセクションでは、選択、 **AnnouncementBackup - Workflow1**リンク。 これはサイト ワークフローを開始し、カスタム アクションで、コードを実行します。  
  
5.  クイック起動バーで、**お知らせバックアップ**リンク。 注意してに格納されているお知らせはすべて、**お知らせ**一覧は、この新しいリストにコピーされています。  
  
## <a name="see-also"></a>関連項目
 [方法: イベント レシーバーを作成します。](../sharepoint/how-to-create-an-event-receiver.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
