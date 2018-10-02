---
title: 'チュートリアル: WPF アプリケーションで関連データの表示 |Microsoft Docs'
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
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f6a052f7894c37e35defc748528b01124957cbc6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534943"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>チュートリアル: WPF アプリケーションでの関連データの表示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルでは、親/子リレーションシップを持つデータベース テーブルからデータを表示する WPF アプリケーションを作成します。 データは、エンティティ データ モデル内のエンティティにカプセル化します。 親エンティティには、一連の注文の概要情報が含まれています。 このエンティティの各プロパティは、アプリケーションで別のコントロールにバインドされます。 子エンティティには、各注文の詳細が含まれています。 この一連のデータにバインドする<xref:System.Windows.Controls.DataGrid>コントロール。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   WPF アプリケーションと、AdventureWorksLT サンプル データベース内のデータから生成される Entity Data Model を作成します。  
  
-   一連の注文の概要情報を表示するデータ バインド コントロールのセットを作成します。 親エンティティをドラッグして、コントロールを作成する、**データソース**ウィンドウ**WPF デザイナー**します。  
  
-   作成、<xref:System.Windows.Controls.DataGrid>ごとに関連する詳細を表示するコントロールは、順序を選択します。 子エンティティをドラッグして、コントロールを作成する、**データソース**ウィンドウのウィンドウに**WPF デザイナー**します。  
  
     [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
-   AdventureWorksLT サンプル データベースが添付された、SQL Server または SQL Server Express の実行中のインスタンスへのアクセス権。 AdventureWorksLT データベースをダウンロードすることができます、 [CodePlex Web サイト](http://go.microsoft.com/fwlink/?linkid=87843)します。  
  
 次の概念に関する知識があると役立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   Entity Data Model および ADO.NET Entity Framework。 詳細については、次を参照してください。 [Entity Framework の概要](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0)します。  
  
-   WPF デザイナーの操作。 詳細については、次を参照してください。 [WPF および Silverlight デザイナーの概要](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62)します。  
  
-   WPF データ バインディング。 詳しくは、「 [データ バインディングの概要](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)」をご覧ください。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 注文レコードを表示する新しい WPF プロジェクトを作成します。  
  
#### <a name="to-create-a-new-wpf-project"></a>新しい WPF プロジェクトを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
3.  展開**Visual c#** または**Visual Basic**、し、 **Windows**します。  
  
4.  確認します **.NET Framework 4**  ダイアログ ボックスの上部にあるコンボ ボックスで選択されています。 <xref:System.Windows.Controls.DataGrid>このチュートリアルで使用するコントロールは、.NET Framework 4 でのみ使用できます。  
  
5.  選択、 **WPF アプリケーション**プロジェクト テンプレート。  
  
6.  **[名前]** ボックスに「`AdventureWorksOrdersViewer`」と入力します。  
  
7.  **[OK]** をクリックします。  
  
     Visual Studio によって作成、`AdventureWorksOrdersViewer`プロジェクト。  
  
## <a name="creating-an-entity-data-model-for-the-application"></a>アプリケーションのエンティティ データ モデルの作成  
 アプリケーションのデータ モデルを定義および追加する必要がありますデータ バインド コントロールを作成する前に、**データソース**ウィンドウ。 このチュートリアルでは、データ モデルは、Entity Data Model は。  
  
#### <a name="to-create-an-entity-data-model"></a>Entity Data Model を作成するには  
  
1.  **データ** メニューのをクリックして**新しいデータ ソースの追加**を開く、**データ ソース構成ウィザード**します。  
  
2.  **データ ソースの種類を選択**] ページで [**データベース**、順にクリックします**次**します。  
  
3.  **データベース モデルの選択**] ページで [ **Entity Data Model**、順にクリックします**次**。  
  
4.  **モデルのコンテンツの選択**] ページで [**データベースから生成**、順にクリックします**次**。  
  
5.  **データ接続の選択** ページで、次のいずれかを実行します。  
  
    -   AdventureWorksLT サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は、これを選択します。  
  
         - または -  
  
    -   クリックして**新しい接続**AdventureWorksLT データベースへの接続を作成します。  
  
     確認します、 **app.config にエンティティ接続設定の保存**オプションが選択されているをクリックして**次**します。  
  
6.  **データベース オブジェクトの選択** ページで、展開**テーブル**、次のテーブルを選択します。  
  
    -   **SalesOrderDetail**  
  
    -   **SalesOrderHeader**  
  
7.  **[完了]** をクリックします。  
  
8.  プロジェクトをビルドします。  
  
## <a name="creating-data-bound-controls-that-display-the-orders"></a>注文を表示するコントロールのデータ バインドを作成  
 ドラッグして、注文レコードを表示するコントロールを作成、`SalesOrderHeaders`からエンティティを**データソース**WPF デザイナーにウィンドウ。  
  
#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>注文レコードを表示するデータ バインド コントロールを作成するには  
  
1.  **ソリューション エクスプ ローラー**MainWindow.xaml をダブルクリックします。  
  
     WPF デザイナーでウィンドウが開きます。  
  
2.  XAML を編集するため、**高さ**と**幅**800 にプロパティが設定されます  
  
3.  **データ ソース**ウィンドウで、ドロップダウン メニューをクリックして、 **[salesorderheaders]** ノード**詳細**します。  
  
4.  展開、 **[salesorderheaders]** ノード。  
  
5.  横にドロップダウン メニューをクリックして**SalesOrderID**選択**ComboBox**します。  
  
6.  次の子ノードの各、 **[salesorderheaders]** ノード、次に、ノードのドロップダウン メニューをクリックし、選択**None**:  
  
    -   **RevisionNumber**  
  
    -   **OnlineOrderFlag**  
  
    -   **ShipToAddressID**  
  
    -   **BillToAddressID**  
  
    -   **CreditCardApprovalCode**  
  
    -   **小計の表示 します。**  
  
    -   **TaxAmt**  
  
    -   **Freight**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     この操作は、次の手順において、これらのノードに対応するデータ バインド コントロールが Visual Studio で作成されるのを防ぎます。 このチュートリアルでは、これらのデータをエンド ユーザーが参照する必要はありません。  
  
7.  **データソース**ウィンドウで、ドラッグ、 **[salesorderheaders]** ノードでのウィンドウに**WPF デザイナー**します。  
  
     Visual Studio 内のデータにバインドされているコントロールのセットを作成する XAML の生成、 **[salesorderheaders]** エンティティ、およびデータを読み込むコード。 生成された XAML とコードの詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)します。  
  
8.  次に、デザイナーのクリックしてコンボ ボックス、 **Sales Order ID**ラベル。  
  
9. **プロパティ**ウィンドウで、横にあるチェック ボックスを選択、 **IsReadOnly**プロパティ。  
  
## <a name="creating-a-datagrid-that-displays-the-order-details"></a>注文の詳細を表示する DataGrid を作成します。  
 作成、<xref:System.Windows.Controls.DataGrid>をドラッグして、注文の詳細を表示するコントロールを`SalesOrderDetails`からエンティティを**データソース**WPF デザイナーにウィンドウ。  
  
#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>注文の詳細を表示する DataGrid を作成するのには  
  
1.  **データソース**ウィンドウで、検索、 **SalesOrderDetails**ノードの子である、 **[salesorderheaders]** ノード。  
  
    > [!NOTE]
    >  **SalesOrderDetails**のピア ノード、 **[salesorderheaders]** ノード。 子ノードを選択することを確認、 **[salesorderheaders]** ノード。  
  
2.  子展開**SalesOrderDetails**ノード。  
  
3.  次の子ノードの各、 **SalesOrderDetails**ノード、次に、ノードのドロップダウン メニューをクリックし、選択**None**:  
  
    -   **SalesOrderID**  
  
    -   **SalesOrderDetailID**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     この操作によりが Visual Studio でこのデータを含む、<xref:System.Windows.Controls.DataGrid>次の手順で作成するコントロール。 このチュートリアルでは、これらのデータをエンド ユーザーが参照する必要はありません。  
  
4.  **データ ソース**ウィンドウで、子のドラッグ**SalesOrderDetails**ノードでのウィンドウに**WPF デザイナー**します。  
  
     Visual Studio で新しいデータ バインドを定義する XAML が生成される<xref:System.Windows.Controls.DataGrid>コントロール、およびコントロールが、デザイナーに表示されます。 Visual Studio も更新され、生成された`GetSalesOrderHeadersQuery`内のデータを含めるよう分離コード ファイル内のメソッド、 **SalesOrderDetails**エンティティ。  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 ビルドして、注文レコードが表示されることを確認するアプリケーションを実行します。  
  
#### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  **F5**キーを押します。  
  
     アプリケーションがビルドされ、実行されます。 次のことを検証します。  
  
    -   **Sales Order ID**コンボ ボックスが表示されます**71774**します。 これは、エンティティの最初の注文 ID です。  
  
    -   選択した注文ごとに、 **Sales Order ID**コンボ ボックスで、詳細な注文情報に表示されます、<xref:System.Windows.Controls.DataGrid>します。  
  
2.  アプリケーションを終了します。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルを完了すると、使用する方法を説明します、**データ ソース**WPF のバインドを Visual Studio のウィンドウを他の種類のデータ ソースを制御します。 詳細については、次を参照してください。 [WCF data service にコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)と[データセットにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-a-dataset.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータに WPF コントロールをバインドします。](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [WPF アプリケーションで関連データを表示する](../data-tools/display-related-data-in-wpf-applications.md)