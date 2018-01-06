---
title: "チュートリアル: サーバー上のブック内のデータをキャッシュを変更する |Microsoft ドキュメント"
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
helpviewer_keywords:
- workbooks [Office development in Visual Studio], changing server data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
ms.assetid: 69e13de3-9286-40cc-8c4b-1727caf761bf
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9d6f3032a2c09b176b8fb1df7443cd07ef0ab1e8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-changing-cached-data-in-a-workbook-on-a-server"></a>チュートリアル : サーバー上のブックにキャッシュされたデータの変更
  このチュートリアルを使用して Excel を起動しなくても Microsoft Office Excel ブックにキャッシュされているデータセットを変更する方法を示します、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラスです。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   AdventureWorksLT データベースからデータを含むデータセットを定義します。  
  
-   Excel ブック プロジェクトおよびコンソール アプリケーション プロジェクトで、データセットのインスタンスを作成します。  
  
-   作成する、<xref:Microsoft.Office.Tools.Excel.ListObject>は、ブック内のデータセットにバインドされたで設定したとき、<xref:Microsoft.Office.Tools.Excel.ListObject>ブックを開いたときにデータを使用します。  
  
-   データ キャッシュに、ブック内のデータセットを追加します。  
  
-   キャッシュされたデータセット内のデータ列を変更するには、Excel を起動せず、コンソール アプリケーションでコードを実行します。  
  
 このチュートリアルでは、開発用コンピューター上のコードを実行していることを前提としていますが、Excel がインストールされていないサーバーでこのチュートリアルで示されるコードを使用できます。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   Microsoft SQL Server または接続して、AdventureWorksLT サンプル データベースがある Microsoft SQL Server Express の実行中のインスタンスへのアクセス。 AdventureWorksLT データベースをダウンロードすることができます、 [CodePlex Web サイト](http://go.microsoft.com/fwlink/?linkid=87843)です。 データベースをアタッチする方法について詳しくは、次のトピックをご覧ください。  
  
    -   SQL Server Management Studio または SQL Server Management Studio Express を使用してデータベースをアタッチする場合は、「 [データベースをアタッチする方法 (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa)」をご覧ください。  
  
    -   コマンド ラインを使用してデータベースをアタッチする場合は、「 [データベース ファイルを SQL Server Express にアタッチする方法](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68)」をご覧ください。  
  
## <a name="creating-a-class-library-project-that-defines-a-dataset"></a>データセットを定義するクラス ライブラリ プロジェクトを作成します。  
 Excel ブック プロジェクトと、コンソール アプリケーションで同じデータセットを使用するのには、これらのプロジェクトの両方で参照されている別のアセンブリにデータセットを定義する必要があります。 このチュートリアルでは、クラス ライブラリ プロジェクトで、データセットを定義します。  
  
#### <a name="to-create-the-class-library-project"></a>クラス ライブラリ プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  **[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。  
  
3.  テンプレート ペインで、展開**Visual c#**または**Visual Basic**、クリックして**Windows**です。  
  
4.  プロジェクト テンプレートの一覧で選択**クラス ライブラリ**です。  
  
5.  **名前**ボックスに、入力**AdventureWorksDataSet**です。  
  
6.  をクリックして**参照**%UserProfile%\My ドキュメント (Windows XP 用と以前) または (Windows Vista の場合) の %UserProfile%\Documents フォルダーに移動し、をクリックして、**フォルダーの選択**です。  
  
7.  **新しいプロジェクト** ダイアログ ボックスで、いることを確認、**ソリューションのディレクトリを作成** チェック ボックスが選択されていません。  
  
8.  **[OK]**をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]追加、 **AdventureWorksDataSet**プロジェクトを**ソリューション エクスプ ローラー**開くと、 **Class1.cs**または**Class1.vb**コード ファイル。  
  
9. **ソリューション エクスプ ローラー**を右クリックして**Class1.cs**または**Class1.vb**、クリックして**削除**です。 このチュートリアルのこのファイルが不要です。  
  
## <a name="defining-a-dataset-in-the-class-library-project"></a>クラス ライブラリ プロジェクトでデータセットを定義します。  
 データを含む、AdventureWorksLT データベースから SQL Server 2005 の型指定されたデータセットを定義します。 このチュートリアルの後半では、Excel ブック プロジェクトと、コンソール アプリケーション プロジェクトからこのデータセットを参照します。  
  
 データセットが、*型指定されたデータセット*AdventureWorksLT データベースの Product テーブル内のデータを表すです。 型指定されたデータセットの詳細については、次を参照してください。 [Visual Studio でのデータセット ツール](/visualstudio/data-tools/dataset-tools-in-visual-studio)です。  
  
#### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>クラス ライブラリ プロジェクトで指定されたデータセットを定義するには  
  
1.  **ソリューション エクスプ ローラー**をクリックして、 **AdventureWorksDataSet**プロジェクト。  
  
2.  **[データ ソース]** ウィンドウが表示されていない場合は、メニュー バーの **[表示]**、 **[その他のウィンドウ]**、 **[データ ソース]**の順にクリックして表示します。  
  
3.  **[新しいデータ ソースの追加]** をクリックして **データ ソース構成ウィザード**を開始します。  
  
4.  **[データベース]**をクリックして、 **[次へ]**をクリックします。  
  
5.  この接続を選択しをクリックして、AdventureWorksLT データベースへの既存の接続があれば、**次**です。  
  
     それ以外の場合は、 **[新しい接続]**をクリックし、 **[接続の追加]** ダイアログ ボックスを使用して新しい接続を作成します。 詳細については、次を参照してください。[新しい接続を追加](../data-tools/add-new-connections.md)です。  
  
6.  **[アプリケーション構成ファイルへの接続文字列を保存]** ページで、 **[次へ]**をクリックします。  
  
7.  **データベース オブジェクトの選択** ページで、展開**テーブル**選択**Product (SalesLT)**です。  
  
8.  **[完了]**をクリックします。  
  
     AdventureWorksLTDataSet.xsd ファイルに追加、 **AdventureWorksDataSet**プロジェクト。 このファイルでは、次の項目を定義します。  
  
    -   `AdventureWorksLTDataSet`という名前の型指定されたデータセット。 このデータセットでは、AdventureWorksLT データベースは Product テーブルの内容を表します。  
  
    -   という名前の TableAdapter`ProductTableAdapter`です。 この TableAdapter データを読み書きするために使用できます、`AdventureWorksLTDataSet`です。 詳細については、「 [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)」を参照してください。  
  
     これらのオブジェクトは、どちらもこのチュートリアルの後半で使用します。  
  
9. **ソリューション エクスプ ローラー**を右クリックして**AdventureWorksDataSet**  をクリック**ビルド**です。  
  
     プロジェクトのビルドでエラーが発生しないことを確認します。  
  
## <a name="creating-an-excel-workbook-project"></a>Excel ブック プロジェクトの作成  
 データへのインターフェイス用の Excel ブック プロジェクトを作成します。 このチュートリアルの後半で作成するが、<xref:Microsoft.Office.Tools.Excel.ListObject>データを表示して、ブック内のデータ キャッシュに、データセットのインスタンスを追加します。  
  
#### <a name="to-create-the-excel-workbook-project"></a>Excel ブック プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **AdventureWorksDataSet**ソリューションでは、順にポイント**追加**、クリックして**新しいプロジェクト**です。  
  
2.  [テンプレート] ペインで、展開**Visual c#**または**Visual Basic**、順に展開**Office**です。  
  
3.  展開した  **Office**ノードで、選択、 **2010**ノード。  
  
4.  プロジェクト テンプレートの一覧で、Excel ブック プロジェクトを選択します。  
  
5.  **名前**ボックスに、入力**AdventureWorksReport**です。 場所は変更しないでください。  
  
6.  **[OK]**をクリックします。  
  
     **Visual Studio Tools for Office プロジェクト ウィザード** が開きます。  
  
7.  いることを確認**新しいドキュメントを作成する**を選択して、をクリックして**OK**です。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]開きます、 **AdventureWorksReport**デザイナーでブックを追加し、 **AdventureWorksReport**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Excel ブック プロジェクトのデータ ソースにデータセットを追加します。  
 データセットを表示するには、Excel ブックで、前に、Excel ブック プロジェクトのデータ ソースにデータセットを追加する必要があります。  
  
#### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Excel ブック プロジェクトのデータ ソースにデータセットを追加するには  
  
1.  **ソリューション エクスプ ローラー**をダブルクリックして**Sheet1.cs**または**Sheet1.vb**下にある、 **AdventureWorksReport**プロジェクト。  
  
     ブックは、デザイナーで開きます。  
  
2.  **[データ]** メニューの **[新しいデータ ソースの追加]**をクリックします。  
  
     **データ ソース構成ウィザード**が開きます。  
  
3.  をクリックして**オブジェクト**、順にクリック**次**です。  
  
4.  **オブジェクトを選択へのバインドに**] ページで [**参照の追加**です。  
  
5.  **プロジェクト** タブで、をクリックして**AdventureWorksDataSet**  をクリックし、 **OK**です。  
  
6.  下にある、 **AdventureWorksDataSet**の名前空間、 **AdventureWorksDataSet**アセンブリをクリックして**AdventureWorksLTDataSet**順にクリック**[完了]**.  
  
     **データソース**ウィンドウが開き、および**AdventureWorksLTDataSet**がデータ ソースの一覧に追加します。  
  
## <a name="creating-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>データセットのインスタンスにバインドされる listobject コントロールの作成  
 表示するには、データセット、ブックの作成、<xref:Microsoft.Office.Tools.Excel.ListObject>データセットのインスタンスにバインドされています。 コントロールのデータへのバインドについて詳しくは、「 [Binding Data to Controls in Office Solutions](../vsto/binding-data-to-controls-in-office-solutions.md)」をご覧ください。  
  
#### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>データセットのインスタンスにバインドされた listobject コントロールを作成するには  
  
1.  **データソース**ウィンドウで、展開、 **AdventureWorksLTDataSet**ノードの下**AdventureWorksDataSet**です。  
  
2.  選択、**製品** ノードを選択し、表示されるドロップダウン矢印をクリックして**ListObject**ドロップダウン リストでします。  
  
     ドロップダウン矢印が表示されない場合は、ブックがデザイナーで開かれていることを確認します。  
  
3.  ドラッグ、**製品**セル A1 にテーブルです。  
  
     A<xref:Microsoft.Office.Tools.Excel.ListObject>という名前のコントロール`productListObject`セル A1 にワークシート上に作成します。 同時、という名前のデータセット オブジェクト`adventureWorksLTDataSet`と<xref:System.Windows.Forms.BindingSource>という`productBindingSource`プロジェクトに追加されます。 <xref:Microsoft.Office.Tools.Excel.ListObject> が <xref:System.Windows.Forms.BindingSource>にバインドされ、さらにこれがデータセット オブジェクトにバインドされます。  
  
## <a name="adding-the-dataset-to-the-data-cache"></a>データ キャッシュにデータセットを追加します。  
 ブック内のデータセットにアクセスする Excel ブック プロジェクトの外側のコードを有効にするには、データ キャッシュにデータセットを追加する必要があります。 データ キャッシュの詳細については、次を参照してください。[ドキュメント レベルのカスタマイズでキャッシュ データ](../vsto/cached-data-in-document-level-customizations.md)と[データをキャッシュ](../vsto/caching-data.md)です。  
  
#### <a name="to-add-the-dataset-to-the-data-cache"></a>データ キャッシュにデータセットを追加するには  
  
1.  デザイナーで、をクリックして**adventureWorksLTDataSet**です。  
  
2.  **プロパティ**ウィンドウで、設定、**修飾子**プロパティを**パブリック**です。  
  
3.  設定、 **CacheInDocument**プロパティを**True**です。  
  
## <a name="initializing-the-dataset-in-the-workbook"></a>ブック内のデータセットの初期化  
 キャッシュされたデータセットからデータを取得するには、コンソール アプリケーションを使用して、前にまず、キャッシュされたデータセットにデータを設定する必要があります。  
  
#### <a name="to-initialize-the-dataset-in-the-workbook"></a>ブック内のデータセットを初期化するために  
  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **Sheet1.cs**または**Sheet1.vb**ファイルし、クリックして**コードの表示**です。  
  
2.  `Sheet1_Startup` イベント ハンドラーを次のコードで置き換えます。 このコードのインスタンスを使用して、`ProductTableAdapter`クラスで定義されている、 **AdventureWorksDataSet**キャッシュされたデータセットにデータを格納、現在は空である場合のプロジェクトです。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]  
  
