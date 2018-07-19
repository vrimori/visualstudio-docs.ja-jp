---
title: 'チュートリアル : データセット デザイナーでのデータセットの作成'
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 32a093e59d918f34ddf5da9cbb5edb13c96b2777
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117928"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>チュートリアル: データセット デザイナーでデータセットを作成します。

使用してデータセットを作成するこのチュートリアルでは、**データセット デザイナー**します。 記事では、新しいプロジェクトを作成し、新しい追加のプロセス**データセット**項目にします。 ウィザードを使用せず、データベース内のテーブルに基づいて、テーブルを作成する方法について説明します。

## <a name="prerequisites"></a>前提条件

このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 一部として Visual Studio インストーラーでは、SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (SQL Server オブジェクト エクスプ ローラーがの一部としてインストールされている、**データ ストレージと処理**Visual Studio インストーラーにワークロード)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が終了し、Northwind データベースを作成します。

## <a name="create-a-new-windows-forms-application-project"></a>新しい Windows フォーム アプリケーション プロジェクトを作成します。

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

3. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**DatasetDesignerWalkthrough**を選び、 **OK**。

     Visual Studio にプロジェクトが追加**ソリューション エクスプ ローラー**し、デザイナーで新しいフォームを表示します。

## <a name="add-a-new-dataset-to-the-application"></a>アプリケーションに新しいデータセットを追加します。

1.  **プロジェクト**メニューの **新しい項目の追加**します。

     **[新しい項目の追加]** ダイアログ ボックスが表示されます。

2.  左側のウィンドウで次のように選択します。**データ**を選択し、**データセット**中央のペインでします。

3.  データセットの名前を付けます**NorthwindDataset**を選び、**追加**します。

     Visual Studio がという名前のファイルを追加します**NorthwindDataset.xsd**プロジェクトで開くと、**データセット デザイナー**。

## <a name="create-a-data-connection-in-server-explorer"></a>サーバー エクスプ ローラーでのデータ接続を作成します。

1.  **ビュー**  メニューのをクリックして**サーバー エクスプ ローラー**します。

2.  **サーバー エクスプ ローラー**、クリックして、**データベースへの接続**ボタンをクリックします。

3.  Northwind サンプル データベースへの接続を作成します。

## <a name="create-the-tables-in-the-dataset"></a>データセットにテーブルを作成します。

このセクションでは、データセットにテーブルを追加する方法について説明します。

### <a name="to-create-the-customers-table"></a>Customers テーブルを作成するには

1.  作成したデータ接続を展開**サーバー エクスプ ローラー**の順に展開し、**テーブル**ノード。

2.  ドラッグ、**顧客**からテーブル**サーバー エクスプ ローラー**上に、**データセット デザイナー**します。

     A**顧客**データ テーブルと**CustomersTableAdapter**データセットに追加されます。

### <a name="to-create-the-orders-table"></a>Orders テーブルを作成するには

-   ドラッグ、**注文**からテーブル**サーバー エクスプ ローラー**上に、**データセット デザイナー**します。

     **注文**データ テーブル、 **OrdersTableAdapter**との間でデータのリレーションシップ、**顧客**と**注文**テーブルに追加されます、データセット。

### <a name="to-create-the-orderdetails-table"></a>OrderDetails テーブルを作成するには

-   ドラッグ、 **Order Details**からテーブル**サーバー エクスプ ローラー**上に、**データセット デザイナー**します。

     **Order Details**データ テーブル、 **OrderDetailsTableAdapter**との間のリレーションシップ、**注文**と**OrderDetails**テーブルデータセットに追加されます。

## <a name="next-steps"></a>次の手順

-   データセットを保存します。

-   項目を選択、**データ ソース**ウィンドウ、フォームにドラッグするとします。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールを Windows フォームのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)します。

-   TableAdapter に他のクエリを追加します。

-   データセット内のデータ テーブルの <xref:System.Data.DataTable.ColumnChanging> イベントまたは <xref:System.Data.DataTable.RowChanging> イベントに検証ロジックを追加します。 詳細については、次を参照してください。[検証データセットのデータの](../data-tools/validate-data-in-datasets.md)します。

## <a name="see-also"></a>関連項目

- [Visual Studio でデータセットを作成および構成する](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [データを検証します。](../data-tools/validate-data-in-datasets.md)