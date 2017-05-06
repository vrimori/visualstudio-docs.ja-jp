---
title: "チュートリアル: ビジネス データを使用した SharePoint での外部リストの作成"
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
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発]、Web パーツのビジネス データ"
  - "BDC [Visual Studio での SharePoint 開発]、外部リスト"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発]、SharePoint リストのビジネス データ"
  - "BDC [Visual Studio での SharePoint 開発]、SharePoint リストのビジネス データ"
  - "BDC [Visual Studio での SharePoint 開発]、Web パーツのビジネス データ"
  - "BDC [Visual Studio での SharePoint 開発]、エンティティに基づくリスト"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発]、エンティティに基づくリスト"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発]、外部リスト"
ms.assetid: 046cf234-705a-4a6f-91f8-c5c569ae0dd0
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# チュートリアル: ビジネス データを使用した SharePoint での外部リストの作成
  ビジネス データ接続 \(BDC\) サービスを使用すると、バックエンド サーバー アプリケーション、Web サービス、およびデータベースのビジネス データを SharePoint で表示できます。  
  
 このチュートリアルでは、サンプル データベースに含まれる連絡先に関する情報を返すという、BDC サービスのモデルを作成する方法について説明します。  次に、このモデルを使用して SharePoint に外部リストを作成します。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   プロジェクトを作成する。  
  
-   モデルにエンティティを追加する。  
  
-   Finder メソッドを追加する。  
  
-   SpecificFinder メソッドを追加する。  
  
-   プロジェクトをテストする。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Windows と SharePoint。  詳細については、「[SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)」を参照してください。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]、[!INCLUDE[vsUltLong](../sharepoint/includes/vsultlong-md.md)]、または [!INCLUDE[vsPreLong](../sharepoint/includes/vsprelong-md.md)]  
  