## <a name="checkpoint"></a>チェックポイント  
 ビルドして、Excel ブック プロジェクトをコンパイルおよび実行エラーが発生しないことを確認を実行します。 この操作もキャッシュされたデータセットを入力し、ブックのデータを保存します。  
  
#### <a name="to-build-and-run-the-project"></a>プロジェクトをビルドして実行するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **AdventureWorksReport**プロジェクト**デバッグ**、順にクリック**新しいインスタンスを開始**です。  
  
     プロジェクトがビルドされ、Excel でブックを開きます。 次のことを検証します。  
  
    -   <xref:Microsoft.Office.Tools.Excel.ListObject>にデータを入力します。  
  
    -   値、 **ListPrice**の最初の行の列、 <xref:Microsoft.Office.Tools.Excel.ListObject> 1431.5 がします。 このチュートリアルの後半では、コンソール アプリケーションを使用で値を変更する、 **ListPrice**列です。  
  
2.  ブックを保存します。 ファイル名またはブックの場所を変更しないでください。  
  
3.  Excel を終了します。  
  
## <a name="creating-a-console-application-project"></a>コンソール アプリケーション プロジェクトを作成します。  
 使用して、ブックのキャッシュされたデータセットのデータを変更するコンソール アプリケーション プロジェクトを作成します。  
  
