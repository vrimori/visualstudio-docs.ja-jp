---
title: 'チュートリアル: 実行時にリボン上のコントロールを更新します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bad52a02cb87f611293283deb3743c6e148e688
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875915"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-runtime"></a>チュートリアル: 実行時にリボン上のコントロールを更新します。

このチュートリアルでは、リボン オブジェクト モデルを使用して、リボンが Office アプリケーションに読み込まれた後、リボン上のコントロールを更新する方法を示します。

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

この例では、Northwind サンプル データベースからデータを取得し、Microsoft Office Outlook のコンボ ボックスとメニューに読み込みます。 自動的にこれらのコントロールで選択したアイテムのようにフィールドを設定する**に**と**サブジェクト**電子メール メッセージ。

このチュートリアルでは、次の作業について説明します。

-   新しい Outlook VSTO アドイン プロジェクトを作成します。

-   カスタム リボン グループを設計します。

-   組み込みタブにカスタム グループを追加します。

-   実行時にリボン上のコントロールを更新します。

> [!NOTE]
> 次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>新しい Outlook VSTO アドイン プロジェクトを作成します。

まず、Outlook VSTO アドイン プロジェクトを作成します。

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>新しい Outlook VSTO アドイン プロジェクトを作成するには

1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、名前の Outlook VSTO アドイン プロジェクトを作成**Ribbon_Update_At_Runtime**します。

2.  **[新しいプロジェクト]** ダイアログ ボックスの **[ソリューションのディレクトリを作成]** チェック ボックスをオンにします。

