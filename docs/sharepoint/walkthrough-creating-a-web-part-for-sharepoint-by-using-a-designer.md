---
title: "チュートリアル: デザイナーを使用した SharePoint の Web パーツの作成 | Microsoft Docs"
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
  - "Web パーツ [Visual Studio での SharePoint 開発], 作成"
  - "Web パーツ [Visual Studio での SharePoint 開発], デザイナー"
  - "Web パーツ [Visual Studio での SharePoint 開発], デザイン"
ms.assetid: 3dd62654-ada2-468f-b7da-eb5704a2ff7a
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# チュートリアル: デザイナーを使用した SharePoint の Web パーツの作成
  SharePoint サイトの Web パーツを作成すれば、ユーザーはブラウザーを使用して、そのサイトを構成するページのコンテンツ、外観、動作を直接変更できます。  このチュートリアルでは、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] に用意されている SharePoint の**視覚的 Web パーツ** プロジェクト テンプレートを使用して、Web パーツを視覚的に作成する方法を説明します。  
  
 ここで作成する Web パーツには、月間カレンダー ビューと、サイトで使用する各カレンダー リストのチェック ボックスが表示されます。  ユーザーがチェック ボックスをオンにすると、それに対応するカレンダー リストが月間カレンダー ビューに追加されます。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   **視覚的 Web パーツ** プロジェクト テンプレートを使用して Web パーツを作成する  
  
-   Visual Studio の Visual Web Developer デザイナーを使用して Web パーツをデザインする  
  
-   Web パーツに配置したコントロールのイベントを処理するコードを追加する  
  
-   SharePoint で Web パーツをテストする  
  
    > [!NOTE]  
    >  このチュートリアルに記載されている Visual Studio ユーザー インターフェイスの一部の要素は、お使いのコンピューターに実際に表示される名前や場所と異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Windows と SharePoint。  「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] 以上  
  
## Web パーツ プロジェクトを作成する  
 まず、**視覚的 Web パーツ** プロジェクト テンプレートを使用して Web パーツ プロジェクトを作成します。  
  
#### 視覚的 Web パーツ プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を、**\[管理者として実行\]** オプションを使用して起動します。  
  
2.  メニュー バーで **\[ファイル\]**、**\[新規\]**、**\[プロジェクト\]** の順にクリックします。  
  
     \[新しいプロジェクト\] ダイアログ ボックスが表示されます。  
  
