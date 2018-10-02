---
title: データを検索する Windows フォームの作成 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], paramaterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a64377e2689ca4e5111f316c13808aee6cfb59be
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545454"
---
# <a name="create-a-windows-form-to-search-data"></a>データを検索する Windows フォームを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[データを検索する Windows フォームの作成](https://docs.microsoft.com/visualstudio/data-tools/create-a-windows-form-to-search-data)です。  
  
  
一般的なアプリケーションのシナリオでは、選択したデータをフォーム上に表示します。 たとえば、特定の顧客の注文、特定の注文の明細などを表示する場合があります。 このシナリオでは、ユーザーがフォームに情報を入力した後、ユーザーの入力をパラメーターとして使用してクエリが実行されます。つまり、パラメーター クエリに基づいてデータが選択されます。 クエリは、ユーザーが入力した条件を満たすデータのみを返します。 ここでは、特定の都市にいる顧客を返すクエリを作成する方法、およびユーザー インターフェイスを変更して、ユーザーが都市の名前を入力してクエリを実行するボタンを押すことができるようにする方法について説明します。  
  
 パラメーター クエリを使用することにより、データベースが最も得意とする作業 (レコードの迅速なフィルター処理) をデータベースに任せることができるため、アプリケーションの効率が高まります。 これに対し、データベース テーブル全体を要求、ネットワーク経由で転送、目的のレコードを検索するアプリケーション ロジックを使用した場合は、アプリケーションは低速で非効率的ななることができます。  
  
 パラメーター化クエリを追加するには、TableAdapter (およびコントロール パラメーターの値をそのまま使用し、クエリを実行する) を使用して、**検索条件ビルダー**  ダイアログ ボックス。 選択してダイアログ ボックスが開き、**クエリの追加**コマンドを**データ**メニュー (または TableAdapter スマート タグ)。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   新しい Windows フォーム アプリケーション プロジェクトを作成します。  
  
-   使用してアプリケーションでのデータ ソースの構成の作成と、**データ ソースの構成**ウィザード。  
  
-   内の項目のドロップ タイプを設定、**データソース**ウィンドウ。  
  
-   項目をドラッグしてデータを表示するコントロールを作成、**データソース**ウィンドウからフォームにします。  
  
-   データを表示するコントロールをフォームに追加します。  
  
-   完了、**検索条件ビルダー**  ダイアログ ボックス。  
  
-   フォームにパラメーターを入力し、パラメーター化クエリを実行します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベースにアクセスします。  
  
## <a name="create-the-windows-application"></a>Windows アプリケーションを作成します。  
 作成するには、まず、 **Windows アプリケーション**します。 プロジェクトに名前を割り当てるはこの手順で、省略可能ですが、名前を付けますが、ここでため、後で保存します。  
  
#### <a name="to-create-the-new-windows-application-project"></a>新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  **ファイル**] メニューの [新しいプロジェクトを作成します。  
  
2.  プロジェクトに `WindowsSearchForm` という名前を付けます。  
  
3.  選択**Windows アプリケーション** をクリック**OK**します。  
  
     **WindowsSearchForm**プロジェクトが作成されに追加**ソリューション エクスプ ローラー**します。  
  
## <a name="create-the-data-source"></a>データ ソースを作成します。  
 この手順を使用してデータベースからのデータ ソースの作成、**データ ソースの構成**ウィザード。 接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。 Northwind サンプル データベースのセットアップについては、次を参照してください。[サンプル データベースの SQL Server のインストール](../data-tools/install-sql-server-sample-databases.md)します。  
  
#### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。  
  
2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソースの構成**ウィザード。  
  
3.  **[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]** をクリックします。  
  
4.  **データ接続の選択**ページは、次のいずれか。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。  
  
    -   選択**新しい接続**を起動する、**接続の追加/変更** ダイアログ ボックス。  
  
5.  データベースにパスワードが必要な場合をクリックして、機密データを含めるオプションを選択**次**します。  
  
6.  **接続文字列をアプリケーション構成ファイルに保存**] ページで [**次**します。  
  
7.  **データベース オブジェクトの選択** ページで、展開、**テーブル**ノード。  
  
8.  選択、**顧客**テーブルをクリックして**完了**。  
  
     **NorthwindDataSet**がプロジェクトに追加し、**顧客**テーブルに表示されます、**データ ソース**ウィンドウ。  
  
## <a name="create-the-form"></a>フォームを作成します。  
 項目をドラッグして、データ バインド コントロールを作成することができます、**データソース**ウィンドウから、フォームにします。  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>フォームにデータ バインド コントロールを作成するには  
  
1.  展開、**顧客**内のノード、**データソース**ウィンドウ。  
  
2.  ドラッグ、**顧客**ノードから、**データ ソース**ウィンドウ、フォームにします。  
  
     <xref:System.Windows.Forms.DataGridView> と、レコード間を移動するためのツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォーム上に表示されます。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、 [CustomersTableAdapter](../data-tools/tableadapter-overview.md)、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。  
  
## <a name="addparameterization-search-functionality-to-the-query"></a>クエリに Addparameterization (検索機能)  
 WHERE 句を追加するには元のクエリを使用する、**検索条件ビルダー**  ダイアログ ボックス。  
  
#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>パラメーター クエリとコントロールを作成してパラメーターを入力するには  
  
1.  選択、<xref:System.Windows.Forms.DataGridView>コントロールを選び、**クエリの追加**上、**データ**メニュー。  
  
2.  型`FillByCity`で、**新しいクエリ名**上の領域、**検索条件ビルダー**  ダイアログ ボックス。  
  
3.  追加`WHERE City = @City`でクエリを**クエリ テキスト**領域。  
  
     クエリは次のようになります。  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  アクセスおよび OLE DB データ ソースは疑問符 () を使用して ('? ') パラメーターを示すためにそのため、WHERE 句はようになります:`WHERE City = ?`します。  
  
4.  クリックして**OK**を閉じる、**検索条件ビルダー**  ダイアログ ボックス。  
  
     A **FillByCityToolStrip**フォームに追加されます。  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 アプリケーションを実行すると、パラメーターを入力として取得できる状態のフォームが開きます。  
  
#### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  F5 キーを押してアプリケーションを実行します。  
  
2.  型**ロンドン**に、**市区町村**テキスト ボックス、およびクリック**FillByCity**します。  
  
     データ グリッドには、条件を満たす顧客が取得されます。 この例では、データ グリッドのみが表示されますの値を持つ顧客**ロンドン**でその**市区町村**列。  
  
## <a name="next-steps"></a>次の手順  
 アプリケーションの要件に応じて、パラメーター付きのフォームを作成した後に、追加の操作を実行できます。 このチュートリアルで行うことができる拡張には次のものがあります。  
  
-   関連するデータを表示するコントロールを追加します。 詳細については、「[方法: 関連するデータを Windows フォーム アプリケーションに表示する](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)」を参照してください。  
  
-   データセットを編集し、データベース オブジェクトの追加または削除を行います。 詳細については、[データセットの作成と構成](../data-tools/create-and-configure-datasets-in-visual-studio.md)に関するページを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

