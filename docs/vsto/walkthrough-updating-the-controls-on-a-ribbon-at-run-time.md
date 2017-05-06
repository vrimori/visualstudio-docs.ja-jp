---
title: "チュートリアル : 実行時のリボン コントロールの更新"
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
helpviewer_keywords: 
  - "コントロール [Visual Studio での Office 開発], リボン"
  - "動的メニュー [Visual Studio での Office 開発]"
  - "リボン [Visual Studio での Office 開発], コントロール"
  - "リボン [Visual Studio での Office 開発], 動的メニュー"
  - "リボン [Visual Studio での Office 開発], 更新"
  - "更新 (リボン コントロールを)"
ms.assetid: ed80790f-3f95-47e4-8a41-872588a8ca07
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# チュートリアル : 実行時のリボン コントロールの更新
  このチュートリアルでは、Office アプリケーションにリボンを読み込んだ後でリボン オブジェクト モデルを使用してリボン上のコントロールを更新する方法について説明します。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 この例では、Northwind サンプル データベースからデータを取得し、Microsoft Office Outlook のコンボ ボックスとメニューに読み込みます。  これらのコントロールで選択した項目は、電子メール メッセージの**宛先**や**件名**などのフィールドに自動的に読み込まれます。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   新しい Outlook VSTO アドイン プロジェクトの作成。  
  
-   カスタム リボン グループのデザイン。  
  
-   組み込みタブへのカスタム グループの追加。  
  
-   実行時のリボン コントロールの更新。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## 新しい Outlook VSTO アドイン プロジェクトの作成  
 まず、Outlook VSTO アドイン プロジェクトを作成します。  
  
#### 新しい Outlook VSTO アドイン プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で、Ribbon\_Update\_At\_Runtime という名前の Outlook VSTO アドイン プロジェクトを作成します。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスの **\[ソリューションのディレクトリを作成\]** チェック ボックスをオンにします。  
  
3.  プロジェクトを既定のプロジェクト ディレクトリに保存します。  
  
     詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
## カスタム リボン グループのデザイン  
 この例のリボンは、ユーザーが新しいメール メッセージを作成するときに表示されます。  リボンのカスタム グループを作成するには、最初にプロジェクトにリボン項目を追加し、次にリボン デザイナーでグループをデザインします。  このカスタム グループを使用して、データベースから顧客名と注文履歴を取得し、顧客へのフォローアップ電子メール メッセージを作成できます。  
  
#### カスタム グループをデザインするには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[リボン \(ビジュアル デザイナー\)\]** をクリックします。  
  
3.  新しいリボンの名前を「**CustomerRibbon**」に変更し、**\[追加\]** をクリックします。  
  
     リボン デザイナーで **CustomerRibbon.cs** ファイルまたは **CustomerRibbon.vb** ファイルが開き、既定のタブとグループが表示されます。  
  
4.  リボン デザイナーをクリックして選択します。  
  
5.  **\[プロパティ\]** ウィンドウで、**\[RibbonType\]** プロパティの隣のドロップダウン矢印をクリックし、**\[Microsoft.Outlook.Mail.Compose\]** をクリックします。  
  
     これにより、ユーザーが Outlook で新しいメール メッセージを作成するときにリボンが表示されます。  
  
6.  リボン デザイナーで、**\[Group1\]** をクリックして選択します。  
  
7.  **\[プロパティ\]** ウィンドウで、**\[ラベル\]** を「Customer Purchases」に設定します。  
  
8.  **\[ツールボックス\]** の **\[Office リボン コントロール\]** タブから **\[ComboBox\]** を **\[Customer Purchases\]** グループにドラッグします。  
  
9. **\[ComboBox1\]** をクリックして選択します。  
  
10. **\[プロパティ\]** ウィンドウで、**\[ラベル\]** を「Customers」に設定します。  
  
11. **\[ツールボックス\]** の **\[Office リボン コントロール\]** タブから **\[Menu\]** を **\[Customer Purchases\]** グループにドラッグします。  
  
12. **\[プロパティ\]** ウィンドウで、**\[ラベル\]** を「Product Purchased」に設定します。  
  
13. **\[ダイナミック\]** を **true** に設定します。  
  
     これにより、実行時にリボンが Office アプリケーションに読み込まれた後で、メニュー上のコントロールを追加および削除できます。  
  
## 組み込みタブへのカスタム グループの追加  
 組み込みタブは、Outlook エクスプローラーまたはインスペクターのリボンに始めから含まれているタブです。  この手順では、組み込みタブにカスタム グループを追加し、タブ上のカスタム グループの位置を指定します。  
  
#### 組み込みタブにカスタム グループを追加するには  
  
1.  **\[TabAddins \(ビルトイン\)\]** タブをクリックして選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、**\[ControlId\]** プロパティを展開し、**\[OfficeId\]** を「TabNewMailMessage」に設定します。  
  
     これにより、**\[Customer Purchases\]** グループが新しいメール メッセージ内に表示されるリボンの **\[Messages\]** タブに追加されます。  
  
