---
title: "チュートリアル: SharePoint の Web パーツを作成する | Microsoft Docs"
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
  - "Web パーツ [Visual Studio での SharePoint 開発], デザイン"
  - "Web パーツ [Visual Studio での SharePoint 開発], 開発"
ms.assetid: 51fb5bdd-b99c-4716-83bc-e66a5da15169
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# チュートリアル: SharePoint の Web パーツを作成する
  Web パーツを使用すると、ブラウザーから SharePoint サイト ページのコンテンツ、外観、および動作を直接変更できます。  このチュートリアルでは、Visual Studio 2010 の **Web パーツ**項目テンプレートを使用して、Web パーツを作成する方法について説明します。  
  
 この Web パーツのデータ グリッドには従業員が表示されます。  従業員データを格納するファイルの場所を指定します。  また、マネージャーである従業員のみが一覧に表示されるように、データ グリッドにフィルターをかけることもできます。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   Visual Studio **Web パーツ**項目テンプレートを使用して Web パーツを作成する。  
  
-   Web パーツのユーザーが設定できるプロパティを作成する。  このプロパティでは、従業員データ ファイルの場所を指定します。  
  
-   コントロールを Web パーツ コントロール コレクションに追加することで Web パーツにコンテンツをレンダリングする。  
  
-   レンダリングされた Web パーツの動詞メニューに表示される、*動詞*という新しいメニュー項目を作成する。  動詞を使用すると、Web パーツに表示されるデータを変更できます。  
  
-   SharePoint の Web パーツをテストする。  
  
    > [!NOTE]  
    >  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Microsoft Windows および SharePoint。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)] または Visual Studio アプリケーション ライフサイクル管理 \(ALM\) のエディション  
  
## 空の SharePoint プロジェクトの作成  
 まず、空の SharePoint プロジェクトを作成します。  後で、**Web パーツ**項目テンプレートを使用してプロジェクトに Web パーツを追加します。  
  
#### 空の SharePoint プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を、**\[管理者として実行\]** オプションを使用して起動します。  
  
2.  メニュー バーで **\[ファイル\]**、**\[新規\]**、**\[プロジェクト\]** の順にクリックします。  
  
3.  **\[新しいプロジェクト\]** ダイアログ ボックスで、使用する言語の **\[SharePoint\]** ノードを展開して、**\[2010\]** ノードを選択します。  
  
4.  **\[テンプレート\]** ペインで、**\[SharePoint 2010 プロジェクト\]** を選択し、**\[OK\]** をクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  このウィザードを使用すると、プロジェクトのデバッグに使用するサイトや、ソリューションの信頼レベルを選択できます。  
  
5.  **\[ファーム ソリューションとして配置する\]** をクリックします。ローカル SharePoint サイトの構成は既定値のままで、**\[完了\]** をクリックします。  
  
## Web パーツのプロジェクトへの追加  
 プロジェクトに **Web パーツ**項目を追加します。  **Web パーツ**項目によって Web パーツ コード ファイルが追加されます。  後で、Web パーツ コード ファイルにコードを追加して、Web パーツのコンテンツをレンダリングします。  
  
#### プロジェクトに Web パーツを追加するには  
  
1.  メニュー バーで **\[プロジェクト\]**、**\[新しい項目の追加\]** の順に選択します。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスの **\[インストールされたテンプレート\]** ペインで、**\[SharePoint\]** ノードを展開し、**\[2010\]** ノードを選択します。  
  
3.  SharePoint テンプレートの一覧で **\[Web パーツ\]** テンプレートを選択し、**\[追加\]** をクリックします。  
  
     **ソリューション エクスプローラー**に **Web パーツ**項目が表示されます。  
  
## Web パーツのコンテンツのレンダリング  
 Web パーツに表示するコントロールを指定するには、Web パーツ クラスのコントロール コレクションにコントロールを追加します。  
  
#### Web パーツのコンテンツをレンダリングするには  
  
