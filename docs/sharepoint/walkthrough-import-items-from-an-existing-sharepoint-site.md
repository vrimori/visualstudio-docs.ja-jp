---
title: "チュートリアル: 既存の SharePoint サイトからのアイテムのインポート"
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
  - "インポート (項目を) [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, インポート (項目を)"
ms.assetid: faac3309-88d7-4fb2-8392-feda07fc00e5
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# チュートリアル: 既存の SharePoint サイトからのアイテムのインポート
  このチュートリアルでは、既存の SharePoint サイトから [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクトに項目をインポートする方法について説明します。  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   カスタム サイト列 \(*フィールド*とも呼ばれます\) を追加して SharePoint をカスタマイズする。  
  
-   SharePoint サイトを .wsp ファイルにエクスポートする。  
  
-   .wsp のインポート プロジェクトを使用して、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint に .wsp ファイルをインポートする。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] および SharePoint。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   Visual Studio  
  
## SharePoint サイトのカスタマイズ  
 この例では、SharePoint サブサイトの作成とカスタマイズを行います。新しいサイト内の列を追加し、後で使用するためのサブサイトを別途作成します。  その後、1 つ目のサブサイトを .wsp ファイルにエクスポートした後、.wsp インポート プロジェクトを使用して、カスタム サイト内の列を 2 つ目のサブサイトにインポートします。  
  
#### SharePoint サイトの作成とカスタマイズを行うには  
  
