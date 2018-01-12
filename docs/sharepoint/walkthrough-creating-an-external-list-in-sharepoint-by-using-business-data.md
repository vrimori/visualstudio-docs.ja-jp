---
title: "チュートリアル: sharepoint ビジネス データを使用して外部リストを作成する |Microsoft ドキュメント"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c0954665e8b088f969d59bdad0a2ef1207c95c8f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data"></a>チュートリアル: ビジネス データを使用した SharePoint での外部リストの作成
  ビジネス データ接続 (BDC) サービスは、バック エンド サーバー アプリケーション、Web サービス、およびデータベースのビジネス データを表示するように SharePoint を利用します。  
  
 このチュートリアルでは、サンプル データベース内の連絡先に関する情報を返すという、BDC サービスのモデルを作成する方法を示します。 このモデルを使用して SharePoint での外部リストを作成します。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   プロジェクトを作成します。  
  
-   モデルにエンティティを追加します。  
  
-   Finder メソッドを追加します。  
  
-   Specificfinder メソッドを追加します。  
  
-   プロジェクトをテストします。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   サポート対象エディションの Windows と SharePoint 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]、[!INCLUDE[vsUltLong](../sharepoint/includes/vsultlong-md.md)] または [!INCLUDE[vsPreLong](../sharepoint/includes/vsprelong-md.md)]  
  
