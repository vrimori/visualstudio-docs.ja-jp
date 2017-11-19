---
title: "チュートリアル: カスタム サイト ワークフロー アクティビティの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
ms.assetid: 8219a779-c27b-4186-92c9-5bda03328aa9
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6d3579c3d537dc13723cbe285b454b24d079fe1f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>チュートリアル: サイトのカスタム ワークフロー アクティビティの作成
  このチュートリアルは、カスタム アクティビティを使用して、サイト レベルのワークフローを作成する方法を示します[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 (サイト レベルのワークフローは、サイトの一覧だけでなく、サイト全体に適用)。カスタム アクティビティは、バックアップお知らせリストを作成し、そこにお知らせリストの内容をコピーします。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   サイト レベルのワークフローを作成します。  
  
-   カスタム ワークフロー アクティビティを作成します。  
  
-   作成して、SharePoint リストの削除します。  
  
-   1 つのリストから別の項目をコピーします。  
  
-   クイック起動バーに一覧を表示しています。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]および SharePoint。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   Visual Studio  
  
## <a name="creating-a-site-workflow-custom-activity-project"></a>サイト ワークフロー カスタム アクティビティ プロジェクトの作成  
 最初に、格納し、カスタム ワークフロー アクティビティをテストするプロジェクトを作成します。  
  
#### <a name="to-create-a-site-workflow-custom-activity-project"></a>サイト ワークフロー カスタム アクティビティ プロジェクトを作成するには  
  
1.  メニュー バーで、次のように選択します。**ファイル**、**新規**、**プロジェクト**を表示する、**新しいプロジェクト** ダイアログ ボックス。  
  
2.  展開、 **SharePoint**ノード**Visual c#**または**Visual Basic**を選択し、 **2010**ノード。  
  
3.  **テンプレート** ウィンドウで、選択、 **SharePoint 2010 プロジェクト**テンプレート。  
  
4.  **名前**ボックスに、入力**AnnouncementBackup**を選択し、 **OK**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
5.  **デバッグのサイトとセキュリティ レベルを指定して**ページで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックして、**完了**ボタンをクリックして、信頼レベルと既定のサイトです。  
  
     この手順では、ファーム ソリューションでは、ワークフロー プロジェクトでのみ使用可能なオプションとして、ソリューションの信頼レベルを設定します。  
  
6.  **ソリューション エクスプ ローラー**、プロジェクト ノードを選択し、次に、メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
7.  いずれかで**Visual c#**または**Visual Basic**、展開、 **SharePoint**  ノードを選択し、 **2010**ノード。  
  
8.  **テンプレート** ウィンドウで、選択、**シーケンシャル ワークフロー (ファーム ソリューションのみ)**テンプレートを選択し、**追加**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
9. **デバッグのワークフローの名前を指定** ページで、既定の名前 (AnnouncementBackup - Workflow1) をそのまま使用します。 ワークフロー テンプレートの種類を変更する**サイト ワークフロー**を選択し、**次**ボタンをクリックします。  
  
10. 選択、**完了**ボタンをクリックして、残りの既定の設定。  
  
## <a name="adding-a-custom-workflow-activity-class"></a>カスタム ワークフロー アクティビティ クラスを追加します。  
 次に、カスタム ワークフロー アクティビティのコードを含むようにプロジェクトにクラスを追加します。  
  
#### <a name="to-add-a-custom-workflow-activity-class"></a>カスタム ワークフロー アクティビティ クラスを追加するには  
  
1.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**を表示する、**新しい項目の追加** ダイアログ ボックス。  
  
2.  **インストールされたテンプレート**ツリー ビューで、選択、**コード** ノードを選択し、**クラス**プロジェクト項目テンプレートの一覧にテンプレート。 Class1 の既定の名前を使用します。 **[追加]** ボタンをクリックします。  
  
3.  Class1 コードのすべて、次に置き換えます。  
  
     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]  
  
4.  プロジェクトを保存し、次に、メニュー バーで、次のように選択します。**ビルド**、**ソリューションのビルド**です。  
  
     Class1 がカスタム動作として表示されます、**ツールボックス**上、 **AnnouncementBackup コンポーネント**タブです。  
  
## <a name="adding-the-custom-activity-to-the-site-workflow"></a>サイト ワークフローにカスタム アクティビティを追加します。  
 次に、カスタム コードを含むワークフローに活動を追加します。  
  
#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>サイト ワークフローにカスタム アクティビティを追加するには  
  
1.  Workflow1 をワークフロー デザイナーのデザイン ビューで開きます。  
  
2.  Class1 からドラッグして、**ツールボックス**の下に表示されるように、 `onWorkflowActivated1` Class1 用には、ショートカット メニューを開くまたはアクティビティを選択**コピー**、下にある行のショートカット メニューを開き、 `onWorkflowActivated1`アクティビティを選択し**貼り付け**です。  
  
3.  プロジェクトを保存します。  
  
## <a name="testing-the-site-workflow-custom-activity"></a>サイト ワークフローのカスタム アクティビティのテスト  
 次に、プロジェクトを実行し、サイトのワークフローを開始します。 カスタム アクティビティは、バックアップお知らせリストを作成し、そこに、現在のお知らせリストから、内容をコピーします。 また、コードは、バックアップ リストは 1 つを作成する前に既に存在するかどうかを確認します。 バックアップ リストが既に存在する場合は削除されます。 コードはまた、SharePoint サイトのクイック起動バーで、新しいリストへのリンクを追加します。  
  
#### <a name="to-test-the-site-workflow-custom-activity"></a>サイト ワークフローのカスタム アクティビティをテストするには  
  
1.  プロジェクトを実行し、SharePoint に配置するには、F5 キーを選択します。  
  
2.  クイック起動バーで、選択、**一覧**すべての SharePoint サイトで使用可能な一覧を表示するリンクです。 お知らせという名前のリストを 1 つだけがあることを確認**お知らせ**です。  
  
3.  SharePoint web ページの上部には、選択、**サイト ワークフロー**リンクします。  
  
4.  新しいワークフローのセクションの開始日を選択して、 **AnnouncementBackup - Workflow1**リンクします。 これにより、サイト ワークフローを開始し、カスタム アクションのコードを実行します。  
  
5.  クイック起動バーで、選択、**お知らせバックアップ**リンクします。 注意してお知らせに含まれるのすべて、**お知らせ**一覧は、この新しいリストにコピーされています。  
  
## <a name="see-also"></a>関連項目  
 [方法: イベント レシーバーを作成します。](../sharepoint/how-to-create-an-event-receiver.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  
  