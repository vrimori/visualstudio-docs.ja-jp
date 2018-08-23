---
title: 'チュートリアル: フィーチャー イベント レシーバーの追加 |Microsoft Docs'
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
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4a8777dff45eb257a941716306f099c67e3fcda7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "42626089"
---
# <a name="walkthrough-add-feature-event-receivers"></a>チュートリアル: フィーチャー イベント レシーバーを追加します。
  フィーチャー イベント レシーバーは、SharePoint で、次の機能に関連するイベントのいずれかが発生したときに実行する方法です。

-   機能をインストールします。

-   フィーチャーがアクティブにします。

-   フィーチャーが非アクティブ化します。

-   機能が削除されます。

 このチュートリアルでは、SharePoint プロジェクト内のフィーチャーには、イベント レシーバーを追加する方法を示します。 これには、次のタスクを示しています。

-   フィーチャー イベント レシーバーを空のプロジェクトを作成しています。

-   処理、 **FeatureDeactivating**メソッド。

-   SharePoint プロジェクト オブジェクト モデルを使用して、お知らせをお知らせリストに追加します。

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必須コンポーネント
 このチュートリアルを実行するには、次のコンポーネントが必要です。

-   サポート対象エディションの Microsoft Windows および SharePoint。

-   Visual Studio

## <a name="create-a-feature-event-receiver-project"></a>フィーチャー イベント レシーバー プロジェクトを作成します。
 最初に、フィーチャー イベント レシーバーを含めるためのプロジェクトを作成します。

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>フィーチャー イベント レシーバーを含むプロジェクトを作成するには

1.  メニュー バーで、**ファイル** > **新規** > **プロジェクト**を表示する、**新しいプロジェクト** ダイアログ ボックス。

2.  展開、 **SharePoint**のどちらかのノード**Visual c#** または**Visual Basic**を選択し、 **2010**ノード。

3.  **テンプレート**ウィンドウで、選択、 **SharePoint 2010 プロジェクト**テンプレート。

     プロジェクト テンプレートがないために、フィーチャー イベント レシーバーのこのプロジェクトの種類を使用します。

4.  **名**ボックスに、入力**FeatureEvtTest**、選択し、 **OK**を表示するボタン、 **SharePoint カスタマイズ ウィザード**。

5.  **デバッグのサイトとセキュリティのレベルを指定**ページで、新しいカスタム フィールドのアイテムを追加する SharePoint サーバー サイトの URL を入力するか、既定の場所を使用して (http://\<*システム名前*>/)。

6.  **この SharePoint ソリューションの信頼レベルとは何ですか?** セクションで、選択、**ファーム ソリューションとして配置**オプション ボタンをクリックします。

     サンド ボックス ソリューションとファーム ソリューションの詳細については、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)します。

7.  選択、**完了**ボタンをクリックし、Feature1 という機能が表示されることに注意してください、**機能**ノード。

## <a name="add-an-event-receiver-to-the-feature"></a>フィーチャー イベント レシーバーを追加します。
 次に、フィーチャー イベント レシーバーを追加し、機能が非アクティブ化時に実行されるコードを追加します。

#### <a name="to-add-an-event-receiver-to-the-feature"></a>フィーチャー イベント レシーバーを追加するには

1.  機能 ノードのショートカット メニューを開き、選択し、**機能の追加**機能を作成します。

2.  下、**機能**ノード、ショートカット メニューを開き**Feature1**を選び、**イベント レシーバーの追加**フィーチャー イベント レシーバーを追加します。

     これには、Feature1 コード ファイルが追加されます。 この場合、いずれかに名前が*Feature1.EventReceiver.cs*または*Feature1.EventReceiver.vb*プロジェクトの開発言語によって異なります。

3.  プロジェクトが記述されている場合[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]がない場合は、イベント レシーバーの上部にある次のコードを追加します。

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4.  イベント レシーバー クラスには、イベントとして機能するいくつかのコメント アウトされたメソッドが含まれています。 置換、 **FeatureDeactivating**を次のメソッド。

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>フィーチャー イベント レシーバーをテストします。
 次に、テスト対象の機能を非アクティブ化するかどうか、 **FeatureDeactivating**メソッドは、SharePoint のお知らせリストにお知らせを出力します。

#### <a name="to-test-the-feature-event-receiver"></a>フィーチャー イベント レシーバーをテストするには

1.  プロジェクトの値を設定**アクティブな配置構成**プロパティを**アクティブ化しない**します。

     このプロパティを設定して、機能が SharePoint でアクティブ化することを防止、フィーチャー イベント レシーバーをデバッグすることができます。 詳細については、次を参照してください。[デバッグの SharePoint ソリューション](../sharepoint/debugging-sharepoint-solutions.md)します。

2.  選択、 **F5**プロジェクトを実行し、SharePoint に配置するキー。

3.  SharePoint Web ページの上部にあるを開く、**サイトの操作**] メニューの [選び、**サイト設定**します。

4.  下、**サイトの操作**のセクション、**サイト設定**ページで、選択、**サイト機能の管理**リンク。

5.  **機能**ページで、選択、 **Activate**横に、 **FeatureEvtTest Feature1**機能します。

6.  **機能**ページで、選択、**非アクティブ化**横に、 **FeatureEvtTest Feature1**機能を選択し、**この機能を非アクティブ化**機能を非アクティブ化するリンクを確認します。

7.  選択、**ホーム**ボタンをクリックします。

     お知らせが表示されます、**お知らせ**機能が非アクティブ化した後に一覧表示します。

## <a name="see-also"></a>関連項目

- [方法: イベント レシーバーを作成](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)