---
title: 'チュートリアル: ビジネス データを使用して SharePoint に外部リストの作成 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 96c52d1d30444aa557465ce2022a3ef1db4c3de0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53918785"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>チュートリアル: ビジネス データを使用して SharePoint に外部リストを作成します。

バック エンド サーバー アプリケーション、Web サービス、およびデータベースからビジネス データを表示するビジネス データ接続 (BDC) サービスを有効にします。

このチュートリアルでは、サンプル データベース内の連絡先に関する情報を返しますという、BDC サービスのモデルを作成する方法を示します。 このモデルを使用して、外部リストを SharePoint で作成したが、します。

このチュートリアルでは、次の作業について説明します。

- プロジェクトを作成します。
- モデルにエンティティを追加します。
- Finder メソッドを追加します。
- Specificfinder メソッドを追加します。
- プロジェクトをテストします。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

- サポート対象エディションの Windows と SharePoint

- AdventureWorks サンプル データベースへのアクセス。 AdventureWorks データベースをインストールする方法の詳細については、次を参照してください。 [SQL Server サンプル データベース](http://go.microsoft.com/fwlink/?LinkID=117483)します。

## <a name="create-a-project-that-contains-a-bdc-model"></a>BDC モデルを含むプロジェクトを作成します。

1. Visual Studio でメニュー バー、**ファイル** > **新規** > **プロジェクト**します。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

2. いずれかで**Visual c#** または**Visual Basic**、展開、 **SharePoint**ノードを選択し、 **2010**項目。

3. **テンプレート**ウィンドウで、選択**SharePoint 2010 プロジェクト**、プロジェクトに名前を**AdventureWorksTest**、選択し、 **OK**ボタン.

     **SharePoint カスタマイズ ウィザード**が表示されます。 このウィザードでは、プロジェクトをデバッグして、ソリューションの信頼レベルの設定に使用するサイトを指定できます。

4. 選択、**ファーム ソリューションとして配置**信頼レベルを設定するオプション ボタンをクリックします。

5. 選択、**完了**を既定のローカル SharePoint サイトを受け入れるようにボタンをクリックします。

6. **ソリューション エクスプ ローラー**、SharePoint プロジェクト ノードを選択します。

7. メニュー バーで **[プロジェクト]** > **[新しい項目の追加]** の順に選択します。

     **[新しい項目の追加]** ダイアログ ボックスが開きます。

8. **テンプレート**ウィンドウで、選択**ビジネス データ接続モデル (ファーム ソリューションのみ)**、プロジェクトに名前を**AdventureWorksContacts**、を選択し**追加**ボタンをクリックします。

## <a name="add-data-access-classes-to-the-project"></a>データ アクセス クラスをプロジェクトに追加します。

1. メニュー バーで、**ツール** > **データベースへの接続**します。

     **接続の追加** ダイアログ ボックスが表示されます。

2. SQL Server の AdventureWorks サンプル データベースへの接続を追加します。

     詳細については、次を参照してください。[接続接続の追加/変更 (Microsoft SQL Server)](https://msdn.microsoft.com/fa400910-26c3-4df7-b9d1-115e688b4ea3)します。

3. **ソリューション エクスプローラー**で、プロジェクト ノードを選択します。

4. メニュー バーで **[プロジェクト]** > **[新しい項目の追加]** の順に選択します。

5. **インストールされたテンプレート**ウィンドウで、選択、**データ**ノード。

6. **テンプレート**ウィンドウで、選択**LINQ to SQL クラス**します。

7. **名前**ボックスで、指定**AdventureWorks**、選択し、**追加**ボタンをクリックします。

     .Dbml ファイルがプロジェクトに追加し、オブジェクト リレーショナル デザイナー (O/R デザイナー) を開きます。

8. メニュー バーで、**ビュー** > **サーバー エクスプ ローラー**します。

9. **サーバー エクスプ ローラー**、AdventureWorks サンプル データベースを表すノードを展開し、展開、**テーブル**ノード。

10. 追加、 **(Person) にお問い合わせください**O/R デザイナーにテーブルです。

     エンティティ クラスが作成され、デザイン サーフェイスに表示されます。 エンティティ クラスには、Contact (Person) テーブルの列にマップされるプロパティがあります。

## <a name="remove-the-default-entity-from-the-bdc-model"></a>BDC モデルからの既定のエンティティを削除します。

**Business Data Connectivity モデル**プロジェクト モデルでは、Entity1 をという名前の既定のエンティティを追加します。 このエンティティを削除します。 後で、新しいエンティティを追加します。 以降では、空のモデルは、このチュートリアルを完了に必要な手順の数を減らします。

1. **ソリューション エクスプ ローラー**、展開、 **BdcModel1**ノード、および順に開いて、 *BdcModel1.bdcm*ファイル。

2. Business Data Connectivity モデル ファイルは、BDC デザイナーで開きます。

3. デザイナーで、ショートカット メニューを開き、 **Entity1**を選び、**削除**します。

4. **ソリューション エクスプ ローラー**、ショートカット メニューを開き*Entity1.vb* (Visual Basic) でまたは*Entity1.cs* (c# で) を選び、**削除**.

5. ショートカット メニューを開き*Entity1Service.vb* (Visual Basic) でまたは*Entity1Service.cs* (で c#)、し**削除**します。

## <a name="add-an-entity-to-the-model"></a>エンティティ モデルを追加します。

モデルにエンティティを追加します。 エンティティを追加するには、Visual Studio から**ツールボックス**BDC デザイナーにします。

1. メニュー バーで **[表示]**、**[ツールボックス]** の順にクリックします。

2. **BusinessDataConnectivity**のタブ、**ツールボックス**、追加、**エンティティ**BDC デザイナーにします。

     デザイナーで新しいエンティティが表示されます。 Visual Studio は、という名前のファイルを追加します。 *EntityService.vb* (Visual Basic) でまたは*EntityService.cs* (で C# の場合) をプロジェクトにします。

3. メニュー バーで、**ビュー** > **プロパティ** > **ウィンドウ**します。

4. **プロパティ**ウィンドウで、設定、**名前**プロパティの値を**連絡先**します。

5. デザイナーで、エンティティのショートカット メニューを開き、選択**追加**を選び、**識別子**します。

     エンティティに新しい識別子が表示されます。

6. **プロパティ**ウィンドウで、識別子の名前を変更**ContactID**します。

7. **型名**一覧で、選択**System.Int32**します。

## <a name="add-a-specific-finder-method"></a>Specificfinder メソッドを追加します。

特定の連絡先を表示する BDC サービスを有効にするには、Specificfinder メソッドを追加する必要があります。 ユーザーがリストの項目を選択し、選択したときに、BDC サービスが Specificfinder メソッドを呼び出す、**ビュー項目**リボンのボタンをクリックします。

使用して、Contact エンティティを Specificfinder メソッドを追加、 **BDC メソッドの詳細**ウィンドウ。 特定のエンティティを返すには、メソッドにコードを追加します。

1. BDC デザイナーで、選択、**連絡先**エンティティ。

2. メニュー バーで、**ビュー** > **その他の Windows** > **BDC メソッドの詳細**します。

     BDC メソッドの詳細ウィンドウが開きます。

3. **メソッドを追加する**一覧で、選択**特定 Finder メソッドの作成**です。

     Visual Studio では、モデルに、次の要素を追加します。 これらの要素、 **BDC メソッドの詳細**ウィンドウ。

    - ReadItem をという名前のメソッド。

    - メソッドの入力パラメーター。

    - メソッドの戻り値のパラメーター。

    - 各パラメーターの型記述子。

    - メソッドのメソッドのインスタンス。

4. **BDC メソッドの詳細**ウィンドウで、について表示される一覧を開き、**連絡先**記述子を入力し、**編集**します。

     **BDC エクスプ ローラー**が開き、モデルの階層ビューを提供します。

5. **プロパティ**ウィンドウで、次に、一覧を開き、 **TypeName**プロパティ、選択、**現在のプロジェクト**、タブをクリックして、 **にお問い合わせください**プロパティ。

6. **BDC エクスプ ローラー**のショートカット メニューを開き、**連絡先**を選び、**型記述子の追加**。

     という新しい型記述子**TypeDescriptor1**に表示されます、 **BDC エクスプ ローラー**します。

7. **プロパティ**ウィンドウで、設定、**名前**プロパティの値を**ContactID**します。

8. 次に、一覧を開き、 **TypeName**プロパティを選び、 **Int32**。

9. 横に、一覧を開き、**識別子**プロパティを選び、 **ContactID**します。

10. 手順 6 の各次のフィールドの型記述子を作成する.

    |名前|型の名前|
    |----------|---------------|
    |FirstName|System.String|
    |LastName|System.String|
    |電話番号|System.String|
    |EmailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. BDC デザイナーでの**連絡先**エンティティ、オープン、 **ReadItem**メソッド。

     連絡先のサービス コード ファイルでは、コード エディターで開きます。

12. `ContactService`クラス、置換、`ReadItem`メソッドを次のコード。 このコードは次のタスクを実行します。

    - AdventureWorks データベースの Contact テーブルからレコードを取得します。

    - BDC サービスには、Contact エンティティを返します。

    > [!NOTE]
    > 値を置き換える、`ServerName`フィールドに、サーバーの名前。

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Finder メソッドを追加します。

一覧で、連絡先を表示する BDC サービスを有効にするには、Finder メソッドを追加する必要があります。 使用して、Contact エンティティを Finder メソッドを追加、 **BDC メソッドの詳細**ウィンドウ。 BDC サービスに返すエンティティのコレクションには、メソッドにコードを追加します。

1. BDC デザイナーで、**連絡先**エンティティ。

2. **BDC メソッドの詳細**ウィンドウ、折りたたみ、 **ReadItem**ノード。

3. **メソッドを追加する**下にある、 **ReadList**メソッド選択**Finder メソッドの作成**です。

     Visual Studio では、メソッド、戻りパラメーター、および型記述子を追加します。

4. BDC デザイナーでの**連絡先**エンティティ、オープン、 **ReadList**メソッド。

     連絡先サービスのコード ファイルでは、コード エディターで開きます。

5. `ContactService`クラス、置換、`ReadList`メソッドを次のコード。 このコードは次のタスクを実行します。

   - AdventureWorks データベースの Contacts テーブルからデータを取得します。

   - BDC サービスには、Contact エンティティの一覧を返します。

     > [!NOTE]
     > 値を置き換える、`ServerName`フィールドに、サーバーの名前。

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>プロジェクトをテストします。

プロジェクトを実行するときに、SharePoint サイトが表示され、Visual Studio は、ビジネス データ接続サービスにモデルを追加します。 Contact エンティティを参照する SharePoint の外部リストを作成します。 一覧で、AdventureWorks データベースで連絡先データが表示されます。

> [!NOTE]
> ソリューションをデバッグする前に、SharePoint のセキュリティ設定を変更する必要があります。 詳細については、次を参照してください。[ビジネス データ接続モデルを設計する](../sharepoint/designing-a-business-data-connectivity-model.md)します。

1. **F5** キーを押します。

     SharePoint サイトが開きます。

2. **サイトの操作**メニューで、選択、**オプションより**コマンド。

3. **作成**ページで、選択、**外部リスト**テンプレートを選択し、**作成**ボタン。

4. カスタム リストの名前**連絡先**します。

5. 次に、参照ボタンを選択、**外部コンテンツ タイプ**フィールド。

6. **外部コンテンツ タイプ ピッカー**  ダイアログ ボックスで、選択、 **AdventureWorksContacts.BdcModel1.Contact**項目を選び、**作成**ボタンをクリックします。

     SharePoint では、AdventureWorks サンプル データベースからの連絡先を格納する外部リストを作成します。

7. Specificfinder メソッドをテストするには、一覧に連絡先を選択します。

8. リボンで、選択、**項目**、タブをクリックして、**ビュー項目**コマンド。

     選択した連絡先の詳細については、フォームに表示されます。

## <a name="next-steps"></a>次の手順

これらのトピックから SharePoint の BDC サービスのモデルを設計する方法の詳細を確認できます。

- [方法: Creator メソッドを追加](../sharepoint/how-to-add-a-creator-method.md)します。
- [方法: Updater メソッドを追加](../sharepoint/how-to-add-an-updater-method.md)します。
- [方法: Deleter メソッドを追加](../sharepoint/how-to-add-a-deleter-method.md)します。

## <a name="see-also"></a>関連項目

[ビジネス データ接続モデルを設計します。](../sharepoint/designing-a-business-data-connectivity-model.md)  
[ビジネス データ接続モデルを作成します。](../sharepoint/creating-a-business-data-connectivity-model.md)  
[BDC モデルのデザイン ツールの概要](../sharepoint/bdc-model-design-tools-overview.md)  
[SharePoint ビジネス データを統合します。](../sharepoint/integrating-business-data-into-sharepoint.md)
