---
title: 'チュートリアル: 実行時にリボン コントロールの更新 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 10577f1ca996913ed91f07a7609c59eb9805bced
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-updating-the-controls-on-a-ribbon-at-run-time"></a>チュートリアル : 実行時のリボン コントロールの更新
  このチュートリアルでは、Office アプリケーションにリボンを読み込んだ後でリボン オブジェクト モデルを使用してリボン上のコントロールを更新する方法について説明します。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 この例では、Northwind サンプル データベースからデータを取得し、Microsoft Office Outlook のコンボ ボックスとメニューに読み込みます。 これらのコントロールで自動的に選択したアイテムがなどのフィールドを設定**に**と**サブジェクト**電子メールのメッセージ。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   新しい Outlook VSTO アドイン プロジェクトの作成。  
  
-   カスタム リボン グループのデザイン。  
  
-   組み込みタブへのカスタム グループの追加。  
  
-   実行時のリボン コントロールの更新。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## <a name="creating-a-new-outlook-vsto-add-in-project"></a>新しい Outlook VSTO アドイン プロジェクトの作成  
 まず、Outlook VSTO アドイン プロジェクトを作成します。  
  
#### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>新しい Outlook VSTO アドイン プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、名前の Outlook VSTO アドイン プロジェクトを作成**Ribbon_Update_At_Runtime**です。  
  
2.  **[新しいプロジェクト]** ダイアログ ボックスの **[ソリューションのディレクトリを作成]**チェック ボックスをオンにします。  
  
3.  プロジェクトを既定のプロジェクト ディレクトリに保存します。  
  
     詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
## <a name="designing-a-custom-ribbon-group"></a>カスタム リボン グループのデザイン  
 この例のリボンは、ユーザーが新しいメール メッセージを作成するときに表示されます。 リボンのカスタム グループを作成するには、最初にプロジェクトにリボン項目を追加し、次にリボン デザイナーでグループをデザインします。 このカスタム グループを使用して、データベースから顧客名と注文履歴を取得し、顧客へのフォローアップ電子メール メッセージを作成できます。  
  
#### <a name="to-design-a-custom-group"></a>カスタム グループをデザインするには  
  
1.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
2.  **[新しい項目の追加]** ダイアログ ボックスで、 **[リボン (ビジュアル デザイナー)]**をクリックします。  
  
3.  新しいリボンの名前を変更**CustomerRibbon**、クリックして**追加**です。  
  
     **CustomerRibbon.cs**または**CustomerRibbon.vb**ファイルがリボン デザイナーで開き、既定のタブとグループが表示されます。  
  
4.  リボン デザイナーをクリックして選択します。  
  
5.  **プロパティ**ウィンドウで、横にドロップダウン矢印をクリックして、 **[ribbontype]**プロパティ、およびクリック**[microsoft.outlook.mail.compose]**です。  
  
     これにより、ユーザーが Outlook で新しいメール メッセージを作成するときにリボンが表示されます。  
  
6.  リボン デザイナーでクリックして**Group1**をオンにします。  
  
7.  **プロパティ**ウィンドウで、設定**ラベル**に**Customer Purchases**です。  
  
8.  **Office リボン コントロール**のタブ、**ツールボックス**、ドラッグ、 **ComboBox**上に、 **Customer Purchases**グループ。  
  
9. をクリックして**ComboBox1**をオンにします。  
  
10. **プロパティ**ウィンドウで、設定**ラベル**に**顧客**です。  
  
11. **Office リボン コントロール**のタブ、**ツールボックス**、ドラッグ、**メニュー**上に、 **Customer Purchases**グループ。  
  
12. **プロパティ**ウィンドウで、設定**ラベル**に**製品を購入**です。  
  
13. 設定**動的**に**true**です。  
  
     これにより、実行時にリボンが Office アプリケーションに読み込まれた後で、メニュー上のコントロールを追加および削除できます。  
  
## <a name="adding-the-custom-group-to-a-built-in-tab"></a>組み込みタブへのカスタム グループの追加  
 組み込みタブは、Outlook エクスプローラーまたはインスペクターのリボンに始めから含まれているタブです。 この手順では、組み込みタブにカスタム グループを追加し、タブ上のカスタム グループの位置を指定します。  
  
#### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>組み込みタブにカスタム グループを追加するには  
  
1.  クリックして、 **TabAddins (ビルトイン)**  タブを選択します。  
  
2.  **プロパティ**ウィンドウで、展開、 **ControlId**プロパティ、および設定**OfficeId**に**「tabnewmailmessage」**です。  
  
     これを追加、 **Customer Purchases**グループに、**メッセージ**新しいメール メッセージに表示されるリボンのタブです。  
  
3.  クリックして、 **Customer Purchases**グループを選択します。  
  