#### <a name="to-create-the-console-application-project"></a>コンソール アプリケーション プロジェクトを作成するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **AdventureWorksDataSet**ソリューションでは、順にポイント**追加**、クリックして**新しいプロジェクト**です。  
  
2.  **プロジェクトの種類** ウィンドウで、展開**Visual c#**または**Visual Basic**、クリックして**Windows**です。  
  
3.  **テンプレート**ペインで、**コンソール アプリケーション**です。  
  
4.  **名前**ボックスに、入力**DataWriter**です。 場所は変更しないでください。  
  
5.  **[OK]**をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]追加、 **DataWriter**プロジェクトを**ソリューション エクスプ ローラー**開くと、 **Program.cs**または**Module1.vb**コード ファイル。  
  
## <a name="changing-data-in-the-cached-dataset-by-using-the-console-application"></a>コンソール アプリケーションを使用して、キャッシュされたデータセット内のデータを変更します。  
 使用して、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>ローカル データの読み取りにコンソール アプリケーション内のクラス`AdventureWorksLTDataSet`オブジェクト、このデータを変更し、キャッシュされたデータセットに保存します。  
  
#### <a name="to-change-data-in-the-cached-dataset"></a>キャッシュされたデータセット内のデータを変更するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **DataWriter**プロジェクトし、クリックして**参照の追加**です。  
  