1.  **ソリューション エクスプローラー**で、WebPart1.vb \(Visual Basic の場合\) または WebPart1.cs \(C\# の場合\) を開きます。  
  
     コード エディターで Web パーツ コード ファイルが開きます。  
  
2.  Web パーツ コード ファイルの先頭に次のステートメントを追加します。  
  
     [!code-csharp[SP_WebPart#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#1)]  
  
3.  `WebPart1` クラスに次のコードを追加します。  このコードは、次のフィールドを宣言します。  
  
    -   Web パーツに従業員を表示するデータ グリッド。  
  
    -   データ グリッドのフィルターに使用するコントロール上に表示するテキスト。  
  
    -   データ グリッドでデータを表示できない場合、エラーを表示するラベル。  
  
    -   従業員データ ファイルのパスを含む文字列。  
  
     [!code-csharp[SP_WebPart#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#2)]  
  
4.  `WebPart1` クラスに次のコードを追加します。  このコードで、`DataFilePath` というカスタム プロパティが Web パーツに追加されます。  カスタム プロパティとは、ユーザーが SharePoint で設定できるプロパティです。  このプロパティでは、データ グリッドの設定に使用される XML データ ファイルの場所を取得および設定します。  
  
     [!code-csharp[SP_WebPart#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#3)]  
  
5.  `CreateChildControls` メソッドを次のコードに置き換えます。  このコードは次のタスクを実行します。  
  
    -   前の手順で宣言したデータ グリッドとラベルを追加します。  
  
    -   従業員データを格納する XML ファイルにデータ グリッドをバインドします。  
  
     [!code-csharp[SP_WebPart#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#4)]  
  
6.  `WebPart1` クラスに次のメソッドを追加します。  このコードは次のタスクを実行します。  
  
    -   レンダリングされた Web パーツの Web パーツ動詞メニューに表示する動詞を作成します。  
  
    -   動詞メニューの動詞を選択すると発生するイベントを処理します。  このコードでは、データ グリッドに表示される従業員一覧にフィルターをかけます。  
  
     [!code-csharp[SP_WebPart#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_webpart/cs/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_webpart/vb/webpart1/webpart1.vb#5)]  
  
## Web パーツのテスト  
 プロジェクトを実行すると、SharePoint サイトが開きます。  Web パーツは SharePoint の Web パーツ ギャラリーに自動的に追加されます。  Web パーツは任意の Web パーツ ページに追加できます。  
  
#### Web パーツをテストするには  
  
1.  次の XML をメモ帳ファイルに貼り付けます。  この XML ファイルには、Web パーツに表示されるサンプル データが含まれます。  
  
    ```  
  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
       <employee>  
           <name>David Hamilton</name>  
           <hireDate>2001-05-11</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
       <employee>  
           <name>Karina Leal</name>  
           <hireDate>1999-04-01</hireDate>  
           <title>Manager</title>  
       </employee>  
       <employee>  
           <name>Nancy Davolio</name>  
           <hireDate>1992-05-01</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
       <employee>  
           <name>Steven Buchanan</name>  
           <hireDate>1955-03-04</hireDate>  
           <title>Manager</title>  
       </employee>  
       <employee>  
           <name>Suyama Michael</name>  
           <hireDate>1963-07-02</hireDate>  
           <title>Sales Associate</title>  
       </employee>  
    </employees>  
    ```  
  
2.  メモ帳のメニュー バーで、**\[ファイル\]**、**\[上書き保存\]** の順にクリックします。  
  
3.  **\[名前を付けて保存\]** ダイアログ ボックスで、**\[ファイルの種類\]** ボックスの一覧から **\[すべてのファイル\]** を選択します。  
  
4.  **\[ファイル名\]** ボックスに「data.xml」と入力します。  
  
5.  **\[フォルダーの参照\]** ボタンを使用してフォルダーを選択し、**\[保存\]** をクリックします。  
  
6.  Visual Studio で F5 キーを押します。  
  
     SharePoint サイトが開きます。  
  
7.  **\[サイトの操作\]** メニューの **\[その他のオプション\]** をクリックします。  
  
8.  **\[作成\]** ページで、種類として **\[Web パーツ ページ\]** を選択し、**\[作成\]** をクリックします。  
  
9. **\[新しい Web パーツ ページ\]** ページで、ページに「**SampleWebPartPage.aspx**」と名前を付け、**\[作成\]** をクリックします。  
  
     \[Web パーツ\] ページが表示されます。  
  
10. \[Web パーツ\] ページ上のゾーンを選択します。  
  
11. ページの上部にある **\[挿入\]** タブをクリックし、**\[Web パーツ\]** をクリックします。  
  
12. **\[カテゴリ\]** ペインで、**\[カスタム\]** フォルダーを選択し、**\[WebPart1\]** Web パーツを選択して **\[追加\]** をクリックします。  
  
     ページに Web パーツが表示されます。  
  
## カスタム プロパティのテスト  
 Web パーツに表示するデータ グリッドを設定するには、各従業員に関するデータが格納された XML ファイルのパスを指定します。  
  
#### カスタム プロパティをテストするには  
  
1.  Web パーツの右側に表示される矢印をクリックし、表示されるメニューで **\[Web パーツの編集\]** を選択します。  
  
     Web パーツのプロパティを含むペインがページの右側に表示されます。  
  
2.  ペインの **\[その他\]** ノードを展開し、上記の手順で作成した XML ファイルのパスを入力して **\[適用\]** をクリックし、**\[OK\]** をクリックします。  
  
     Web パーツに従業員一覧が表示されることを確認します。  
  
## Web パーツの動詞のテスト  
 Web パーツ動詞メニューに表示される項目をクリックすると、マネージャーではない従業員の表示と非表示が切り替わります。  
  
#### Web パーツの動詞をテストするには  
  
1.  Web パーツの右側に表示される矢印をクリックし、表示されるメニューで **\[マネージャーのみを表示\]** を選択します。  
  
     Web パーツにマネージャーである従業員のみが表示されます。  
  
2.  矢印をもう一度クリックし、表示されるメニューで **\[すべての従業員を表示\]** をクリックします。  
  
     Web パーツにすべての従業員が表示されます。  
  
## 参照  
 [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [方法: SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [方法: デザイナーを使用して SharePoint Web パーツを作成する](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [チュートリアル: デザイナーを使用した SharePoint の Web パーツの作成](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  