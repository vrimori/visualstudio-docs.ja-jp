---
title: XML データをデータセットに読み込む
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c6c2ea2b46fcd05360e079dc84da9bfe807ff489
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="read-xml-data-into-a-dataset"></a>XML データをデータセットに読み込む
ADO.NET では、XML データを操作するための簡単な方法を提供します。 このチュートリアルでは、データセットに XML データを読み込む Windows アプリケーションを作成します。 データセットが表示されます、<xref:System.Windows.Forms.DataGridView>コントロール。 最後に、XML ファイルの内容に基づいて XML スキーマは、テキスト ボックスに表示されます。

 このチュートリアルは、5 つの主要な手順で構成されます。

1.  新しいプロジェクトを作成します。

2.  データセットに読み込まれる XML ファイルの作成

3.  ユーザー インターフェイスの作成

4.  データセットの作成、XML ファイルを読み取り、およびで表示する、<xref:System.Windows.Forms.DataGridView>コントロール

5.  XML ファイルに基づいて XML スキーマを表示するコードを追加する、<xref:System.Windows.Forms.TextBox>コントロール

> [!NOTE]
>  ダイアログ ボックスとメニュー コマンドが異なる場合があります、アクティブな設定またはエディションによっては、ヘルプの説明を表示するを使用しています。 設定を変更する、**ツール**メニューの **インポートおよびエクスポート設定**です。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する
 この手順では、このチュートリアルを含む Visual Basic または Visual c# プロジェクトを作成します。

#### <a name="to-create-the-new-windows-project"></a>新しい Windows プロジェクトを作成するには

1. Visual Studio での**ファイル**メニューの **新規**、**プロジェクト.**.

2. いずれかを展開**Visual c#**または**Visual Basic**左側のペインでを選択し、 **Windows クラシック デスクトップ**です。

3. 中央のペインで、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**ReadingXML**を選択し**OK**です。

     **ReadingXML**プロジェクトが作成され、追加**ソリューション エクスプ ローラー**です。

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>データセットに読み込まれる XML ファイルを生成します。
 このチュートリアルでは、データセットに XML データの読み取りに焦点を当てています、ため、XML ファイルの内容が提供されます。

#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>データセットに読み込まれる XML ファイルを作成するには

1.  **プロジェクト**メニューの **新しい項目の追加**です。

2.  選択**XML ファイル**、ファイルの名前を付けます`authors.xml`、し、**追加**です。

     XML ファイルは、デザイナーに読み込まれが編集できるようにします。

3.  XML 宣言の下のエディターに次のコードを貼り付けます。

    ```xml
    <Authors_Table>
      <authors>
        <au_id>172-32-1176</au_id>
        <au_lname>White</au_lname>
        <au_fname>Johnson</au_fname>
        <phone>408 496-7223</phone>
        <address>10932 Bigge Rd.</address>
        <city>Menlo Park</city>
        <state>CA</state>
        <zip>94025</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>213-46-8915</au_id>
        <au_lname>Green</au_lname>
        <au_fname>Margie</au_fname>
        <phone>415 986-7020</phone>
        <address>309 63rd St. #411</address>
        <city>Oakland</city>
        <state>CA</state>
        <zip>94618</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>238-95-7766</au_id>
        <au_lname>Carson</au_lname>
        <au_fname>Cheryl</au_fname>
        <phone>415 548-7723</phone>
        <address>589 Darwin Ln.</address>
        <city>Berkeley</city>
        <state>CA</state>
        <zip>94705</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>267-41-2394</au_id>
        <au_lname>Hunter</au_lname>
        <au_fname>Anne</au_fname>
        <phone>408 286-2428</phone>
        <address>22 Cleveland Av. #14</address>
        <city>San Jose</city>
        <state>CA</state>
        <zip>95128</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>274-80-9391</au_id>
        <au_lname>Straight</au_lname>
        <au_fname>Dean</au_fname>
        <phone>415 834-2919</phone>
        <address>5420 College Av.</address>
        <city>Oakland</city>
        <state>CA</state>
        <zip>94609</zip>
        <contract>true</contract>
      </authors>
    </Authors_Table>
    ```

4.  **ファイル**メニューの **保存 authors.xml**です。

## <a name="create-the-user-interface"></a>ユーザー インターフェイスを作成する
 このアプリケーションのユーザー インターフェイスを次の構成します。

-   A<xref:System.Windows.Forms.DataGridView>データとして XML ファイルの内容を表示するコントロール。

-   A <xref:System.Windows.Forms.TextBox> XML ファイルの XML スキーマを表示するコントロール。

-   2 つ<xref:System.Windows.Forms.Button>コントロール。

    -   1 つのボタンがデータセットに、XML ファイルを読み取りで表示、<xref:System.Windows.Forms.DataGridView>コントロール。

    -   データセットとで、2 番目のボタンが、スキーマを抽出し、<xref:System.IO.StringWriter>で表示、<xref:System.Windows.Forms.TextBox>コントロール。