3.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[Visual C\#\]** または **\[Visual Basic\]** の **\[Office\/SharePoint\]** を展開し、**\[SharePoint ソリューション\]** カテゴリを選択します。  
  
4.  テンプレートの一覧で **\[SharePoint 2013 視覚的 Web パーツ\]** テンプレートを選択し、**\[OK\]** をクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  このウィザードでは、プロジェクトのデバッグ時に使用するサイトやソリューションの信頼レベルを指定できます。  
  
5.  **\[この SharePoint ソリューションの信頼レベル\]** セクションで **\[ファーム ソリューションとして配置する\]** を選択します。  
  
6.  **\[完了\]** ボタンをクリックして、既定のローカル SharePoint サイトを作成します。  
  
## Web パーツをデザインする  
 **ツールボックス**にあるコントロールを Visual Web Developer デザイナーのサーフェイスへ追加して、Web パーツをデザインします。  
  
#### Web パーツのレイアウトをデザインするには  
  
1.  Visual Web Developer デザイナーで、**\[デザイン\]** タブを選択してデザイン ビューに切り替えます。  
  
2.  メニュー バーで **\[表示\]**、**\[ツールボックス\]** の順にクリックします。  
  
3.  **ツールボックス**の **\[標準\]** ノードで **\[CheckBoxList\]** コントロールを選択し、次のいずれかの手順に従います。  
  
    -   **\[CheckBoxList\]** コントロールのショートカット メニューを開き、**\[コピー\]** を選択します。デザイナーで最初の行のショートカット メニューを開き、**\[貼り付け\]** を選択します。  
  
    -   **ツールボックス**から **\[CheckBoxList\]** コントロールをドラッグし、デザイナーの最初の行に接続します。  
  
4.  前の手順を繰り返します。ただし、ここでは、デザイナーの次の行へボタンを移動します。  
  
5.  デザイナーで **\[Button1\]** ボタンを選択します。  
  
6.  メニュー バーで、**\[表示\]**、**\[プロパティ ウィンドウ\]** の順に選択します。  
  
     **\[プロパティ\]** ウィンドウが開きます。  
  
7.  ボタンの **\[テキスト\]** プロパティに「更新」と入力します。  
  
## Web パーツ上のコントロールのイベントを処理する  
 ユーザーがマスター カレンダー ビューにカレンダーを追加できるようにするコードを追加します。  
  
#### Web パーツ上のコントロールのイベントを処理するには  
  
1.  次のいずれかの操作を実行します。  
  
    -   デザイナーで、**\[更新\]** ボタンをダブルクリックします。  
  
    -   **\[更新\]** ボタンの **\[プロパティ\]** ウィンドウで、**\[Events\]** ボタンを選択します。  **\[Click\]** プロパティに「**Button1\_Click**」と入力し、Enter キーを押します。  
  
     ユーザー コントロール コード ファイルがコード エディターで開き、`Button1_Click` イベント ハンドラーが表示されます。  後で、このイベント ハンドラーにコードを追加します。  
  
2.  ユーザー コントロール コード ファイルの先頭に次のステートメントを追加します。  
  
     [!code-csharp[SP_VisualWebPart#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]
     [!code-vb[SP_VisualWebPart#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]  
  
3.  `VisualWebPart1` クラスに次のコード行を追加します。  このコードでは、月間カレンダー ビュー コントロールを宣言します。  
  
     [!code-csharp[SP_VisualWebPart#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]
     [!code-vb[SP_VisualWebPart#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]  
  
4.  `VisualWebPart1` クラスの `Page_Load` メソッドを次のコードに置き換えます。  このコードは次のタスクを実行します。  
  
    -   月間カレンダー ビューをユーザー コントロールに追加します。  
  
    -   サイト上の各カレンダー リストにチェック ボックスを追加します。  
  
    -   カレンダー ビューに表示される項目の種類ごとにテンプレートを指定します。  
  
     [!code-csharp[SP_VisualWebPart#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]
     [!code-vb[SP_VisualWebPart#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]  
  
5.  `VisualWebPart1` クラスの `Button1_Click` メソッドを次のコードに置き換えます。  このコードでは、選択したカレンダーの項目をマスター カレンダー ビューに追加します。  
  
     [!code-csharp[SP_VisualWebPart#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]
     [!code-vb[SP_VisualWebPart#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]  
  
## Web パーツをテストする  
 プロジェクトを実行すると、SharePoint サイトが開きます。  SharePoint の Web パーツ ギャラリーに Web パーツが自動的に追加されます。  このプロジェクトをテストするには、次のタスクを実行します。  
  
-   2 つのカレンダー リストそれぞれにイベントを追加します。  
  
-   Web パーツを Web パーツ ページに追加します。  
  
-   月間カレンダー ビューに含めるリストを指定します。  
  
#### サイト上のカレンダー リストにイベントを追加するには  
  
1.  Visual Studio で F5 キーを押します。  
  
     SharePoint サイトが開き、ページ上に [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] クイック起動バーが表示されます。  
  
2.  クイック起動バーの **\[リスト\]** にある **\[カレンダー\]** リンクを選択します。  
  
     **\[カレンダー\]** ページが表示されます。  
  
     クイック起動バーにカレンダー リンクが表示されない場合は、**\[サイト コンテンツ\]** リンクを選択します。  \[サイト コンテンツ\] ページに **\[カレンダー\]** 項目が表示されない場合は、カレンダーを作成します。  
  
3.  カレンダー ページで、日を選択し、選択した日の **\[追加\]** リンクを選択してイベントを追加します。  
  
4.  既定のカレンダーの **\[タイトル\]** ボックスに「イベント」と入力し、**\[保存\]** ボタンをクリックします。  
  
5.  **\[サイト コンテンツ\]** リンクを選択し、**\[アプリの追加\]** タイルを選択します。  
  
6.  **\[作成\]** ページで、種類として **\[カレンダー\]** を選択し、カレンダーの名前を入力します。**\[作成\]** ボタンをクリックします。  
  
7.  新しいカレンダーにイベントを追加し、カスタム カレンダーのイベントに「イベント」という名前を付けます。**\[保存\]** ボタンをクリックします。  
  
#### Web パーツを Web パーツ ページに追加するには  
  
1.  **\[サイト コンテンツ\]** ページで **\[サイトのページ\]** フォルダーを開きます。  
  
2.  リボンで **\[ファイル\]** タブを選択します。**\[新しいドキュメント\]** メニューを開き、**\[Web パーツ ページ\]** を選択します。  
  
3.  **\[新しい Web パーツ ページ\]**で、ページに「**SampleWebPartPage.aspx**」と名前を付け、**\[作成\]** ボタンをクリックします。  
  
     Web パーツ ページが表示されます。  
  
4.  Web パーツ ページの上部にある **\[挿入\]** タブをクリックし、**\[Web パーツ\]** ボタンをクリックします。  
  
5.  **\[カスタム\]** フォルダーを選択します。さらに **\[VisualWebPart1\]** Web パーツを選択し、**\[追加\]** ボタンをクリックします。  
  
     ページに Web パーツが表示されます。  Web パーツに次のコントロールが表示されます。  
  
    -   月間カレンダー ビュー  
  
    -   **\[更新\]** ボタン  
  
    -   **\[カレンダー\]** チェック ボックス  
  
    -   **\[カスタム カレンダー\]** チェック ボックス  
  
#### 月間カレンダー ビューに追加するリストを指定するには  
  
1.  Web パーツで、月間カレンダー ビューに追加するカレンダーを選択し、**\[更新\]** ボタンをクリックします。  
  
     指定したすべてのカレンダーのイベントが月間カレンダー ビューに表示されます。  
  
## 参照  
 [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [方法: SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [方法: デザイナーを使用して SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [チュートリアル: SharePoint の Web パーツを作成する](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)  
  
  