-   AdventureWorks サンプル データベースへのアクセス権。  この方法の詳細については、AdventureWorks データベースをインストールする参照します [SQL Server のサンプル データベース](http://go.microsoft.com/fwlink/?LinkID=117483)。  
  
## BDC モデルを含むプロジェクトを作成する  
  
#### BDC モデルを含むプロジェクトを作成するには  
  
1.  Visual Studio のメニュー バーで、**\[ファイル\]**、**\[新規作成\]**、**\[プロジェクト\]** の順にクリックします。  
  
     **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
2.  **\[Visual C\#\]** または **\[Visual Basic\]** で、**\[SharePoint\]** ノードを展開し、**2010** 項目を選択します。  
  
3.  **\[テンプレート\]** のペインで、**\[SharePoint 2010 プロジェクト\]** をクリックします、プロジェクト AdventureWorksTest "という名前を付けて、**\[OK\]** ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  このウィザードで、プロジェクトをデバッグし、ソリューションの信頼レベルを設定するために使用するサイトを指定できます。  
  
4.  信頼レベルを設定するに **\[ファーム ソリューションとして配置する\]** のオプション ボタンを選択します。  
  
5.  **\[完了\]** ボタンをクリックして、既定のローカル SharePoint サイトを作成します。  
  
6.  **\[ソリューション エクスプローラー\]** で SharePoint のプロジェクト ノードをクリックします。  
  
7.  メニュー バーで **\[プロジェクト\]**、**\[新しい項目の追加\]** の順に選択します。  
  
     **\[新しい項目の追加\]** ダイアログ ボックスが表示されます。  
  
8.  **\[テンプレート\]** のペインで、**\[ビジネス データ接続モデル \(ファーム ソリューションのみ\)\]** をクリックします、プロジェクト AdventureWorksContacts "を付けておくと、**\[追加\]** ボタンをクリックします。  
  
## プロジェクトへのデータ アクセス クラスの追加  
  
#### プロジェクトにデータ アクセス クラスを追加するには  
  
1.  メニュー バーで、**\[データベースへの接続\]\[ツール\]** をクリックします。  
  
     **\[接続の追加\]** ダイアログ ボックスが表示されます。  
  
2.  SQL Server AdventureWorks サンプル データベースとの接続を追加します。  
  
     詳細については、「[Add\/Modify Connection \(Microsoft SQL Server\)](http://msdn.microsoft.com/ja-jp/fa400910-26c3-4df7-b9d1-115e688b4ea3)」を参照してください。  
  
3.  **ソリューション エクスプローラー**で、プロジェクト ノードを選択します。  
  
4.  メニュー バーで **\[プロジェクト\]**、**\[新しい項目の追加\]** の順に選択します。  
  
5.  **\[インストールされているテンプレート\]** のペインで、**\[データ\]** ノードを選択します。  
  
6.  **\[テンプレート\]** のペインで、**\[LINQ to SQL クラス\]** をクリックします。  
  
7.  **\[名前\]** ボックスで、AdventureWorks を指定し、**\[追加\]** ボタンをクリックします。  
  
     .dbml ファイルがプロジェクトに追加され、オブジェクト リレーショナル デザイナー \(O\/R デザイナー\) が表示されます。  
  
8.  メニュー バーで、**\[サーバー エクスプローラー\]\[表示\]** をクリックします。  
  
9. **サーバー エクスプローラー**で、AdventureWorks サンプル データベースを示すノードを展開し、**\[テーブル\]** ノードを展開します。  
  
10. O\/R デザイナーに **\[連絡担当者\]** テーブルを追加します。  
  
     エンティティ クラスが作成され、デザイン サーフェイスに表示されます。  このエンティティ クラスには、Contact \(Person\) テーブルの列にマップされるプロパティが含まれています。  
  
## BDC モデルからの既定のエンティティの削除  
 **\[ビジネス データ接続モデル\]** プロジェクトでは、Entity1 という名前の既定のエンティティがモデルに追加されます。  このエンティティを削除します。  後で、新しいエンティティを追加します。  空のモデルから始めることで、チュートリアルの完了までに必要な手順数を減らすことができます。  
  
#### BDC モデルからの既定のエンティティを削除するには  
  
1.  **\[ソリューション エクスプローラー\]** で、**\[BdcModel1\]** ノードを展開し、BdcModel1.bdcm ファイルを開きます。  
  
2.  BDC デザイナーにビジネス データ接続モデル ファイルが開きます。  
  
3.  デザイナーで、**\[Entity1\]** のショートカット メニューを開き、**\[削除\]** をクリックします。  
  
4.  **\[ソリューション エクスプローラー\]** で、Entity1.vb \(Visual Basic の場合\) または Entity1.cs のショートカット メニュー \(C\# の場合\) を開き、**\[削除\]** をクリックします。  
  
5.  Entity1Service.vb \(Visual Basic の場合\) または Entity1Service.cs のショートカット メニュー \(C\# の場合\) を開き、**\[削除\]** をクリックします。  
  
## モデルへのエンティティの追加  
 モデルにエンティティを追加します。  BDC デザイナーに Visual Studio **\[ツールボックス\]** からエンティティを追加する。  
  
#### モデルにエンティティを追加するには  
  
1.  メニュー バーで **\[表示\]**、**\[ツールボックス\]** の順にクリックします。  
  
2.  **\[ツールボックス\]** の **\[BusinessDataConnectivity\]** タブで、BDC デザイナーに **\[エンティティ\]** を追加します。  
  
     新しいエンティティがデザイナーに表示されます。  Visual Studio は EntityService.vb \(Visual Basic の場合\) またはプロジェクトに EntityService.cs \(C\# の場合\) という名前のファイルが追加されます。  
  
3.  メニュー バーで、**\[プロパティ\]**、**\[ウィンドウ\]\[表示\]** をクリックします。  
  
4.  **\[プロパティ\]** ウィンドウで、連絡先の **\[名前\]** プロパティ値を設定します。  
  
5.  デザイナーのエンティティのショートカット メニューを開き、**\[追加\]** をクリックします、**\[識別子\]** をクリックします。  
  
     新しい識別子がエンティティに表示されます。  
  
6.  **プロパティ** ウィンドウで、ContactID の識別子の名前を変更します。  
  
7.  **\[型の名前\]** の一覧で、**\[System.Int32\]** をクリックします。  
  
## SpecificFinder メソッドの追加  
 BDC サービスで特定の連絡先を表示できるようにするには、SpecificFinder メソッドを追加する必要があります。  ユーザーがリストの項目を選択し、次へをクリックすると、BDC サービス呼び出しから SpecificFinder メソッドのリボンのボタンを **\[アイテムの表示\]**。  
  
 **\[BDC メソッドの詳細\]** ウィンドウを使用して、SpecificFinder メソッドを Contact エンティティに追加します。  特定のエンティティを返すには、メソッドにコードを追加します。  
  
#### SpecificFinder メソッドを追加するには  
  
1.  BDC デザイナーで、**\[連絡先\]** エンティティを選択します。  
  
2.  メニュー バーで、**\[その他のウィンドウ\]**、**\[BDC メソッドの詳細\]\[表示\]** をクリックします。  
  
     \[BDC メソッドの詳細\] ウィンドウが表示されます。  
  
3.  **\[メソッドの追加\]** の一覧で、**\[SpecificFinder メソッドの作成\]** をクリックします。  
  
     次の要素がモデルに追加されます。  これらの要素は **\[BDC メソッドの詳細\]** ウィンドウに表示されます。  
  
    -   ReadItem というメソッド。  
  
    -   メソッドの入力パラメーター。  
  
    -   メソッドの戻り値パラメーター。  
  
    -   各パラメーターの型記述子。  
  
    -   メソッドのメソッド インスタンス。  
  
4.  **\[BDC メソッドの詳細\]** ウィンドウで、**\[連絡先\]** 型記述子に表示される開き、**\[編集\]** をクリックしますリストを返します。  
  
     **\[BDC エクスプローラー\]** はモデルの階層ビューを開き、提供します。  
  
5.  **\[プロパティ\]** ウィンドウでリストを **\[TypeName\]** のプロパティの横に開き、**\[現在のプロジェクト\]** タブをクリックし、**\[連絡先\]** のプロパティをクリックします。  
  
6.  **\[BDC エクスプローラー\]** で、**\[連絡先\]** のショートカット メニューを開き、**\[型記述子の追加\]** をクリックします。  
  
     **\[TypeDescriptor1\]** という新しい型記述子が **\[BDC エクスプローラー\]** に表示されます。  
  
7.  **\[プロパティ\]** ウィンドウで、**ContactID**に **\[名前\]** プロパティ値を設定します。  
  
8.  リストを **\[TypeName\]** のプロパティの横に開き、**\[Int32\]** をクリックします。  
  
9. リストを **\[識別子\]** のプロパティの横に開き、**ContactID**を選択します。  
  
10. 手順 6. を繰り返して、次の各フィールドについて型記述子を作成します。  
  
    |名前|型の名前|  
    |--------|----------|  
    |FirstName|System.String|  
    |LastName|System.String|  
    |Phone|System.String|  
    |EmailAddress|System.String|  
    |EmailPromotion|System.Int32|  
    |NameStyle|System.Boolean|  
    |PasswordHash|System.String|  
    |PasswordSalt|System.String|  
  
11. BDC デザイナーで、**\[連絡先\]** エンティティで、**\[ReadItem\]** のメソッドを開きます。  
  
     コード エディターで、Contact のサービス コード ファイルが開きます。  
  
12. `ContactService` クラスで、`ReadItem` メソッドを次のコードに置き換えます。  このコードは次のタスクを実行します。  
  
    -   AdventureWorks データベースの Contacts テーブルのレコードを取得します。  
  
    -   Contact エンティティを BDC サービスに返します。  
  
    > [!NOTE]  
    >  `ServerName` フィールドの値を、使用するサーバーの名前に置き換えます。  
  
     [!code-csharp[SP_BDC#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#3)]  
  
## Finder メソッドの追加  
 BDC サービスで連絡先を一覧表示できるようにするには、Finder メソッドを追加する必要があります。  **\[BDC メソッドの詳細\]** ウィンドウを使用して、Finder メソッドを Contact エンティティに追加します。  エンティティのコレクションを BDC サービスに返すには、メソッドにコードを追加します。  
  
#### Finder メソッドを追加するには  
  
1.  BDC デザイナーで、**\[連絡先\]** エンティティを選択します。  
  
2.  **\[BDC メソッドの詳細\]** ウィンドウで、**\[ReadItem\]** ノードを折りたたんでします。  
  
3.  **\[ReadList\]** のメソッドの **\[メソッドの追加\]** の一覧で、**\[Finder メソッドの作成\]** をクリックします。  
  
     メソッド、戻り値パラメーター、および型記述子が追加されます。  
  
4.  BDC デザイナーで、**\[連絡先\]** エンティティで、**\[ReadList\]** のメソッドを開きます。  
  
     連絡先サービスのコード ファイルがコード エディターで開きます。  
  
5.  `ContactService` クラスで、`ReadList` メソッドを次のコードに置き換えます。  このコードは次のタスクを実行します。  
  
    -   AdventureWorks データベースの Contacts テーブルのデータを取得します。  
  
    -   Contact エンティティの一覧を BDC サービスに返します。  
  
    > [!NOTE]  
    >  `ServerName` フィールドの値を、使用するサーバーの名前に置き換えます。  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## プロジェクトのテスト  
 プロジェクトを実行すると、SharePoint サイトが開き、Visual Studio ではモデルがビジネス データ接続サービスに追加されます。  SharePoint に Contact エンティティを参照する外部リストを作成します。  AdventureWorks データベースに含まれる連絡先のデータが一覧表示されます。  
  
> [!NOTE]  
>  場合によっては、ソリューションをデバッグする前に SharePoint のセキュリティ設定を変更する必要があります。詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
#### プロジェクトをテストするには  
  
1.  **F5** キーを押します。  
  
     SharePoint サイトが開きます。  
  
2.  **\[サイトの操作\]** メニューで、**\[その他のオプション\]** コマンドを選択します。  
  
3.  **\[作成\]** ページで、**\[外部リスト\]** テンプレートを選択し、**\[作成\]** ボタンをクリックします。  
  
4.  カスタム リストに Contacts と名前を付けます。  
  
5.  **\[外部コンテンツ タイプ\]** フィールドの横にある参照ボタンをクリックします。  
  
6.  **\[外部コンテンツ タイプの選択\]** ダイアログ ボックスで、**\[AdventureWorksContacts.BdcModel1.Contact\]** 項目を選択し、**\[作成\]** ボタンをクリックします。  
  
     SharePoint では、AdventureWorks サンプル データベースの連絡先を含む外部リストを作成します。  
  
7.  特定の Finder メソッドをテストするには、一覧から連絡先を選択します。  
  
8.  リボンで、**\[項目\]** タブをクリックし、**\[アイテムの表示\]** コマンドを選択します。  
  
     選択した連絡先の詳細情報がフォームに表示されます。  
  
## 次の手順  
 SharePoint で BDC サービスのモデルを設計する方法の詳細については、次のトピックを参照してください。  
  
-   [方法: Creator メソッドを追加する](../sharepoint/how-to-add-a-creator-method.md).  
  
-   [方法: Updater メソッドを追加する](../sharepoint/how-to-add-an-updater-method.md).  
  
-   [方法: Deleter メソッドを追加する](../sharepoint/how-to-add-a-deleter-method.md).  
  
## 参照  
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [SharePoint へのビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  