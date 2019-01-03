---
title: 'チュートリアル: VSTO アドイン プロジェクトでの単純データ バインディング'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: df572f63ec6bb8a77a854144dd2ff4a165148c41
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828421"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>チュートリアル: VSTO アドイン プロジェクトでの単純データ バインディング

VSTO アドイン プロジェクトでは、ホスト コントロールと Windows フォーム コントロールにデータをバインドできます。 このチュートリアルでは、Microsoft Office Word 文書にコントロールを追加し、実行時にデータをコントロールにバインドする方法を示します。

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

このチュートリアルでは、次の作業について説明します。

-   追加、<xref:Microsoft.Office.Tools.Word.ContentControl>実行時にドキュメントにします。

-   コントロールをデータセットのインスタンスに接続する <xref:System.Windows.Forms.BindingSource> を作成する。

-   ユーザーがレコードをスクロールしてレコードをコントロールに表示できるようにする。

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。

-   `AdventureWorksLT` サンプル データベースがアタッチされた SQL Server 2005 または SQL Server 2005 Express の実行中のインスタンスへのアクセス。 ダウンロードすることができます、`AdventureWorksLT`からデータベース、 [CodePlex web サイト](http://go.microsoft.com/fwlink/?LinkId=115611)します。 データベースをアタッチする方法について詳しくは、次のトピックをご覧ください。

    -   データベースをアタッチするには、SQL Server Management Studio または SQL Server Management Studio Express を使用して、参照してください。[方法。データベース (SQL Server Management Studio) をアタッチする](/sql/relational-databases/databases/attach-a-database)します。

    -   コマンドラインを使用してデータベースをアタッチする、次を参照してください。[方法。SQL Server Express データベース ファイルを添付](/previous-versions/sql/)します。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する

まず、Word VSTO アドイン プロジェクトを作成します。

### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには

1.  Visual Basic または C# を使用して、 **Populating Documents from a Database**という名前の Word VSTO アドイン プロジェクトを作成します。

     詳細については、「[方法 :Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。

     Visual Studio を開き、 *ThisAddIn.vb*または*ThisAddIn.cs*ファイルし、追加、 **Populating Documents from データベース**プロジェクトを**ソリューション エクスプ ローラー**.

2.  場合、プロジェクトのターゲット、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]または[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]への参照を追加、 *Microsoft.Office.Tools.Word.v4.0.Utilities.dll*アセンブリ。 この参照は、このチュートリアルの後半でプログラムを使用して Windows フォーム コントロールをドキュメントに追加するのに必要です。

## <a name="create-a-data-source"></a>データ ソースの作成

**[データ ソース]** ウィンドウを使用して、型指定されたデータセットをプロジェクトに追加します。

### <a name="to-add-a-typed-dataset-to-the-project"></a>型指定されたデータセットをプロジェクトに追加するには

1. 場合、**データソース**ウィンドウが表示されない、メニュー バーで 表示することによって、**ビュー** > **その他の Windows**  >  **データ ソース**します。

2. **[新しいデータ ソースの追加]** をクリックして **データ ソース構成ウィザード**を開始します。

3. **[データベース]** をクリックして、 **[次へ]** をクリックします。

4. `AdventureWorksLT` データベースへの既存の接続がある場合は、その接続を選んで **[次へ]** をクリックします。

    それ以外の場合は、 **[新しい接続]** をクリックし、 **[接続の追加]** ダイアログ ボックスを使用して新しい接続を作成します。 詳細については、次を参照してください。[新しい接続を追加](../data-tools/add-new-connections.md)します。

5. **[アプリケーション構成ファイルへの接続文字列を保存]** ページで、 **[次へ]** をクリックします。

6. **[データベース オブジェクトの選択]** ページで、 **[テーブル]** を展開し、 **[Customer (SalesLT)]** を選びます。

7. **[完了]** をクリックします。

    *AdventureWorksLTDataSet.xsd*ファイルに追加されます**ソリューション エクスプ ローラー**します。 このファイルでは、次の項目を定義します。

   - `AdventureWorksLTDataSet`という名前の型指定されたデータセット。 このデータセットは、AdventureWorksLT データベースの **Customer (SalesLT)** テーブルの内容を表します。

   - という名前の TableAdapter`CustomerTableAdapter`します。 この TableAdapter データを読み書きするために使用できます、`AdventureWorksLTDataSet`します。 詳細については、次を参照してください。 [TableAdapter の概要](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)します。

     これらのオブジェクトは、どちらもこのチュートリアルの後半で使用します。

## <a name="create-controls-and-binding-controls-to-data"></a>コントロールとデータ バインド コントロールを作成します。

このチュートリアルでは、データベース レコードを表示するためのインターフェイスは、basic、およびドキュメントの内部の右側に作成されます。 1 つの <xref:Microsoft.Office.Tools.Word.ContentControl> には一度に 1 つのデータベース レコードが表示されます。2 つの <xref:Microsoft.Office.Tools.Word.Controls.Button> コントロールを使用してレコードを前後にスクロールできます。 コンテンツ コントロールは <xref:System.Windows.Forms.BindingSource> を使用して、データベースに接続します。

データ バインド コントロールの詳細については、次を参照してください。 [Office ソリューションでのコントロールにデータをバインド](../vsto/binding-data-to-controls-in-office-solutions.md)します。

### <a name="to-create-the-interface-in-the-document"></a>ドキュメントでインターフェイスを作成するには

1.  `ThisAddIn` クラスで、次のコントロールを宣言し、 `Customer` データベースの `AdventureWorksLTDataSet` テーブルをスクロールして表示できるようにします。

     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]

