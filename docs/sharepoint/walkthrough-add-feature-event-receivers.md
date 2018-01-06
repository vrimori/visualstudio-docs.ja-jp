---
title: "チュートリアル: フィーチャー イベント レシーバーの追加 |Microsoft ドキュメント"
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
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
ms.assetid: fbd44c33-2c27-4d57-abca-21cddc16fbc3
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6250673ae2fa262fbe932aea79e36aeb6b0d0915
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-add-feature-event-receivers"></a>チュートリアル: フィーチャーのイベント レシーバーの追加
  フィーチャー イベント レシーバーとは、SharePoint で、次の機能に関連するイベントのいずれかが発生したときに実行する方法です。  
  
-   機能をインストールします。  
  
-   フィーチャーがアクティブです。  
  
-   フィーチャーが非アクティブ化します。  
  
-   機能が削除されます。  
  
 このチュートリアルでは、SharePoint プロジェクトの機能には、イベント レシーバーを追加する方法を示します。 これには、次のタスクを示しています。  
  
-   フィーチャー イベント レシーバーで空のプロジェクトを作成しています。  
  
-   処理、 **FeatureDeactivating**メソッドです。  
  
-   SharePoint プロジェクトのオブジェクト モデルを使用して、お知らせをお知らせリストに追加します。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   Visual Studio  
  
## <a name="creating-a-feature-event-receiver-project"></a>フィーチャー イベント レシーバー プロジェクトを作成します。  
 最初に、フィーチャー イベント レシーバーを含めるためのプロジェクトを作成します。  
  
#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>フィーチャー イベント レシーバーでプロジェクトを作成するには  
  
1.  メニュー バーで、次のように選択します。**ファイル**、**新規**、**プロジェクト**を表示する、**新しいプロジェクト** ダイアログ ボックス。  
  
2.  展開、 **SharePoint**ノード**Visual c#**または**Visual Basic**を選択し、 **2010**ノード。  
  
3.  **テンプレート** ウィンドウで、選択、 **SharePoint 2010 プロジェクト**テンプレート。  
  
     プロジェクト テンプレートがないために、フィーチャー イベント レシーバーのこのプロジェクトの種類を使用するとします。  
  
4.  **名**ボックスに、入力**FeatureEvtTest**を選択し、 **OK**を表示するボタン、 **SharePoint カスタマイズ ウィザード**です。  
  
5.  **デバッグのサイトとセキュリティ レベルを指定して**ページで、新しい項目のカスタム フィールドを追加する SharePoint サーバー サイトの URL を入力するか、既定の場所を使用して (http://\<*システム名前*>/)。  
  
6.  **この SharePoint ソリューションの信頼レベルは何ですか?**セクションで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックします。  
  
     サンド ボックス ソリューションとファーム ソリューションの詳細については、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)です。  
  
7.  選択、**完了**ボタンをクリックし、Feature1 をという名前のフィーチャーが表示されることに注意してください、**機能**ノード。  
  
## <a name="adding-an-event-receiver-to-the-feature"></a>フィーチャー イベント レシーバーの追加  
 次に、フィーチャー イベント レシーバーを追加し、フィーチャーが非アクティブ化されたときに実行されるコードを追加します。  
  
#### <a name="to-add-an-event-receiver-to-the-feature"></a>フィーチャー イベント レシーバーを追加するには  
  
1.  機能 ノードのショートカット メニューを開き、選択**フィーチャーの追加**フィーチャーを作成します。  
  
2.  下にある、**機能**ノード、ショートカット メニューを開き、 **Feature1**を選択し**イベント レシーバーの追加**フィーチャー イベント レシーバーを追加します。  
  
     これには、[feature1] の下のコード ファイルが追加されます。 この場合、という名前が Feature1.EventReceiver.cs または Feature1.EventReceiver.vb のいずれか、プロジェクトの開発言語に応じて。  
  
3.  プロジェクトが記述されている場合[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]がない場合、イベント レシーバーの上部にある次のコードを追加します。  
  
     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  イベント レシーバー クラスには、イベントとして機能するいくつかのコメント アウトされたメソッドが含まれています。 置換、 **FeatureDeactivating**を次のメソッド。  
  
     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]  
  
## <a name="testing-the-feature-event-receiver"></a>フィーチャー イベント レシーバーのテスト  
 次に、テスト対象の機能を非アクティブ化するかどうか、 **FeatureDeactivating**メソッドは、SharePoint のお知らせリストにアナウンスを出力します。  
  
#### <a name="to-test-the-feature-event-receiver"></a>フィーチャー イベント レシーバーをテストするには  
  
1.  プロジェクトの値を設定**アクティブな配置構成**プロパティを**アクティブ化しない**です。  
  
     このプロパティを設定して、SharePoint でアクティブ化処理により、機能、フィーチャーのイベント レシーバーをデバッグすることができます。 詳細については、次を参照してください。 [SharePoint ソリューションのデバッグ](../sharepoint/debugging-sharepoint-solutions.md)です。  
  
2.  選択、 **f5 キーを押して**キーをプロジェクトを実行し、SharePoint に配置します。  
  
3.  SharePoint Web ページの上部で、開く、**サイトの操作** メニューを選択し**サイト設定**です。  
  
4.  下にある、**サイトの操作**のセクションで、**サイト設定**ページで、選択、**サイト機能の管理**リンクします。  
  
5.  **機能**ページで、選択、 **Activate**横に、 **FeatureEvtTest Feature1**機能します。  
  
6.  **機能**ページで、選択、 **Deactivate**横に、 **FeatureEvtTest Feature1**機能を選択し、**このフィーチャーを非アクティブ**機能を非アクティブ化するリンクを確認します。  
  
7.  選択、**ホーム**ボタンをクリックします。  
  
     お知らせが表示されます、**お知らせ**フィーチャーが非アクティブ化された後に一覧表示します。  
  
## <a name="see-also"></a>参照  
 [方法: イベント レシーバーを作成します。](../sharepoint/how-to-create-an-event-receiver.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  
  