4.  **プロパティ**ウィンドウで、展開、**位置**プロパティの横のドロップダウン矢印をクリックして、 **PositionType**プロパティ、およびクリック**[Beforeofficeid]**です。  
  
5.  設定、 **OfficeId**プロパティを**「groupclipboard」**です。  
  
     配置、 **Customer Purchases**する前にグループ化、**クリップボード**のグループ、**メッセージ**タブです。  
  
## <a name="creating-the-data-source"></a>データ ソースの作成  
 **[データ ソース]** ウィンドウを使用して、型指定されたデータセットをプロジェクトに追加します。  
  
#### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1.  **[データ]** メニューの **[新しいデータ ソースの追加]**をクリックします。  
  
     起動、**データ ソース構成ウィザード**です。  
  
2.  選択**データベース**、順にクリック**次**です。  
  
3.  選択**データセット**、順にクリック**次**です。  
  
4.  Northwind サンプルの Microsoft SQL Server Compact 4.0 データベースへのデータ接続を選択するかを使用して新しい接続を追加、**新しい接続**ボタンをクリックします。  
  
5.  接続を選択または作成した後にをクリックして**次**です。  
  
6.  をクリックして**次**を接続文字列を保存します。  
  
7.  **データベース オブジェクトの選択** ページで、展開**テーブル**です。  
  
8.  次の各テーブルの横にあるチェック ボックスをオンにします。  
  
    1.  **顧客**  
  
    2.  **注文の詳細**  
  
    3.  **注文**  
  
    4.  **製品**  
  
9. **[完了]**をクリックします。  
  
## <a name="updating-controls-in-the-custom-group-at-run-time"></a>実行時のカスタム グループ内のコントロールの更新  
 リボン オブジェクト モデルを使用して、以下のタスクを実行します。  
  
-   顧客名を追加、**顧客**コンボ ボックス。  
  
-   メニューおよびボタン コントロールを追加、 **Products Purchased**販売注文および製品を表すメニュー販売します。  
  
-   設定に、件名、および本文からデータを使用して、新しいメール メッセージのフィールド、**顧客**コンボ ボックスと**の製品を購入**メニュー。  
  
#### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>リボン オブジェクト モデルを使用してカスタム グループのコントロールを更新するには  
  
1.  **[プロジェクト]** メニューの **[参照の追加]** をクリックします。  
  
2.  **参照の追加**ダイアログ ボックスで、をクリックして、 **.NET** ] タブで、[、 **System.Data.Linq**アセンブリ、およびクリック**[ok]**です。  
  
     このアセンブリには、統合言語クエリ (LINQ) を使用するためのクラスが含まれています。 ここでは、LINQ を使用して Northwind データベースから取得したデータをカスタム グループのコントロールに読み込みます。  
  
3.  **ソリューション エクスプ ローラー**をクリックして**CustomerRibbon.cs**または**CustomerRibbon.vb**をオンにします。  
  
4.  **ビュー**  メニューのをクリックして**コード**です。  
  
     コード エディターでリボン コード ファイルが開きます。  
  
5.  リボン コード ファイルの先頭に次のステートメントを追加します。 これらのステートメントによって、LINQ 名前空間や Outlook プライマリ相互運用機能アセンブリ (PIA) の名前空間に簡単にアクセスできます。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]  
  
6.  CustomerRibbon クラス内に次のコードを追加します。 このコードは、Northwind データベースの Customer、Orders、Order Details、および Product テーブルから取得した情報を格納するために使用するデータ テーブルおよびテーブル アダプターを宣言します。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]  
  
7.  `CustomerRibbon` クラスに次のコード ブロックを追加します。 このコードは、実行時にリボンのコントロールを作成する 3 つのヘルパー メソッドを追加します。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]  
  
8.  `CustomerRibbon_Load` イベント ハンドラー メソッドを次のコードで置き換えます。 このコードは、LINQ クエリを使用して以下のタスクを実行します。  
  
    -   追加、**顧客**Northwind データベースの ID と 20 の顧客の名前を使用して、コンボ ボックス。  
  
    -   `PopulateSalesOrderInfo` ヘルパー メソッドを呼び出す。 このメソッドは、更新、 **ProductsPurchased**メニューには、現在選択されている顧客に関連する販売注文番号。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]  
  
9. `CustomerRibbon` クラスに次のコードを追加します。 このコードは、LINQ クエリを使用して以下のタスクを実行します。  
  
    -   サブメニューを追加、 **ProductsPurchased**選択した顧客に関連する販売注文ごとにメニュー。  
  
    -   販売注文に関連する製品を示すボタンを各サブメニューに追加する。  
  
    -   各ボタンにイベントハンドラーを追加する。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]  
  
10. **ソリューション エクスプ ローラー**、リボン コード ファイルをダブルクリックします。  
  
     リボン デザイナーが開きます。  
  