2.  `ThisAddIn_Startup` メソッドに次のコードを追加し、データセットを初期化して、そのデータセットに `AdventureWorksLTDataSet` データベースから得た情報を設定します。

     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]

3.  `ThisAddIn_Startup` メソッドに次のコードを追加します。 これによりホスト項目が生成され、ドキュメントの機能が拡張されます。 詳細については、次を参照してください。[拡張 Word 文書や Excel ブックを実行時に VSTO アドインで](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)します。

     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]

4.  ドキュメントの先頭でいくつかの範囲を定義します。 これらの範囲は、テキストを挿入し、コントロールを配置する場所を指定します。

     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]

5.  以前に定義された範囲にインターフェイス コントロールを追加します。

     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]

6.  `AdventureWorksLTDataSet` を使用してコンテンツ コントロールを <xref:System.Windows.Forms.BindingSource>にバインドします。 C# 開発者の場合、2 つのイベント ハンドラーを <xref:Microsoft.Office.Tools.Word.Controls.Button> コントロールに追加します。

     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]

7.  データベース レコード間を移動するには、次のコードを追加します。

     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]

## <a name="test-the-add-in"></a>アドインのテストします。

Word を開くと、コンテンツ コントロールに `AdventureWorksLTDataSet` データセットからのデータが表示されます。 **[次へ]** と **[前へ]** ボタンをクリックして、データベース レコードをスクロールします。

### <a name="to-test-the-vsto-add-in"></a>VSTO アドインをテストするには

1.  **F5**キーを押します。

     `customerContentControl` という名前のコンテンツ コントロールが作成され、データが読み込まれます。 同時に、 `adventureWorksLTDataSet` という名前のデータセット オブジェクトと、 <xref:System.Windows.Forms.BindingSource> という名前の `customerBindingSource` がプロジェクトに追加されます。 <xref:Microsoft.Office.Tools.Word.ContentControl> が <xref:System.Windows.Forms.BindingSource>にバインドされ、さらにこれがデータセット オブジェクトにバインドされます。

2.  **[次へ]** ボタンと **[前へ]** ボタンをクリックして、データベース レコードをスクロールします。

## <a name="see-also"></a>関連項目

- [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)
- [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)
- [方法: データベースからデータをワークシートに読み込む](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [方法: データベースからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [方法: サービスからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-services.md)
- [方法: オブジェクトからのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [方法: ワークシート内のデータベース レコードをスクロールします。](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [方法: ホスト コントロールからのデータでデータ ソースを更新します。](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [チュートリアル: ドキュメント レベルのプロジェクトでの単純データ バインディング](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [チュートリアル: ドキュメント レベルのプロジェクトで複合データ バインディング](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Office ソリューションの概要でのローカル データベース ファイルを使用します。](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [新しいデータ ソースの追加](../data-tools/add-new-data-sources.md)
- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [方法: オブジェクトからのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [方法: ホスト コントロールからのデータでデータ ソースを更新します。](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Office ソリューションの概要でのローカル データベース ファイルを使用します。](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource コンポーネントの概要](/dotnet/framework/winforms/controls/bindingsource-component-overview)