1.  http:\/\/*system name*\/SitePages\/Home.aspx などの Web ブラウザーで SharePoint サイトを開きます。  
  
2.  **\[サイトの操作\]** メニューを開き、**\[新しいサイト\]** をクリックしますして、メインの SharePoint サイトに対してサブサイトを作成します。  
  
3.  サイトの **\[作成\]** ダイアログ ボックスで、**\[空のサイト\]** の種類を選択します。  
  
4.  **\[タイトル\]** ボックスで、Site Column Test 1;を入力します。**\[URL 名\]** ボックスで、columntest1 "と入力します。; 既定値で他の設定をそのまま使用します; と **\[作成\]** ボタンをクリックします。  
  
5.  サイトが作成されたら、メイン サイト、http:\/\/*system name*\/SitePages\/Home.aspx がブラウザーに移動します。  
  
6.  さらに、**\[サイトの操作\]** メニューを開き、" **\[新しいサイト\]** をクリックします、**\[空のサイト\]** の種類を選択して、メインの SharePoint サイトに対して空のサブサイトを作成します。  
  
7.  **\[タイトル\]** ボックスで、Site Column Test 2;を入力します。**\[URL 名\]** ボックスで、columntest2;を入力します。既定値で他の設定をそのまま使用します; と **\[作成\]** ボタンをクリックします。  
  
8.  一つ目のサブサイト \(http:\/\/*SystemName*\/columntest1\/default.aspx に移動します。  
  
9. **\[サイトの操作\]** メニューで、サイトの設定ページを表示するに **\[サイトの設定\]** をクリックします。  
  
10. **\[ギャラリー\]** セクションで、**\[サイト列\]** リンクをクリックします。  
  
11. **\[サイト内の列ギャラリー\]** ページの上部に、**\[作成\]** ボタンをクリックします。  
  
12. **\[列名\]** ボックスで、Test Column "と入力し、他の既定値を保持し、次へ **\[OK\]** ボタンをクリックします。  
  
13. **\[Test Column\]** の列は Site Column ギャラリーからカスタム列見出しの下に表示されます。  
  
## SharePoint サイトのエクスポート  
 次に、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint プロジェクトにインポートする SharePoint アイテムや SharePoint 要素が含まれた SharePoint セットアップ \(.wsp\) ファイルを入手します。  まだ .wsp ファイルが手元にない場合は、既存の SharePoint サイトから作成する必要があります。  この例では、既定の SharePoint サイトを .wsp ファイルにエクスポートします。  
  
> [!IMPORTANT]  
>  次の手順を実行する途中でランタイム エラーが発生する場合は、SharePoint サイトへのアクセス権があるシステム上で実行してください。  
  
#### 既存の SharePoint サイトをエクスポートするには  
  
1.  SharePoint サイトで、サイトの設定ページを表示するに **\[サイトの操作\]** タブで **\[サイトの設定\]** をクリックします。  
  
2.  サイトの設定 **\[サイトの操作\]** セクションで **\[テンプレートとしてサイトを保存\]** リンクのページングを選択します。  
  
3.  **\[ファイル名\]** ボックスに「ExampleSite」と入力し、**\[テンプレート名\]** ボックスに「Example Site」と入力します。  
  
4.  この例では、**\[コンテンツを含む\]** チェック ボックスをオフのままにします。  
  
     このボックスをオンにした場合、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によってすべてのリストおよびドキュメント ライブラリに加えて、その内容が .wsp ファイルに保存されます。  場合によっては便利な機能ですが、この例では必要ありません。  
  
5.  操作が正常に完了したら、.wsp ファイルを表示するに **\[ソリューション ギャラリー\]** リンクをクリックします。  
  
     ソリューション ギャラリー ページを後で確認するには、**\[サイトの操作\]** メニューを開き、**\[サイトの設定\]** をクリックします、**\[サイト コレクションの管理\]** セクションの **\[トップ レベルのサイト設定に移動\]** リンクを選択し、**\[ギャラリー\]** セクションの **\[ソリューション\]** リンクをクリックします。  
  
6.  ソリューション ギャラリーで、**\[ExampleSite\]** リンクをクリックします。  
  
7.  **\[ファイルのダウンロード\]** ダイアログ ボックスでは、ダウンロード フォルダーのローカル ファイル システムでは、既定で格納する **\[保存\]** ボタンをクリックします。  
  
## .wsp ファイルのインポート  
 再利用する項目 \(カスタム サイト内の Test Column 列\) を含んだ .wsp ファイルが用意できたので、これをインポートして .wsp ファイルにアクセスします。  
  
#### .wsp ファイルをインポートするには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]のメニュー バーで、**\[新しいプロジェクト\]** ダイアログ ボックスを表示するには、**\[新規作成\]**、**\[プロジェクト\]\[ファイル\]** をクリックします。  Visual Basic 開発設定を選択し、メニュー バーで使用する IDE が設定されている場合、**\[新しいプロジェクト\]\[ファイル\]** をクリックします。  
  
2.  **\[SharePoint\]** ノードを **\[Visual C\#\]** または **\[Visual Basic\]** で展開し、**2010** ノードを選択します。  
  
3.  **\[テンプレート\]** ペインの **\[SharePoint 2010 ソリューション パッケージのインポート\]** のテンプレートを選択して、WspImportProject1 としてプロジェクトの名前をそのままにし、次へ **\[OK\]** ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
4.  **\[デバッグのサイトとセキュリティ レベルの指定\]** ページで、先ほど作成した二つ目の SharePoint サブサイト 2 の [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] を入力します。  そのサブサイトに、新しいカスタム フィールド項目、http:\/\/*system name*\/columntest2 を追加します。  
  
5.  **\[この SharePoint ソリューションの信頼レベル\]** セクションの選択は **\[サンドボックス ソリューションとして配置する\]** のままにします。  
  
6.  **\[新しいプロジェクト ソースの指定\]** ページで、先ほど .wsp ファイルを保存し、**\[次へ\]** ボタンを選択したシステム上の場所に移動します。  
  
    > [!NOTE]  
    >  このページの **\[完了\]** ボタンを選択すると、.wsp ファイルで使用できるすべての項目がインポートされます。  
  
7.  **\[インポートする項目の選択\]** ボックスのすべてをリストのチェック ボックスを **\[Test Column\]** を除き、オフに **\[完了\]** ボタンをクリックします。  
  
     リストに多くの項目が含まれているため、リスト内のすべての項目を選択して Ctrl \+ A キーを選択し、すべてのチェック ボックスをオフにして Space キーのキーを選択し、**\[Test Column\]** 項目の横のチェック ボックスを選択します。  
  
     インポート操作が完了すると、"**フィールド**" という名前のフォルダーを含んだ **WspImportProject1** という名前の新しいプロジェクトが作成されます。  このフォルダーには、カスタム サイト内の列 **Test Column** と、その定義ファイル Elements.xml が格納されます。  
  
## プロジェクトの配置  
 最後に、先ほど作成した 2 つ目の SharePoint サブサイトに **WspImportProject1** を配置して、カスタム サイト内の列を表示します。  
  
#### プロジェクトを配置するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で、.wsp のインポート プロジェクトを配置して実行するには、F5 キーを押します。  
  
2.  SharePoint サイトで、**\[サイトの操作\]** メニューを開き、サイトの設定ページを表示するに **\[サイトの設定\]** をクリックします。  
  
3.  **\[ギャラリー\]** セクションで、**\[サイト列\]** リンクをクリックします。  
  
4.  下へスクロールして **\[Custom Columns\]** セクションを表示します。  
  
     1 つ目の SharePoint サイトからインポートしたカスタム サイト内の列が一覧に表示されます。  
  
## 参照  
 [既存の SharePoint サイトからのアイテムのインポート](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  