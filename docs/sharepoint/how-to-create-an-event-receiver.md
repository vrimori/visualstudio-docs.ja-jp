---
title: "方法: イベント レシーバーを作成する"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.EventReceiver"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "イベント レシーバー [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, イベント レシーバー"
ms.assetid: 6f90cb48-eb8f-43c2-a3f7-ed4ce81aedf2
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 方法: イベント レシーバーを作成する
  *イベント レシーバー*を作成して、ユーザーがリストまたはリスト項目などの SharePoint アイテムと対話するときに応答できます。  たとえば、イベント レシーバーのコードは、ユーザーが変更カレンダー トリガーするか、連絡先リストから名前を削除します。  このトピックに従ってリスト インスタンスにイベント レシーバーを追加する方法について学習できます。  
  
 これらの手順を完了するには、Windows と SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] とサポートされているエディションをインストールしておく必要があります。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  この例では、SharePoint プロジェクトを必要とするため、[チュートリアル: SharePoint のサイト列、コンテンツ タイプ、およびリストの作成](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)"の手順を終了している必要があります。  
  
## イベント レシーバーの追加  
 ユーザーが [チュートリアル: SharePoint のサイト列、コンテンツ タイプ、およびリストの作成](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) で作成したプロジェクトは、カスタム サイト内の列、カスタム リストおよびコンテンツ タイプが含まれています。  次の手順では、リストなどの SharePoint アイテムで発生するイベントを処理する方法を指定するには、リスト インスタンスに単純なイベント ハンドラー \(イベント レシーバー\) を追加することによって、このプロジェクトを展開します。  
  
#### リスト インスタンスにイベント レシーバーを追加するには  
  
1.  「[チュートリアル: SharePoint のサイト列、コンテンツ タイプ、およびリストの作成](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)」で作成したプロジェクトを開きます。  
  
2.  **\[ソリューション エクスプローラー\]** で、**\[クリニック\]** という名前の SharePoint プロジェクト ノードをクリックします。  
  
3.  メニュー バーで **\[プロジェクト\]**、**\[新しい項目の追加\]** の順に選択します。  
  
4.  **\[Visual C\#\]** または **\[Visual Basic\]** で、**\[SharePoint\]** ノードを展開し、**2010** 項目を選択します。  
  
5.  **\[テンプレート\]** のペインで、**\[イベント レシーバー\]** をクリックします、" TestEventReceiver1 "という名前を付けて、**\[OK\]** ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
6.  **\[使用するイベント レシーバーの種類\]** の一覧で、**\[リスト項目イベント\]** をクリックします。  
  
7.  **\[イベント ソースとなる項目\]** の一覧で、**\[患者 \(Clinic\\Patients\) \]** をクリックします。  
  
8.  **\[次のイベントを処理\]** の一覧で、チェック ボックスを **\[項目が追加されました\]** の横にし、**\[完了\]** ボタンをクリックします。  
  
     新しいイベント レシーバーのコード ファイルが `ItemAdded`という名前のメソッドが一つ含まれています。  次の手順では、連絡先が Scott Brown とともに指定されるように、このメソッドにコードを追加します。  
  
9. `ItemAdded` の既存のメソッドを次のコードで置き換えて、F5 キーを押してする:  
  
     [!code-csharp[SP_EventReceiver#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_eventreceiver/CS/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_eventreceiver/VB/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     コードが実行され、SharePoint サイトが Web ブラウザーに表示されます。  
  
10. クイック起動バーに、**\[患者\]** リンクを選択し、**\[新しいアイテムの追加\]** リンクをクリックします。  
  
     新しい項目の参加アプリケーションの記述が開きます。  
  
11. フィールドにデータを入力し、**\[保存\]** ボタンをクリックします。  
  
     **\[保存\]** ボタンを選択したら、名前 Scott Brown に自動的に **\[Patient Name\]** 列の更新。  
  
## 参照  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  