#### <a name="to-add-controls-to-the-form"></a>フォームにコントロールを追加するには

1.  開いている`Form1`デザイン ビューでします。

2.  **ツールボックス**、次のコントロールをフォームにドラッグします。

    -   1 つ<xref:System.Windows.Forms.DataGridView>コントロール

    -   1 つ<xref:System.Windows.Forms.TextBox>コントロール

    -   2 つ<xref:System.Windows.Forms.Button>コントロール

3.  次のプロパティを設定します。

    |コントロール|プロパティ|設定|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**ScrollBars**|**垂直方向**|
    |`Button1`|**Name**|`ReadXmlButton`|
    ||**[テキスト]**|`Read XML`|
    |`Button2`|**Name**|`ShowSchemaButton`|
    ||**[テキスト]**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>XML データを受信するデータセットを作成します。
 という名前の新しいデータセットを作成するこの手順で`authors`です。 データセットの詳細については、次を参照してください。 [Visual Studio でのデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)です。

#### <a name="to-create-a-new-dataset-that-receives-the-xml-data"></a>XML データを受信する新しいデータセットを作成するには

1.  **ソリューション エクスプ ローラー**のソース ファイルを選択**Form1**、クリックして、**ビュー デザイナー**のボタンでは、**ソリューション エクスプ ローラー**ツールバー。

2.  [ツールボックス、[データ] タブ](../ide/reference/toolbox-data-tab.md)、ドラッグ、**データセット**に**Form1**です。

3.  **データセットの追加**ダイアログ ボックスで、**型指定されていないデータセット**、し、 **OK**です。

     **DataSet1**がコンポーネント トレイに追加します。

4.  **プロパティ**ウィンドウで、設定、**名前**と<xref:System.Data.DataSet.DataSetName%2A>プロパティ`AuthorsDataSet`です。

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>データセットに XML ファイルの読み取りにイベント ハンドラーを作成します。
 **読み取り XML**ボタンは、データセットに、XML ファイルを読み込みます。 プロパティを設定し、<xref:System.Windows.Forms.DataGridView>データセットにバインドするコントロール。

#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>ReadXmlButton_Click イベント ハンドラーにコードを追加するには

1.  **ソリューション エクスプ ローラー**select、 **Form1**、し、、**ビュー デザイナー**のボタンでは、**ソリューション エクスプ ローラー**ツールバー。

2.  選択、**読み取り XML**ボタンをクリックします。

     **コード エディター**で開き、`ReadXmlButton_Click`イベント ハンドラー。

3.  次のコードを入力、`ReadXmlButton_Click`イベントのハンドラー。

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4.  `ReadXMLButton_Click`イベント ハンドラーのコードの変更、`filepath =`正しいパスを入力します。

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>テキスト ボックスに、スキーマを表示するイベント ハンドラーを作成します。
 **スキーマの表示**ボタンを作成、<xref:System.IO.StringWriter>はスキーマで塗りつぶされに表示するオブジェクト、<xref:System.Windows.Forms.TextBox>コントロール。

#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>ShowSchemaButton_Click イベント ハンドラーにコードを追加するには

1.  **ソリューション エクスプ ローラー** **Form1**、し、選択、**ビュー デザイナー**ボタンをクリックします。

2.  選択、**スキーマの表示**ボタンをクリックします。

     **コード エディター**で開き、`ShowSchemaButton_Click`イベント ハンドラー。

3.  次のコードを入力、`ShowSchemaButton_Click`イベント ハンドラー。

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>フォームをテストします。
 フォームをテストして、期待どおりに動作することを確認します。

#### <a name="to-test-the-form"></a>フォームをテストするには

1.  選択**f5 キーを押して**アプリケーションを実行します。

2.  選択、**読み取り XML**ボタンをクリックします。

     DataGridView では、XML ファイルの内容を表示します。

3.  選択、**スキーマの表示**ボタンをクリックします。

     テキスト ボックスには、XML ファイルの XML スキーマが表示されます。

## <a name="next-steps"></a>次の手順
 このチュートリアルでは、データセット、XML ファイルを読み取るだけでなく、XML ファイルの内容に基づくスキーマの作成の基礎を説明します。 次に実行するいくつかのタスクを次に示します。

-   データセットと書き込みます XML としてデータを編集します。 詳細については、「<xref:System.Data.DataSet.WriteXml%2A>」を参照してください。

-   データセットのデータを編集し、データベースに書き込みます。 詳細については、次を参照してください。[データの保存](../data-tools/saving-data.md)です。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)
- [Visual Studio の XML ツール](../xml-tools/xml-tools-in-visual-studio.md)