-   AdventureWorks サンプル データベースにアクセスします。 AdventureWorks データベースをインストールする方法の詳細については、次を参照してください。 [SQL Server サンプル データベース](http://go.microsoft.com/fwlink/?LinkID=117483)です。  
  
## <a name="creating-a-project-that-contains-a-bdc-model"></a>BDC モデルを含むプロジェクトを作成する  
  
#### <a name="to-create-a-project-that-contains-a-bdc-model"></a>BDC モデルを含むプロジェクトを作成するには  
  
1.  Visual Studio のメニュー バー、**ファイル**、**新規**、**プロジェクト**です。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  いずれかで**Visual c#**または**Visual Basic**、展開、 **SharePoint**  ノードを選択し、 **2010**項目。  
  
3.  **テンプレート** ウィンドウで、選択**SharePoint 2010 プロジェクト**、プロジェクトに名前を**AdventureWorksTest**を選択し、 **OK**ボタン.  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。 このウィザードでは、プロジェクトのデバッグし、ソリューションの信頼レベルを設定するときに使用するサイトを指定できます。  
  
4.  選択、**ファーム ソリューションとして配置**信頼レベルを設定するオプション ボタンをクリックします。  
  
5.  選択、**完了**ボタンをクリックして既定のローカル SharePoint サイトです。  
  
6.  **ソリューション エクスプ ローラー**、SharePoint プロジェクト ノードを選択します。  
  
7.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
     **[新しい項目の追加]** ダイアログ ボックスが開きます。  
  
8.  **テンプレート** ウィンドウで、選択**ビジネス データ接続モデル (ファーム ソリューションのみ)**、プロジェクトに名前を**AdventureWorksContacts**、を選択し**追加**ボタンをクリックします。  
  
## <a name="adding-data-access-classes-to-the-project"></a>プロジェクトに追加のデータ アクセス クラス  
  
#### <a name="to-add-data-access-classes-to-the-project"></a>データ アクセス クラスをプロジェクトに追加するには  
  
1.  メニュー バーで、次のように選択します。**ツール**、**データベースへの接続**です。  
  
     **接続の追加** ダイアログ ボックスが表示されます。  
  
2.  SQL Server の AdventureWorks サンプル データベースへの接続を追加します。  
  
     詳細については、次を参照してください。[追加/変更接続 (Microsoft SQL Server)](http://msdn.microsoft.com/en-us/fa400910-26c3-4df7-b9d1-115e688b4ea3)です。  
  
3.  **ソリューション エクスプローラー**で、プロジェクト ノードを選択します。  
  
4.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
5.  **インストールされたテンプレート** ウィンドウで、選択、**データ**ノード。  
  
6.  **テンプレート** ウィンドウで、選択**LINQ to SQL クラス**です。  
  
7.  **名前**ボックスで、指定**AdventureWorks**を選択し、**追加**ボタンをクリックします。  
  
     プロジェクトに .dbml ファイルが追加され、オブジェクト リレーショナル デザイナー (O/R デザイナー) が表示されます。  
  
8.  メニュー バーで、次のように選択します。**ビュー**、**サーバー エクスプ ローラー**です。  
  
9. **サーバー エクスプ ローラー**、AdventureWorks サンプル データベースを表すノードを展開し、展開、**テーブル**ノード。  
  
10. 追加、 **(Person) にお問い合わせください**O/R デザイナーにテーブルです。  
  
     エンティティ クラスが作成され、デザイン サーフェイスに表示されます。 エンティティ クラスには、Contact (Person) テーブルの列にマップされるプロパティがあります。  
  
## <a name="removing-the-default-entity-from-the-bdc-model"></a>既定のエンティティを BDC モデルから削除します。  
 **ビジネス データ接続モデル**という名前では、Entity1 のモデルを既定のエンティティが追加されます。 このエンティティを削除します。 その後、新しいエンティティを追加します。 以降、空のモデルで、チュートリアルを完了に必要な手順の数が減少します。  
  
#### <a name="to-remove-the-default-entity-from-the-model"></a>既定のエンティティをモデルから削除するには  
  
1.  **ソリューション エクスプ ローラー**、展開、 **BdcModel1**ノード、およびし BdcModel1.bdcm ファイルを開きます。  
  
2.  ビジネス データ接続モデル ファイルは、BDC デザイナーで開きます。  
  
3.  デザイナーでのショートカット メニューを開いて**Entity1**を選択し**削除**です。  
  
4.  **ソリューション エクスプ ローラー**Entity1.vb (Visual Basic で) または (C# の場合)、Entity1.cs のショートカット メニューを開き、クリックして**削除**です。  
  
5.  (Visual Basic) の Entity1Service.vb または (C# の場合)、Entity1Service.cs のショートカット メニューを開きを選択し、**削除**です。  
  
## <a name="adding-an-entity-to-the-model"></a>モデルにエンティティを追加します。  
 モデルにエンティティを追加します。 エンティティを追加するには、Visual Studio から**ツールボックス**BDC デザイナーにします。  
  
#### <a name="to-add-an-entity-to-the-model"></a>モデルにエンティティを追加するには  
  
1.  メニュー バーで **[表示]**、**[ツールボックス]** の順に選択します。  
  
2.  **BusinessDataConnectivity**のタブ、**ツールボックス**、追加、**エンティティ**BDC デザイナーにします。  
  
     デザイナーに新しいエンティティが表示されます。 Visual Studio では、プロジェクトに (Visual Basic) の名前付き EntityService.vb または EntityService.cs (C# の場合) であるファイルを追加します。  
  
3.  メニュー バーで、次のように選択します。**ビュー**、**プロパティ**、**ウィンドウ**します。  
  
4.  **プロパティ**ウィンドウで、設定、**名前**プロパティの値を**連絡先**です。  
  
5.  デザイナーで、エンティティのショートカット メニューを開き、選択**追加**を選択し**識別子**です。  
  
     エンティティに新しい識別子が表示されます。  
  
6.  **プロパティ**ウィンドウで、識別子の名前を変更**ContactID**です。  
  
7.  **型名**一覧で、選択**System.Int32**です。  
  
## <a name="adding-a-specific-finder-method"></a>Specificfinder メソッドを追加します。  
 特定の連絡先を表示する BDC サービスを有効にするには、Specific Finder メソッドを追加する必要があります。 BDC サービスは、ユーザーがリストに項目を選択し、選択し、ときに Specific Finder メソッドを呼び出します、**ビュー アイテム**リボンのボタンをクリックします。  
  
 使用して、Contact エンティティに Specific Finder メソッドを追加、 **BDC メソッドの詳細**ウィンドウです。 特定のエンティティを返すには、メソッドにコードを追加します。  
  
#### <a name="to-add-a-specific-finder-method"></a>Specificfinder メソッドを追加するには  
  
1.  BDC デザイナーで、選択、**連絡先**エンティティです。  
  
2.  メニュー バーで、次のように選択します。**ビュー**、**その他のウィンドウ**、 **BDC メソッドの詳細**です。  
  
     [BDC メソッドの詳細] ウィンドウを開きます。  
  
3.  **メソッドを追加**一覧で、選択**特定 Finder メソッドの作成**です。  
  
     Visual Studio では、モデルに、次の要素を追加します。 これらの要素の表示で、 **BDC メソッドの詳細**ウィンドウです。  
  
    -   ReadItem をという名前のメソッドです。  
  
    -   メソッドの入力パラメーター。  
  
    -   メソッドの戻り値のパラメーターです。  
  
    -   各パラメーターの型記述子。  
  
    -   メソッドのメソッドのインスタンス。  
  
4.  **BDC メソッドの詳細**ウィンドウで、について表示されるリストを開く、**連絡先**記述子を入力し、**編集**です。  
  
     **BDC エクスプ ローラー**開き、モデルの階層ビューを提供します。  
  
5.  **プロパティ**ウィンドウで、横に、リストを開く、 **TypeName**プロパティを選択、**現在のプロジェクト** タブをクリックして、**連絡先**プロパティです。  
  
6.  **BDC エクスプ ローラー**のショートカット メニューを開き、**連絡先**を選択し**型記述子の追加**です。  
  
     という新しい型記述子**TypeDescriptor1**に表示されます、 **BDC エクスプ ローラー**です。  
  
7.  **プロパティ**ウィンドウで、設定、**名前**プロパティの値を**ContactID**です。  
  
8.  横に、一覧を開き、 **TypeName**プロパティを選択し**Int32**です。  
  
9. 横に、リストを開く、**識別子**プロパティを選択し**ContactID**です。  
  
10. 手順 6 には、次のフィールドごとに、型記述子を作成します。  
  
    |name|型の名前|  
    |----------|---------------|  
    |FirstName|System.String|  
    |LastName|System.String|  
    |電話番号|System.String|  
    |emailAddress|System.String|  
    |EmailPromotion|System.Int32|  
    |NameStyle|System.Boolean|  
    |PasswordHash|System.String|  
    |PasswordSalt|System.String|  
  
11. BDC デザイナーでの**連絡先**エンティティ、開いている、 **ReadItem**メソッドです。  
  
     連絡先サービス コード ファイルでは、コード エディターで開きます。  
  
12. `ContactService`クラス、置換、`ReadItem`メソッドを次のコード。 このコードは次のタスクを実行します。  
  
    -   AdventureWorks データベースの Contact テーブルからレコードを取得します。  
  
    -   BDC サービスには、Contact エンティティを返します。  
  
    > [!NOTE]  
    >  値を置き換える、`ServerName`フィールドに、サーバーの名前。  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="adding-a-finder-method"></a>Finder メソッドを追加します。  
 一覧で、連絡先を表示する BDC サービスを有効にするには、Finder メソッドを追加する必要があります。 Finder メソッド エンティティに追加する連絡先を使用して、 **BDC メソッドの詳細**ウィンドウです。 BDC サービスに返すエンティティのコレクションには、メソッドにコードを追加します。  
  
#### <a name="to-add-a-finder-method"></a>Finder メソッドを追加するには  
  
1.  BDC デザイナーで、**連絡先**エンティティです。  
  
2.  **BDC メソッドの詳細**ウィンドウで、縮小、 **ReadItem**ノード。  
  
3.  **メソッドを追加**下にあるを一覧表示、 **ReadList**メソッドを選択して**Finder メソッドの作成**です。  
  
     Visual Studio では、メソッド、戻りパラメーター、および型記述子を追加します。  
  
4.  BDC デザイナーでの**連絡先**エンティティ、開いている、 **ReadList**メソッドです。  
  
     連絡先サービスのコード ファイルでは、コード エディターで開きます。  
  
5.  `ContactService`クラス、置換、`ReadList`メソッドを次のコード。 このコードは次のタスクを実行します。  
  
    -   AdventureWorks データベースの Contacts テーブルからデータを取得します。  
  
    -   BDC サービスにお問い合わせくださいエンティティの一覧を返します。  
  
    > [!NOTE]  
    >  値を置き換える、`ServerName`フィールドに、サーバーの名前。  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="testing-the-project"></a>プロジェクトのテスト  
 プロジェクトを実行するときに SharePoint サイトが表示され、Visual Studio は、ビジネス データ接続サービスをモデルを追加します。 Contact エンティティを参照している SharePoint の外部リストを作成します。 一覧で、AdventureWorks データベースで連絡先データが表示されます。  
  
> [!NOTE]  
>  ソリューションをデバッグする前に、SharePoint のセキュリティ設定を変更する必要があります。  詳細については、次を参照してください。[ビジネス データ接続モデルをデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)です。  
  
#### <a name="to-test-the-project"></a>プロジェクトをテストするには  
  
1.  **F5** キーを押します。  
  
     SharePoint サイトが開きます。  
  
2.  **サイトの操作** メニューを選択して、**他のオプション**コマンド。  
  
3.  **作成**ページで、選択、**外部リスト**テンプレートを選択し、**作成**ボタンをクリックします。  
  
4.  カスタム リストの名前**連絡先**です。  
  
5.  次に [参照] ボタンをクリックして、**外部コンテンツ タイプ**フィールドです。  
  
6.  **コンテンツの種類の選択を外部** ダイアログ ボックスで、選択、 **AdventureWorksContacts.BdcModel1.Contact**項目をクリックして、**作成**ボタンをクリックします。  
  
     SharePoint では、AdventureWorks サンプル データベースからの連絡先を含む外部リストを作成します。  
  
7.  Specificfinder メソッドをテストするには、一覧で、連絡先を選択します。  
  
8.  リボンで、選択、**項目** タブをクリックして、**ビュー アイテム**コマンド。  
  
     選択した連絡先の詳細は、フォームに表示されます。  
  
## <a name="next-steps"></a>次の手順  
 これらのトピックから SharePoint の BDC サービスのモデルをデザインする方法の詳細を学習できます。  
  
-   [方法: Creator メソッドを追加](../sharepoint/how-to-add-a-creator-method.md)です。  
  
-   [方法: Updater メソッドを追加](../sharepoint/how-to-add-an-updater-method.md)です。  
  
-   [方法: Deleter メソッドを追加](../sharepoint/how-to-add-a-deleter-method.md)です。  
  
## <a name="see-also"></a>参照  
 [ビジネス データ接続モデルの設計](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [ビジネス データ接続モデルを作成します。](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)   
 [SharePoint へのビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  