3.  **\[Customer Purchases\]** グループをクリックして選択します。  
  
4.  **\[プロパティ\]** ウィンドウで、**\[位置\]** プロパティを展開し、**\[PositionType\]** プロパティの隣にあるドロップダウン矢印をクリックして **\[BeforeOfficeId\]** をクリックします。  
  
5.  **\[OfficeId\]** プロパティを「GroupClipboard」に設定します。  
  
     これにより、**\[Customer Purchases\]** グループが **\[Messages\]** タブの **\[Clipboard\]** グループの前に配置されます。  
  
## データ ソースの作成  
 **\[データ ソース\]** ウィンドウを使用して、型指定されたデータセットをプロジェクトに追加します。  
  
#### データ ソースを作成するには  
  
1.  **\[データ\]** メニューの **\[新しいデータ ソースの追加\]** をクリックします。  
  
     これにより、**データ ソース構成ウィザード**が開始されます。  
  
2.  **\[データベース\]** を選択し、**\[次へ\]** をクリックします。  
  
3.  **\[データセット\]** を選択し、**\[次へ\]** をクリックします。  
  
4.  Microsoft SQL Server Compact 4.0 の Northwind サンプル データベースへのデータ接続を選択するか、または **\[新しい接続\]** ボタンをクリックして新しい接続を追加します。  
  
5.  接続を選択または作成した後で、**\[次へ\]** をクリックします。  
  
6.  **\[次へ\]** をクリックして接続文字列を保存します。  
  
7.  **\[データベース オブジェクトの選択\]** ページの **\[テーブル\]** を展開します。  
  
8.  次の各テーブルの横にあるチェック ボックスをオンにします。  
  
    1.  **Customers**  
  
    2.  **注文の詳細**  
  
    3.  **Orders**  
  
    4.  **製品**  
  
9. **\[完了\]** をクリックします。  
  
## 実行時のカスタム グループ内のコントロールの更新  
 リボン オブジェクト モデルを使用して、以下のタスクを実行します。  
  
-   **\[Customers\]** コンボ ボックスに顧客名を追加する。  
  
-   **\[Products Purchased\]** メニューに、販売注文と販売済み製品を表すメニュー コントロールおよびボタン コントロールを追加する。  
  
-   **\[Customers\]** コンボ ボックスと **\[Products Purchased\]** メニューのデータを使用して、新しいメール メッセージの To、Subject、および Body フィールドを設定する。  
  
#### リボン オブジェクト モデルを使用してカスタム グループのコントロールを更新するには  
  
1.  **\[プロジェクト\]** メニューの **\[参照の追加\]** をクリックします。  
  
2.  **\[参照の追加\]** ダイアログ ボックスで、**\[.NET\]** をクリックし、**System.Data.Linq** アセンブリを選択して **\[OK\]** をクリックします。  
  
     このアセンブリには、統合言語クエリ \(LINQ\) を使用するためのクラスが含まれています。  ここでは、LINQ を使用して Northwind データベースから取得したデータをカスタム グループのコントロールに読み込みます。  
  
3.  **ソリューション エクスプローラー**で、**CustomerRibbon.cs** または **CustomerRibbon.vb** をクリックして選択します。  
  
4.  **\[表示\]** メニューの **\[コード\]** をクリックします。  
  
     コード エディターでリボン コード ファイルが開きます。  
  
5.  リボン コード ファイルの先頭に次のステートメントを追加します。  これらのステートメントによって、LINQ 名前空間や Outlook プライマリ相互運用機能アセンブリ \(PIA\) の名前空間に簡単にアクセスできます。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#1)]  
  
6.  CustomerRibbon クラス内に次のコードを追加します。  このコードは、Northwind データベースの Customer、Orders、Order Details、および Product テーブルから取得した情報を格納するために使用するデータ テーブルおよびテーブル アダプターを宣言します。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#2)]  
  
7.  `CustomerRibbon` クラスに次のコード ブロックを追加します。  このコードは、実行時にリボンのコントロールを作成する 3 つのヘルパー メソッドを追加します。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#3)]  
  
8.  `CustomerRibbon_Load` イベント ハンドラー メソッドを次のコードで置き換えます。  このコードは、LINQ クエリを使用して以下のタスクを実行します。  
  
    -   Northwind データベースに登録されている 20 件の顧客の ID と名前を使用して **\[Customers\]** コンボ ボックスを設定する。  
  
    -   `PopulateSalesOrderInfo` ヘルパー メソッドを呼び出す。  このメソッドは、現在選択されている顧客に関連する販売注文番号を使用して **\[Products Purchased\]** メニューを更新します。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#4)]  
  
9. `CustomerRibbon` クラスに次のコードを追加します。  このコードは、LINQ クエリを使用して以下のタスクを実行します。  
  
    -   選択されている顧客に関連する個々の販売注文を示すサブメニューを **\[Products Purchased\]** メニューに追加する。  
  
    -   販売注文に関連する製品を示すボタンを各サブメニューに追加する。  
  
    -   各ボタンにイベントハンドラーを追加する。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#6)]  
  