2.  **.NET**  タブで、Microsoft.VisualStudio.Tools.Applications を選択します。  
  
3.  **[OK]**をクリックします。  
  
4.  **ソリューション エクスプ ローラー**を右クリックし、 **DataWriter**プロジェクトし、クリックして**参照の追加**です。  
  
5.  **プロジェクト** タブで  **AdventureWorksDataSet**、 をクリック**OK**です。  
  
6.  コード エディターで、Program.cs ファイルまたは Module1.vb ファイルを開きます。  
  
7.  次の追加**を使用して**(C# の場合) または**Imports** (Visual Basic の場合) のステートメントをコード ファイルの先頭。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]  
  
8.  `Main` メソッドに次のコードを追加します。 このコードは、次のオブジェクトを宣言します。  
  
    -   インスタンス、`AdventureWorksLTDataSet`で定義されている型、 **AdventureWorksDataSet**プロジェクト。  
  
    -   ビルド フォルダー内の AdventureWorksReport ブックへのパス、 **AdventureWorksReport**プロジェクト。  
  
    -   A<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>を使用して、ブック内のデータ キャッシュにアクセスするオブジェクト。  
  
        > [!NOTE]  
        >  次のコードでは、.xlsx ファイルの拡張子を持つブックを使用していることを前提としています。 プロジェクトのブックが別のファイル拡張子の場合は、必要に応じてパスを変更します。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#6)]
     [!code-vb[Trin_CachedDataWalkthroughs#6](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#6)]  
  
9. 次のコードを追加、`Main`メソッド、前の手順で追加したコードの後にします。 このコードは次のタスクを実行します。  
  
    -   使用して、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>のプロパティ、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>ブックのキャッシュされたデータセットにアクセスするクラス。  
  
    -   ローカルのデータセットにキャッシュされたデータセットからデータを読み取ります。  
  
    -   変更、`ListPrice`データセットの Product テーブル内の各製品の値。  
  
    -   ブックのキャッシュされたデータセットに変更を保存します。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#7)]
     [!code-vb[Trin_CachedDataWalkthroughs#7](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#7)]  
  
10. **ソリューション エクスプ ローラー**を右クリックし、 **DataWriter**プロジェクトをポイントし、**デバッグ**、クリックして**新しいインスタンスを開始**です。  
  
     コンソール アプリケーションでは、ローカルのデータセットにキャッシュされたデータセットを読み取り、ローカルのデータセット内の製品価格が変更、キャッシュされたデータセットに新しい値を保存中に、メッセージが表示されます。 アプリケーションを終了するには、enter キーを押します。  
  
## <a name="testing-the-workbook"></a>ブックのテスト  
 ブックを開くと、<xref:Microsoft.Office.Tools.Excel.ListObject>に加えた変更が表示されます、`ListPrice`キャッシュされたデータセット内のデータの列です。  
  
#### <a name="to-test-the-workbook"></a>ブックをテストするには  
  
1.  まだ開いている場合は、Visual Studio デザイナーで AdventureWorksReport ブックを閉じます。  
  
2.  ビルド フォルダー内にある AdventureWorksReport ブックを開き、 **AdventureWorksReport**プロジェクト。 既定では、ビルド フォルダーは、次の場所のいずれかでは。  
  
    -   %UserProfile%\My Documents\AdventureWorksReport\bin\Debug (Windows xp および以前)  
  
    -   (Windows Vista の場合) の %UserProfile%\Documents\AdventureWorksReport\bin\Debug  
  
3.  いることを確認の値、 **ListPrice**の最初の行の列、 <xref:Microsoft.Office.Tools.Excel.ListObject> 1574.65 になります。  
  
4.  ブックを閉じます。  
  
## <a name="see-also"></a>参照  
 [チュートリアル: サーバー上のブックへのデータの挿入](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)   
 [Windows フォーム アプリケーションでのデータへの接続](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  