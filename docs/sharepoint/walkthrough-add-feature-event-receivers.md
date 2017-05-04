---
title: "チュートリアル: フィーチャーのイベント レシーバーの追加 | Microsoft Docs"
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
  - "Visual Studio での SharePoint 開発, 高度なパッケージ化ツール"
  - "Visual Studio での SharePoint 開発, イベント レシーバー"
  - "Visual Studio での SharePoint 開発, フィーチャー イベント レシーバー"
ms.assetid: fbd44c33-2c27-4d57-abca-21cddc16fbc3
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# チュートリアル: フィーチャーのイベント レシーバーの追加
  フィーチャーのイベント レシーバーは、次のいずれかのフィーチャー関連のイベントが SharePoint 内で発生した場合に実行されるメソッドです。  
  
-   フィーチャーがインストールされた。  
  
-   フィーチャーがアクティブ化された。  
  
-   フィーチャーが非アクティブ化された。  
  
-   フィーチャーが削除された。  
  
 このチュートリアルでは、SharePoint プロジェクト内のフィーチャーにイベント レシーバーを追加する方法について説明します。  ここでは、次のタスクについて説明します。  
  
-   フィーチャーのイベント レシーバーを備えた空のプロジェクトを作成する。  
  
-   **FeatureDeactivating** メソッドを処理する。  
  
-   お知らせリストに対し、SharePoint プロジェクトのオブジェクト モデルを使用してお知らせを追加する。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   Visual Studio  
  
## フィーチャーのイベント レシーバー プロジェクトの作成  
 まず、フィーチャーのイベント レシーバーを含んだプロジェクトを作成します。  
  
#### フィーチャーのイベント レシーバーを備えたプロジェクトを作成するには  
  
1.  メニュー バーで、**\[新しいプロジェクト\]** ダイアログ ボックスを表示するには、**\[新規作成\]**、**\[プロジェクト\]\[ファイル\]** をクリックします。  
  
2.  **\[SharePoint\]** ノードを **\[Visual C\#\]** または **\[Visual Basic\]** で展開し、**2010** ノードを選択します。  
  
3.  **\[テンプレート\]** のペインで、**\[SharePoint 2010 プロジェクト\]** テンプレートを選択します。  
  
     これらのプロジェクト テンプレートがないため、フィーチャーのイベント レシーバーには、このプロジェクトの種類を使用します。  
  
4.  **\[名前\]** ボックスで、FeatureEvtTest "と入力し、**\[SharePoint カスタマイズ ウィザード\]** を表示するに **\[OK\]** ボタンをクリックします。  
  
5.  **\[デバッグのサイトとセキュリティ レベルの指定\]** ページで、新しいカスタム フィールド項目の追加先と入力するか、既定の場所 \(http:\/\/\<*system name*\>\/\) を使用して、SharePoint サーバー サイトの URL を指定します。  
  
6.  **\[この SharePoint ソリューションの信頼レベル\]** セクションで **\[ファーム ソリューションとして配置する\]** を選択します。  
  
     サンドボックス ソリューションとファーム ソリューションの違いの詳細については、「[サンドボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)」を参照してください。  
  
7.  **\[完了\]** をクリックし、Feature1 という名前のフィーチャーが **\[フィーチャー\]** ノードの下に表示されることを確認します。  
  
## フィーチャーへのイベント レシーバーの追加  
 今度は、フィーチャーにイベント レシーバーを追加し、フィーチャーが非アクティブ化されたときに実行されるコードを追加します。  
  
#### フィーチャーにイベント レシーバーを追加するには  
  
1.  フィーチャー ノードのショートカット メニューを開き、機能を作成するに **\[フィーチャーの追加\(F\)\]** をクリックします。  
  
2.  **\[フィーチャー\]** ノードで、**\[Feature1\]** のショートカット メニューを開き、フィーチャーにイベント レシーバーを追加するに **\[イベント レシーバーの追加\(E\)\]** をクリックします。  
  
     これで、Feature1 にコード ファイルが追加されます。  このファイルには、プロジェクトの開発言語に応じて、Feature1.EventReceiver.cs または Feature1.EventReceiver.vb という名前が付きます。  
  
3.  プロジェクトが [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]written に、既に存在しないイベント レシーバーの先頭に次のコードを追加する:  
  
     [!code-csharp[SP_FeatureEvt#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  イベント レシーバー クラスはイベントとして機能する複数のコメントの付いたメソッドが含まれています。  **FeatureDeactivating** メソッドを次の内容で置き換えます。  
  
     [!code-csharp[SP_FeatureEvt#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#2)]
     [!code-vb[SP_FeatureEvt#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_featureevt/vb/features/feature1/feature1.eventreceiver.vb#2)]  
  
## フィーチャーのイベント レシーバーのテスト  
 次に、**FeatureDeactivating** メソッドによる SharePoint のお知らせリストへの出力がうまく作動するかどうかを、実際にフィーチャーを非アクティブ化してテストします。  
  
#### フィーチャーのイベント レシーバーをテストするには  
  
1.  **\[アクティブ化なし\]** にプロジェクトの **\[アクティブな配置構成\]** のプロパティの値を設定します。  
  
     このプロパティを設定することによって、あえてフィーチャーが SharePoint でアクティブ化されないようにし、フィーチャーのイベント レシーバーをデバッグします。  詳細については、「[SharePoint ソリューションのデバッグ](../sharepoint/debugging-sharepoint-solutions.md)」を参照してください。  
  
2.  プロジェクトを実行し、SharePoint に配置するに **\[F5\]** キーを押します。  
  
3.  SharePoint Web ページの一番上にある **\[サイトの操作\]** メニューを開き、**\[サイトの設定\]** をクリックします。  
  
4.  **\[サイトの設定\]** ページの **\[サイトの操作\]** セクションで、**\[サイト機能の管理\]** リンクをクリックします。  
  
5.  **\[フィーチャー\]** ページで、**\[FeatureEvtTest Feature1\]** フィーチャーの横に **\[ライセンス認証\]** ボタンをクリックします。  
  
6.  **\[フィーチャー\]** ページで、**\[非アクティブ化\]** ボタンを **\[FeatureEvtTest Feature1\]** 機能の横に選択し、フィーチャーを非アクティブにする **\[この機能を非アクティブ化\]** の確認のリンクをクリックします。  
  
7.  **\[ホーム\]** ボタンをクリックします。  
  
     フィーチャーが非アクティブ化されると、**お知らせ** リストにお知らせが表示されます。  
  
## 参照  
 [方法: イベント レシーバーを作成する](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  