11. リボン デザイナーで、ダブルクリック、**顧客**コンボ ボックス。  
  
     リボン コード ファイルがコード エディターで開き、`ComboBox1_TextChanged` イベント ハンドラーが表示されます。  
  
12. `ComboBox1_TextChanged` イベント ハンドラーを次のコードで置き換えます。 このコードは次のタスクを実行します。  
  
    -   `PopulateSalesOrderInfo` ヘルパー メソッドを呼び出す。 このメソッドは、更新、 **Products Purchased**メニューには、選択した顧客に関連する販売注文します。  
  
    -   `PopulateMailItem` ヘルパー メソッドを呼び出し、現在のテキスト (つまり、選択されている顧客の名前) を渡します。 このメソッドに、件名、および本文を作成する新しいメール メッセージのフィールドです。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]  
  
13. `CustomerRibbon` クラスに以下の Click イベント ハンドラーを追加します。 このコードは、新しいメール メッセージの本文 フィールドに、選択した製品の名前を追加します。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]  
  
14. `CustomerRibbon` クラスに次のコードを追加します。 このコードは次のタスクを実行します。  
  
    -   現在選択されている顧客の電子メール アドレスを使用して、新しいメール メッセージの宛先行を追加します。  
  
    -   新しいメール メッセージの件名と本文のフィールドにテキストを追加します。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]  
  
## <a name="testing-the-controls-in-the-custom-group"></a>カスタム グループのコントロールのテスト  
 Outlook でメールに新しいフォームを開くときにカスタムという名前のグループ**Customer Purchases**に表示されます、**メッセージ**リボンのタブです。  
  
 顧客へのフォローアップ電子メール メッセージを作成するには、顧客を選択し、その顧客が購入した製品を選択します。 内のコントロール、 **Customer Purchases**グループは、Northwind データベースからのデータでの実行時に更新されます。  
  
#### <a name="to-test-the-controls-in-the-custom-group"></a>カスタム グループのコントロールをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
     Outlook が起動します。  
  
2.  Outlook では、上、**ファイル** メニューのをポイント**新規**、クリックして**メール メッセージ**です。  
  
     次の操作が行われます。  
  
    -   新しいメール メッセージのインスペクター ウィンドウが表示されます。  
  
    -   **メッセージ**、リボンのタブ、 **Customer Purchases**前にグループが表示されます、**クリップボード**グループ。  
  
    -   **顧客**グループ内のコンボ ボックスが Northwind データベース内の顧客の名前で更新します。  
  
3.  **メッセージ**リボンのタブで、 **Customer Purchases**グループから顧客を選択して、**顧客**コンボ ボックス。  
  
     次の操作が行われます。  
  
    -   **Products Purchased**メニューが更新され、選択した顧客の各販売注文を表示します。  
  
    -   個々の販売注文サブメニューが、その注文で購入された商品を示すように更新されます。  
  
    -   選択した顧客の電子メール アドレスに追加、**に**テキスト メッセージ、および件名とメール メッセージの本文の行が挿入されます。  
  
4.  クリックして、 **Products Purchases** ] メニューの [任意の販売注文をポイントし、販売注文から製品を順にクリックします。  
  
     製品の名前がメール メッセージの本文に追加されます。  
  
## <a name="next-steps"></a>次の手順  
 Office UI をカスタマイズする方法の詳細については、次のトピックで説明します。  
  
-   ドキュメント レベルのカスタマイズにコンテキスト ベースの UI を追加する。 詳細については、「 [Actions Pane Overview](../vsto/actions-pane-overview.md)」を参照してください。  
  
-   標準またはカスタムの Microsoft Office Outlook フォームを拡張する。 詳細については、次を参照してください。[チュートリアル: Outlook フォーム領域のデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)です。  
  
-   Outlook にカスタム作業ウィンドウを追加する。 詳細については、次を参照してください。[カスタム作業ウィンドウの](../vsto/custom-task-panes.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [リボンの概要](../vsto/ribbon-overview.md)   
 [統合言語クエリ (LINQ)](/dotnet/csharp/linq/index)   
 [方法: リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [チュートリアル: リボン デザイナーを使用してカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [リボン オブジェクト モデルの概要](../vsto/ribbon-object-model-overview.md)   
 [Outlook のリボンのカスタマイズ](../vsto/customizing-a-ribbon-for-outlook.md)   
 [方法: リボンのタブの位置を変更](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [方法: 組み込みタブをカスタマイズします。](../vsto/how-to-customize-a-built-in-tab.md)   
 [方法: コントロール Backstage ビューを追加します。](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [方法: リボン デザイナーからリボン XML にエクスポート](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [方法: アドインのユーザー インターフェイス エラーを表示する](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  