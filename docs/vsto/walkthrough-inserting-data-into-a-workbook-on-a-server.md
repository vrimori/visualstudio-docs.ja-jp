---
title: 'チュートリアル: サーバー上のブックにデータを挿入します。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
- workbooks [Office development in Visual Studio], inserting data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: db3bf8cbb205a76b414091b401de7e48c5c96a38
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758948"
---
# <a name="walkthrough-insert-data-into-a-workbook-on-a-server"></a>チュートリアル: サーバー上のブックにデータを挿入します。
  このチュートリアルを使用して起動することがなく、Microsoft Office Excel ブックにキャッシュされているデータセットにデータを挿入する方法、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラス。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 このチュートリアルでは、次の作業について説明します。

-   AdventureWorksLT データベースからデータを含むデータセットを定義します。

-   Excel ブック プロジェクトと、コンソール アプリケーション プロジェクトで、データセットのインスタンスを作成しています。

-   作成、<xref:Microsoft.Office.Tools.Excel.ListObject>ブック内のデータセットにバインドされています。

-   ブックのデータ キャッシュにデータセットを追加します。

-   起動することがなく、コンソール アプリケーションでコードを実行して、キャッシュされたデータセットにデータを挿入します。

 このチュートリアルでは、開発用コンピューターに、コードを実行していることを前提としていますが、Excel がインストールされていないサーバーでこのチュートリアルで示されるコードを使用できます。

> [!NOTE]
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

## <a name="prerequisites"></a>前提条件
 このチュートリアルを実行するには、次のコンポーネントが必要です。

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