10. **ソリューション エクスプローラー**でリボン コード ファイルをダブルクリックします。  
  
     リボン デザイナーが開きます。  
  
11. リボン デザイナーで **\[Customers\]** コンボ ボックスをダブルクリックします。  
  
     リボン コード ファイルがコード エディターで開き、`ComboBox1_TextChanged` イベント ハンドラーが表示されます。  
  
12. `ComboBox1_TextChanged` イベント ハンドラーを次のコードで置き換えます。  このコードは次のタスクを実行します。  
  
    -   `PopulateSalesOrderInfo` ヘルパー メソッドを呼び出す。  このメソッドは、選択されている顧客に関連する販売注文を使用して **\[Products Purchased\]** メニューを更新します。  
  
    -   `PopulateMailItem` ヘルパー メソッドを呼び出し、現在のテキスト \(つまり、選択されている顧客の名前\) を渡します。  このメソッドは、新しいメール メッセージの To、Subject、および Body フィールドにデータを読み込みます。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#5)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#5)]  
  
13. `CustomerRibbon` クラスに以下の Click イベント ハンドラーを追加します。  このコードは、選択された製品の名前を新しいメール メッセージの Body フィールドに追加します。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#8)]  
  
14. `CustomerRibbon` クラスに次のコードを追加します。  このコードは次のタスクを実行します。  
  
    -   現在選択されている顧客の電子メール アドレスを使用して、新しいメール メッセージの To 行を設定する。  
  
    -   新しいメール メッセージの Subject および Body フィールドにテキストを追加する。  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#7)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#7)]  
  
## カスタム グループのコントロールのテスト  
 Outlook で新しいメールを開くと、リボンの **\[Messages\]** タブに **\[Customer Purchases\]** というカスタム グループが表示されます。  
  
 顧客へのフォローアップ電子メール メッセージを作成するには、顧客を選択し、その顧客が購入した製品を選択します。  **\[Customer Purchases\]** グループ内のコントロールが、実行時に Northwind データベースから取得されたデータで更新されます。  
  
#### カスタム グループのコントロールをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
     Outlook が起動します。  
  
2.  Outlook で、**\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[メール メッセージ\]** をクリックします。  
  
     次の処理が実行されます。  
  
    -   新しいメール メッセージのインスペクター ウィンドウが表示されます。  
  
    -   リボンの **\[Message\]** タブに含まれる **\[Clipboard\]** グループの前に **\[Customer Purchases\]** グループが表示されます。  
  
    -   そのグループ内の **\[Customers\]** コンボ ボックスが Northwind データベースに含まれる顧客の名前で更新されます。  
  
3.  リボンの **\[Message\]** タブの **\[Customer Purchases\]** グループで、**\[Customers\]** コンボ ボックスから顧客を選択します。  
  
     次の処理が実行されます。  
  
    -   **\[Products Purchased\]** メニューが、選択されている顧客の個々の販売注文を示すように更新されます。  
  
    -   個々の販売注文サブメニューが、その注文で購入された商品を示すように更新されます。  
  
    -   選択されている顧客の電子メール アドレスがメール メッセージの**宛先**行に追加され、メール メッセージの件名と本文にテキストが読み込まれます。  
  
4.  **\[Products Purchased\]** メニューをクリックし、いずれかの販売注文をポイントして、その販売注文に含まれる製品をクリックします。  
  
     製品の名前がメール メッセージの本文に追加されます。  
  
## 次の手順  
 Office UI をカスタマイズする方法の詳細については、次のトピックで説明します。  
  
-   ドキュメント レベルのカスタマイズにコンテキスト ベースの UI を追加する。  詳細については、「[操作ウィンドウの概要](../vsto/actions-pane-overview.md)」を参照してください。  
  
-   標準またはカスタムの Microsoft Office Outlook フォームを拡張する。  詳細については、「[チュートリアル : Outlook フォーム領域のデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)」を参照してください。  
  
-   Outlook にカスタム作業ウィンドウを追加する。  詳細については、「[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)」を参照してください。  
  
## 参照  
 [実行時のリボンへのアクセス](../vsto/accessing-the-ribbon-at-run-time.md)   
 [リボンの概要](../vsto/ribbon-overview.md)   
 [統合言語クエリ \(LINQ\)](../Topic/LINQ%20(Language-Integrated%20Query).md)   
 [方法 : リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [チュートリアル : リボン デザイナーを使用したカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [リボン オブジェクト モデルの概要](../vsto/ribbon-object-model-overview.md)   
 [Outlook のリボンのカスタマイズ](../vsto/customizing-a-ribbon-for-outlook.md)   
 [方法: リボンのタブの位置を変更する](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [方法 : 組み込みタブをカスタマイズする](../vsto/how-to-customize-a-built-in-tab.md)   
 [方法: Backstage ビューにコントロールを追加する](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [方法 : リボンをリボン デザイナーからリボン XML にエクスポートする](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [方法 : アドインのユーザー インターフェイス エラーを表示する](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  