3.  プロジェクトを既定のプロジェクト ディレクトリに保存します。

     詳細については、「[方法 :Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。

## <a name="design-a-custom-ribbon-group"></a>カスタム リボン グループを設計します。

この例のリボンは、ユーザーが新しいメール メッセージを作成するときに表示されます。 リボンのカスタム グループを作成するには、最初、プロジェクトにリボン項目を追加し、リボン デザイナーでグループを設計し。 このカスタム グループは名前を取得して顧客へのフォロー アップ電子メール メッセージを生成や注文データベースからの履歴に役立ちます。

### <a name="to-design-a-custom-group"></a>カスタム グループをデザインするには

1.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。

2.  **[新しい項目の追加]** ダイアログ ボックスで、 **[リボン (ビジュアル デザイナー)]** をクリックします。

3.  新しいリボンの名前を変更**CustomerRibbon**、 をクリックし、**追加**します。

     *CustomerRibbon.cs*または*CustomerRibbon.vb*ファイルがリボン デザイナーで開き、既定のタブとグループが表示されます。

4.  リボン デザイナーをクリックして選択します。

5.  **プロパティ**ウィンドウで、ドロップダウン矢印をクリックして、 **[ribbontype]** プロパティ、およびクリック**Microsoft.Outlook.Mail.Compose**します。

     これにより、ユーザーが Outlook で新しいメール メッセージを作成するときに表示されるリボンができます。

6.  リボン デザイナーで、クリックして**Group1**をオンにします。

7.  **プロパティ**ウィンドウで、設定**ラベル**に**Customer Purchases**します。

8.  **Office リボン コントロール**のタブ、**ツールボックス**、ドラッグ、 **ComboBox**上に、 **Customer Purchases**グループ。

9. クリックして**ComboBox1**をオンにします。

10. **プロパティ**ウィンドウで、設定**ラベル**に**顧客**します。

11. **Office リボン コントロール**のタブ、**ツールボックス**、ドラッグ、**メニュー**上に、 **Customer Purchases**グループ。

12. **プロパティ**ウィンドウで、設定**ラベル**に**製品を購入**します。

13. 設定**動的**に**true**します。

     これにより、追加し、リボンが Office アプリケーションに読み込まれた後、実行時にメニュー上のコントロールを削除することができます。

## <a name="add-the-custom-group-to-a-built-in-tab"></a>組み込みタブにカスタム グループを追加します。

組み込みタブには、Outlook エクスプ ローラーまたはインスペクターのリボンには既にタブです。 この手順では、組み込みタブにカスタム グループを追加し、タブ上のカスタム グループの位置を指定します。

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>組み込みタブにカスタム グループを追加するには

1.  をクリックして、 **TabAddins (ビルトイン)**  タブを選択します。

2.  **プロパティ**ウィンドウで、展開、 **ControlId**プロパティ、および設定して**OfficeId**に**TabNewMailMessage**します。

     これを追加、 **Customer Purchases**グループに、**メッセージ**新しいメール メッセージに表示されるリボンのタブ。

3.  をクリックして、 **Customer Purchases**グループを選択します。

4.  **プロパティ**ウィンドウで、展開、**位置**プロパティ、ドロップダウン矢印をクリックして、 **PositionType**プロパティ、およびクリック**BeforeOfficeId**します。

5.  設定、 **OfficeId**プロパティを**GroupClipboard**します。

     これを配置、 **Customer Purchases**する前にグループ化、**クリップボード**のグループ、**メッセージ**タブ。

## <a name="create-the-data-source"></a>データ ソースを作成します。

**[データ ソース]** ウィンドウを使用して、型指定されたデータセットをプロジェクトに追加します。

### <a name="to-create-the-data-source"></a>データ ソースを作成するには

1.  **[データ]** メニューの **[新しいデータ ソースの追加]** をクリックします。

     起動、**データ ソース構成ウィザード**します。

2.  選択**データベース**、 をクリックし、**次**。

3.  選択**データセット**、 をクリックし、**次**。

4.  Northwind サンプルの Microsoft SQL Server Compact 4.0 データベースへのデータ接続を選択するかを使用して新しい接続を追加、**新しい接続**ボタンをクリックします。

5.  接続を選択または作成後にをクリックして**次**します。

6.  をクリックして**次**接続文字列に保存します。

7.  **データベース オブジェクトの選択** ページで、展開**テーブル**します。

8.  次の各テーブルの横にあるチェック ボックスをオンにします。

    1.  **顧客**

    2.  **注文の詳細**

    3.  **注文**

    4.  **製品**

9. **[完了]** をクリックします。

## <a name="update-controls-in-the-custom-group-at-runtime"></a>実行時にカスタム グループ内のコントロールを更新します。

リボン オブジェクト モデルを使用して、以下のタスクを実行します。

-   顧客名を追加、**顧客**コンボ ボックス。

-   メニューおよびボタン コントロールを追加、 **Products Purchased**販売の販売注文および製品を表すメニュー。

-   件名、および本文を設定からデータを使用して新しいメール メッセージのフィールド、**顧客**コンボ ボックスと**Products Purchased**メニュー。

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>リボン オブジェクト モデルを使用してカスタム グループのコントロールを更新するには

1. **[プロジェクト]** メニューの **[参照の追加]** をクリックします。

2. **参照の追加**ダイアログ ボックスで、をクリックして、 **.NET** ] タブで、[、 **System.Data.Linq**アセンブリ、およびクリック **[ok]**。

    このアセンブリには、統合言語クエリ (LINQ) を使用するためのクラスが含まれています。 ここでは、LINQ を使用して Northwind データベースから取得したデータをカスタム グループのコントロールに読み込みます。

3. **ソリューション エクスプ ローラー**、 をクリックして**CustomerRibbon.cs**または**CustomerRibbon.vb**をオンにします。

4. **ビュー**  メニューのをクリックして**コード**します。

    コード エディターでリボン コード ファイルが開きます。

5. リボン コード ファイルの先頭に次のステートメントを追加します。 これらのステートメントによって、LINQ 名前空間や Outlook プライマリ相互運用機能アセンブリ (PIA) の名前空間に簡単にアクセスできます。

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. 内の次のコードを追加、`CustomerRibbon`クラス。 このコードは、Northwind データベースの Customer、Orders、Order Details、および Product テーブルから取得した情報を格納するために使用するデータ テーブルおよびテーブル アダプターを宣言します。

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. `CustomerRibbon` クラスに次のコード ブロックを追加します。 このコードは、実行時に、リボンのコントロールを作成する 3 つのヘルパー メソッドを追加します。

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. `CustomerRibbon_Load` イベント ハンドラー メソッドを次のコードで置き換えます。 このコードは、LINQ クエリを使用して以下のタスクを実行します。

   - 設定、**顧客**Northwind データベースの ID と 20 の顧客の名前を使用して、コンボ ボックス。

   - `PopulateSalesOrderInfo` ヘルパー メソッドを呼び出す。 このメソッドは、更新、 **ProductsPurchased**現在選択されている顧客に関連する販売注文番号を持つメニュー。

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. `CustomerRibbon` クラスに次のコードを追加します。 このコードは、LINQ クエリを使用して以下のタスクを実行します。

   - サブメニューに追加します、 **ProductsPurchased**各販売注文のメニューが選択されている顧客に関連します。

   - 販売注文に関連する製品を示すボタンを各サブメニューに追加する。

   - 各ボタンにイベントハンドラーを追加する。

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. **ソリューション エクスプ ローラー**、リボン コード ファイルをダブルクリックします。

     リボン デザイナーが開きます。

11. リボン デザイナーで、ダブルクリック、**顧客**コンボ ボックス。

     リボン コード ファイルがコード エディターで開き、`ComboBox1_TextChanged` イベント ハンドラーが表示されます。

12. `ComboBox1_TextChanged` イベント ハンドラーを次のコードで置き換えます。 このコードは次のタスクを実行します。

    - `PopulateSalesOrderInfo` ヘルパー メソッドを呼び出す。 このメソッドは、更新、 **Products Purchased**選択した顧客に関連する販売注文を含むメニュー。

    - `PopulateMailItem` ヘルパー メソッドを呼び出し、現在のテキスト (つまり、選択されている顧客の名前) を渡します。 このメソッドは、宛先、件名、および本文は設定します。 新しいメール メッセージのフィールド。

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. 次の `Click` イベント ハンドラーを `CustomerRibbon` クラスに追加します。 このコードでは、新しいメール メッセージの本文のフィールドを選択した製品の名前を追加します。

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. `CustomerRibbon` クラスに次のコードを追加します。 このコードは次のタスクを実行します。

    - 現在選択されている顧客の電子メール アドレスを使用して、新しいメール メッセージの行を追加します。

    - 新しいメール メッセージの件名と本文のフィールドにテキストを追加します。

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>カスタム グループのコントロールをテストします。

カスタム グループの名前を Outlook で新しいメール フォームを開くときに**Customer Purchases**に表示される、**メッセージ**リボンのタブ。

カスタマーのフォロー アップ電子メール メッセージを作成するには、顧客を選択し、顧客によって購入された製品を選択します。 内のコントロール、 **Customer Purchases**グループは、Northwind データベースからのデータでの実行時に更新されます。

### <a name="to-test-the-controls-in-the-custom-group"></a>カスタム グループのコントロールをテストするには

1.  キーを押して**F5**プロジェクトを実行します。

     Outlook が起動します。

2.  Outlook では、上、**ファイル**メニューで、**新規**、 をクリックし、**メール メッセージ**。

     次の操作が行われます。

    -   新しいメール メッセージのインスペクター ウィンドウが表示されます。

    -   **メッセージ**、リボンのタブ、 **Customer Purchases**する前にグループが表示されます、**クリップボード**グループ。

    -   **顧客**グループ内のコンボ ボックスが Northwind データベース内の顧客の名前で更新されます。

3.  **メッセージ**リボンのタブで、 **Customer Purchases**グループから顧客を選択して、**顧客**コンボ ボックス。

     次の操作が行われます。

    -   **Products Purchased**メニューが更新され、選択した顧客の各販売注文を表示します。

    -   個々の販売注文サブメニューが、その注文で購入された商品を示すように更新されます。

    -   選択された顧客の電子メール アドレスに追加されます、**に**テキスト メッセージ、および件名とメール メッセージの本文の行が挿入されます。

4.  をクリックして、 **Products Purchases** ] メニューの [任意の販売注文をポイントし、販売注文から製品を順にクリックします。

     製品の名前がメール メッセージの本文に追加されます。

## <a name="next-steps"></a>次の手順

Office UI をカスタマイズする方法の詳細については、次のトピックで説明します。

-   ドキュメント レベルのカスタマイズにコンテキスト ベースの UI を追加する。 詳細については、次を参照してください。[操作ウィンドウの概要](../vsto/actions-pane-overview.md)します。

-   標準またはカスタムの Microsoft Office Outlook フォームを拡張する。 詳細については、「[チュートリアル:Outlook フォーム領域をデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)します。

-   Outlook にカスタム作業ウィンドウを追加する。 詳細については、次を参照してください。[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)します。

## <a name="see-also"></a>関連項目

- [実行時にリボンへのアクセスします。](../vsto/accessing-the-ribbon-at-run-time.md)
- [リボンの概要](../vsto/ribbon-overview.md)
- [統合言語クエリ (LINQ)](/dotnet/csharp/linq/index)
- [方法: リボンのカスタマイズの概要します。](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [リボン デザイナー](../vsto/ribbon-designer.md)
- [チュートリアル: リボン デザイナーを使用してカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [リボン オブジェクト モデルの概要](../vsto/ribbon-object-model-overview.md)
- [Outlook のリボンをカスタマイズします。](../vsto/customizing-a-ribbon-for-outlook.md)
- [方法: リボンのタブの位置を変更します。](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [方法: 組み込みタブをカスタマイズします。](../vsto/how-to-customize-a-built-in-tab.md)
- [方法: Backstage ビューにコントロールを追加します。](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [方法: リボン デザイナーからリボン XML にエクスポートします。](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [方法: アドイン ユーザー インターフェイス エラーを表示します。](../vsto/how-to-show-add-in-user-interface-errors.md)