-   Microsoft SQL Server または AdventureWorksLT サンプル データベースがアタッチされている Microsoft SQL Server Express の実行中のインスタンスへのアクセス。 AdventureWorksLT データベースをダウンロードすることができます、 [CodePlex web サイト](http://go.microsoft.com/fwlink/?linkid=87843)します。 データベースをアタッチする方法について詳しくは、次のトピックをご覧ください。

    -   データベースをアタッチするには、SQL Server Management Studio または SQL Server Management Studio Express を使用して、参照してください。[方法: データベース (SQL Server Management Studio) をアタッチする](http://msdn.microsoft.com/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa)します。

    -   コマンドラインを使用してデータベースをアタッチする、次を参照してください。[方法: SQL Server Express データベース ファイルを添付](http://msdn.microsoft.com/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68)。

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>データセットを定義するクラス ライブラリ プロジェクトを作成します。
 Excel ブック プロジェクトと、コンソール アプリケーションで同じデータセットを使用するには、これらのプロジェクトの両方で参照されている別のアセンブリにデータセットを定義する必要があります。 このチュートリアルでは、クラス ライブラリ プロジェクトで、データセットを定義します。

### <a name="to-create-the-class-library-project"></a>クラス ライブラリ プロジェクトを作成するには

1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。

2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

3.  展開テンプレート ペインで**Visual c#** または**Visual Basic**、 をクリックし、 **Windows**します。

4.  プロジェクト テンプレートの一覧で選択**クラス ライブラリ**します。

5.  **名前**ボックスに「 **AdventureWorksDataSet**します。

6.  をクリックして**参照**に移動し、 *%UserProfile%\My Documents* (for Windows XP 以降) または *%UserProfile%\Documents* (Windows Vista) のフォルダー、および順にクリックします**フォルダーを選択します**します。

7.  **新しいプロジェクト** ダイアログ ボックスでは必ず、**ソリューションのディレクトリを作成** チェック ボックスが選択されていません。

8.  **[OK]** をクリックします。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **AdventureWorksDataSet**プロジェクトを**ソリューション エクスプ ローラー**開くと、 **Class1.cs**または**Class1.vb**コード ファイル。

9. **ソリューション エクスプ ローラー**を右クリックして**Class1.cs**または**Class1.vb**、 をクリックし、**削除**します。 このチュートリアルのこのファイルが不要です。

## <a name="define-a-dataset-in-the-class-library-project"></a>クラス ライブラリ プロジェクトでデータセットを定義します。
 SQL Server 2005 用の AdventureWorksLT データベースからデータを含む型指定されたデータセットを定義します。 このチュートリアルの後半では、Excel ブック プロジェクトと、コンソール アプリケーション プロジェクトからこのデータセットを参照します。

 データセットが、*型指定された dataset* AdventureWorksLT データベースの Product テーブル内のデータを表します。 型指定されたデータセットの詳細については、次を参照してください。 [Visual Studio でのデータセット ツール](/visualstudio/data-tools/dataset-tools-in-visual-studio)します。

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>クラス ライブラリ プロジェクトで指定されたデータセットを定義するには

1.  **ソリューション エクスプ ローラー**、クリックして、 **AdventureWorksDataSet**プロジェクト。

2.  場合、**データソース**ウィンドウが表示されない、メニュー バーで 表示することによって、**ビュー** > **その他の Windows**  >  **データ ソース**します。

3.  **[新しいデータ ソースの追加]** をクリックして **データ ソース構成ウィザード**を開始します。

4.  **[データベース]** をクリックして、 **[次へ]** をクリックします。

5.  AdventureWorksLT データベースに既存の接続があれば、この接続を選択し、をクリックして**次**します。

     それ以外の場合は、 **[新しい接続]** をクリックし、 **[接続の追加]** ダイアログ ボックスを使用して新しい接続を作成します。 詳細については、次を参照してください。[方法: データをデータベースに接続する](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)します。

6.  **[アプリケーション構成ファイルへの接続文字列を保存]** ページで、 **[次へ]** をクリックします。

7.  **データベース オブジェクトの選択** ページで、展開**テーブル**選択**Product (SalesLT)** します。

8.  **[完了]** をクリックします。

     *AdventureWorksLTDataSet.xsd*ファイルに追加されます、 **AdventureWorksDataSet**プロジェクト。 このファイルでは、次の項目を定義します。

    -   `AdventureWorksLTDataSet`という名前の型指定されたデータセット。 このデータセットは、AdventureWorksLT データベースの Product テーブルの内容を表します。

    -   という名前の TableAdapter`ProductTableAdapter`します。 この TableAdapter データを読み書きするために使用できます、`AdventureWorksLTDataSet`します。 詳細については、次を参照してください。 [TableAdapter の概要](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)します。

     これらのオブジェクトは、どちらもこのチュートリアルの後半で使用します。

9. **ソリューション エクスプ ローラー**を右クリックして**AdventureWorksDataSet**クリック**ビルド**。

     プロジェクトのビルドでエラーが発生しないことを確認します。

## <a name="create-an-excel-workbook-project"></a>Excel ブック プロジェクトを作成します。
 データへのインターフェイスの Excel ブック プロジェクトを作成します。 作成するが、このチュートリアルの後半で、<xref:Microsoft.Office.Tools.Excel.ListObject>データを表示して、ブック内のデータ キャッシュに、データセットのインスタンスが追加されます。

### <a name="to-create-the-excel-workbook-project"></a>Excel ブック プロジェクトを作成するには

1.  **ソリューション エクスプ ローラー**を右クリックし、 **AdventureWorksDataSet**ソリューション、 をポイント**追加**、 をクリックし、**新しいプロジェクト**します。

2.  テンプレート ペインで、 **[Visual C#]** または **[Visual Basic]** を展開してから、 **[Office/SharePoint]** を展開します。

3.  展開した **[Office/SharePoint]** ノードの下で、 **[Office Add-ins]** ノードを選択します。

4.  プロジェクト テンプレートのリストで、 **[Excel 2010 ブック]** または **[Excel 2013 ブック]** プロジェクトを選択します。

5.  **名前**ボックスに「 **AdventureWorksReport**します。 場所を変更しないでください。

6.  **[OK]** をクリックします。

     **Visual Studio Tools for Office プロジェクト ウィザード** が開きます。

7.  いることを確認**新しい文書を作成**が選択されているし、をクリックして**OK**します。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 表示されます、 **AdventureWorksReport**デザイナーでブックを追加し、 **AdventureWorksReport**プロジェクトを**ソリューション エクスプ ローラー**します。

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Excel ブック プロジェクトのデータ ソースにデータセットを追加します。
 データセットを表示するには、Excel ブックで、前に、Excel ブック プロジェクトのデータ ソースにデータセットを追加する必要があります。

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Excel ブック プロジェクトのデータ ソースにデータセットを追加するには

1.  **ソリューション エクスプ ローラー**、ダブルクリックして**Sheet1.cs**または**Sheet1.vb**下、 **AdventureWorksReport**プロジェクト。

     ブックがデザイナーで開きます。

2.  **[データ]** メニューの **[新しいデータ ソースの追加]** をクリックします。

     **データ ソース構成ウィザード**が開きます。

3.  クリックして**オブジェクト**、順にクリックします**次**します。

4.  **オブジェクトを選択するバインド** ページで、をクリックする**参照の追加**します。

5.  **プロジェクト**] タブで [ **AdventureWorksDataSet**順にクリックします**OK**。

6.  下、 **AdventureWorksDataSet**の名前空間、 **AdventureWorksDataSet**アセンブリ、 をクリックして**AdventureWorksLTDataSet**順にクリックします**完了**.

     **データソース**ウィンドウが開いたら、および**AdventureWorksLTDataSet**データ ソースの一覧に追加されます。

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>データセットのインスタンスにバインドされた listobject コントロールを作成します。
 ブックでは、データセットを表示するには、作成、<xref:Microsoft.Office.Tools.Excel.ListObject>データセットのインスタンスにバインドされています。 データ バインド コントロールの詳細については、次を参照してください。 [Office ソリューションでのコントロールにデータをバインド](../vsto/binding-data-to-controls-in-office-solutions.md)します。

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>データセットのインスタンスにバインドされた listobject コントロールを作成するには

1.  **データソース**ウィンドウで、展開、 **AdventureWorksLTDataSet**ノードの下**AdventureWorksDataSet**します。

2.  選択、**製品**ノードを選択し、表示されるドロップダウン矢印をクリックします。 **ListObject**ドロップダウン リストでします。

     ドロップダウン矢印が表示されない場合は、ブックがデザイナーで開いていることを確認します。

3.  ドラッグ、**製品**テーブルのセル A1 にします。

     A<xref:Microsoft.Office.Tools.Excel.ListObject>という名前のコントロール`productListObject`セル A1 から始まる、ワークシート上に作成されます。 同時、という名前のデータセット オブジェクト`adventureWorksLTDataSet`と<xref:System.Windows.Forms.BindingSource>という`productBindingSource`プロジェクトに追加されます。 <xref:Microsoft.Office.Tools.Excel.ListObject> が <xref:System.Windows.Forms.BindingSource>にバインドされ、さらにこれがデータセット オブジェクトにバインドされます。

## <a name="add-the-dataset-to-the-data-cache"></a>データ キャッシュにデータセットを追加します。
 ブック内のデータセットにアクセスする Excel ブック プロジェクトの外側のコードを有効にするには、データ キャッシュにデータセットを追加する必要があります。 データ キャッシュの詳細については、次を参照してください。[ドキュメント レベルのカスタマイズでキャッシュされたデータ](../vsto/cached-data-in-document-level-customizations.md)と[データ キャッシュ](../vsto/caching-data.md)します。

### <a name="to-add-the-dataset-to-the-data-cache"></a>データ キャッシュにデータセットを追加するには

1.  デザイナーで、次のようにクリックします。 **adventureWorksLTDataSet**します。

2.  **プロパティ**ウィンドウで、設定、**修飾子**プロパティを**パブリック**します。

3.  設定、 **CacheInDocument**プロパティを**True**します。

## <a name="checkpoint"></a>チェックポイント
 ビルドおよびコンパイルして、エラーなく実行できることを確認します。 Excel ブック プロジェクトを実行します。

### <a name="to-build-and-run-the-project"></a>プロジェクトをビルドして実行するには

1.  **ソリューション エクスプ ローラー**を右クリックし、 **AdventureWorksReport**プロジェクトで、選択**デバッグ**、 をクリックし、**新しいインスタンスを開始**します。

     プロジェクトをビルドし、ブックが Excel で開きます。 <xref:Microsoft.Office.Tools.Excel.ListObject>で**Sheet1**が空、ため、`adventureWorksLTDataSet`データ キャッシュ内のオブジェクトはまだありませんデータ。 次のセクションでは、設定するコンソール アプリケーションを使用します、`adventureWorksLTDataSet`データを持つオブジェクト。

2.  Excel を終了します。 変更を保存できません。

## <a name="create-a-console-application-project"></a>コンソール アプリケーション プロジェクトを作成します。
 使用してブックのキャッシュされたデータセットにデータを挿入するコンソール アプリケーション プロジェクトを作成します。

### <a name="to-create-the-console-application-project"></a>コンソール アプリケーション プロジェクトを作成するには

1.  **ソリューション エクスプ ローラー**を右クリックし、 **AdventureWorksDataSet**ソリューション、 をポイント**追加**、 をクリックし、**新しいプロジェクト**します。

2.  **プロジェクトの種類**ウィンドウで、展開**Visual c#** または**Visual Basic**、 をクリックし、 **Windows**します。

3.  **テンプレート**ペインで、**コンソール アプリケーション**します。

4.  **名前**ボックスに「 **datawriter の各**します。 場所を変更しないでください。

5.  **[OK]** をクリックします。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 追加、 **datawriter の各**プロジェクトを**ソリューション エクスプ ローラー**開くと、 **Program.cs**または**Module1.vb**コード ファイル。

## <a name="add-data-to-the-cached-dataset-by-using-the-console-application"></a>コンソール アプリケーションを使用して、キャッシュされたデータセットにデータを追加します。
 使用して、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>データをブックにキャッシュされたデータセットを作成するコンソール アプリケーション内のクラス。

### <a name="to-add-data-to-the-cached-dataset"></a>キャッシュされたデータセットにデータを追加するには

1.  **ソリューション エクスプ ローラー**を右クリックし、 **datawriter の各**プロジェクトし、クリックして**参照の追加**します。

2.  **.NET** ] タブで [ **Microsoft.VisualStudio.Tools.Applications.ServerDocument**します。

3.  **[OK]** をクリックします。

4.  **ソリューション エクスプ ローラー**を右クリックし、 **datawriter の各**プロジェクトし、クリックして**参照の追加**します。

5.  **プロジェクト** タブで  **AdventureWorksDataSet**、 をクリック**OK**します。

6.  開く、 *Program.cs*または*Module1.vb*ファイルがコード エディター。

7.  次の追加**を使用して**(c#) のまたは**Imports** (Visual Basic) のステートメントをコード ファイルの先頭にします。

     [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8.  `Main` メソッドに次のコードを追加します。 このコードは、次のオブジェクトを宣言します。

    -   インスタンス、`AdventureWorksLTDataSet`と`ProductTableAdapter`型で定義されている、 **AdventureWorksDataSet**プロジェクト。

    -   ビルド フォルダー内の AdventureWorksReport ブックへのパス、 **AdventureWorksReport**プロジェクト。

    -   A<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>ブック内のデータ キャッシュへのアクセスに使用するオブジェクト。

        > [!NOTE]
        >  次のコードを持つブックを使用していることを想定しています、 *.xlsx*ファイル拡張子。 プロジェクトのブックに別のファイル拡張子がある場合は、必要に応じて、パスを変更します。

     [!code-csharp[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#3)]
     [!code-vb[Trin_CachedDataWalkthroughs#3](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#3)]

9. 次のコードを追加、`Main`前の手順で追加したコードの後のメソッド。 このコードは次のタスクを実行します。

    -   テーブル アダプターを使用して型指定された dataset オブジェクトを塗りつぶします。

    -   使用して、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>のプロパティ、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>ブックのキャッシュされたデータセットにアクセスするクラス。

    -   使用して、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>メソッド ローカル型指定されたデータセットのデータをキャッシュされたデータセットを作成します。

     [!code-csharp[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#4)]
     [!code-vb[Trin_CachedDataWalkthroughs#4](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#4)]

10. **ソリューション エクスプ ローラー**を右クリックし、 **datawriter の各**プロジェクトをポイントして、**デバッグ**、 をクリックし、**新しいインスタンスを開始**します。

     プロジェクトをビルドし、コンソール アプリケーションがローカルのデータセットと、アプリケーションは、ブックのキャッシュされたデータセットにデータを保存するときに、いくつかのステータス メッセージを表示します。 キーを押して**Enter**アプリケーションを終了します。

## <a name="test-the-workbook"></a>ブックをテストします。
 ブックを開くと、<xref:Microsoft.Office.Tools.Excel.ListObject>にコンソール アプリケーションを使用して、キャッシュされたデータセットに追加されたデータが表示されます。

### <a name="to-test-the-workbook"></a>ブックをテストするには

1.  まだ開いている場合は、Visual Studio デザイナーで AdventureWorksReport ブックを閉じます。

2.  ファイル エクスプ ローラーでのビルド フォルダー内にある AdventureWorksReport ブックを開く、 **AdventureWorksReport**プロジェクト。 既定では、ビルド フォルダーは、次の場所のいずれかでは。

    -   *%UserProfile%\My Documents\AdventureWorksReport\bin\Debug* (for Windows XP 以降)

    -   *%UserProfile%\Documents\AdventureWorksReport\bin\Debug* (Windows Vista) の場合

3.  いることを確認、<xref:Microsoft.Office.Tools.Excel.ListObject>ブックを開いた後に、データを設定します。

## <a name="next-steps"></a>次の手順

これらのトピックからキャッシュされたデータの処理に関する詳細を確認できます。

-   起動することがなくキャッシュされたデータセット内のデータを変更します。 詳細については、次を参照してください。[チュートリアル: 変更は、サーバー上のブック内のデータをキャッシュ](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)します。

## <a name="see-also"></a>関連項目

- [チュートリアル: サーバー上のブックにキャッシュされたデータを変更します。](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)