---
title: XML データのデータセットへの読み込み
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
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: dec6b30eec5e36212ec2e1a6a16d395a698f332c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946104"
---
# <a name="read-xml-data-into-a-dataset"></a>XML データのデータセットへの読み込み

ADO.NET では、XML データを操作するための単純なメソッドを提供します。 このチュートリアルでは、データセットに XML データを読み込む Windows アプリケーションを作成します。 データセットが表示し、<xref:System.Windows.Forms.DataGridView>コントロール。 最後に、XML ファイルの内容に基づく XML スキーマは、テキスト ボックスに表示されます。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する

この手順では、Visual Basic または Visual c# プロジェクトを作成します。

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

3. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**ReadingXML**を選び、 **OK**。

   **ReadingXML**プロジェクトが作成されに追加**ソリューション エクスプ ローラー**します。

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>データセットに読み込まれる XML ファイルを生成します。

このチュートリアルでは、データセットに XML データの読み取りに重点を置いています、ため、XML ファイルの内容が提供されます。

1. **[プロジェクト]** メニューで **[新しい項目の追加]** を選択します。

2. 選択**XML ファイル**、ファイルに名前を**authors.xml**、し、**追加**します。

   XML ファイルでは、デザイナーに読み込まし、編集の準備ができています。

3. XML 宣言の下のエディターには、次の XML データを貼り付けます。

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

4. **ファイル**メニューの **保存 authors.xml**します。

## <a name="create-the-user-interface"></a>ユーザー インターフェイスを作成する

このアプリケーションのユーザー インターフェイスを次の構成します。

-   A<xref:System.Windows.Forms.DataGridView>データとして XML ファイルの内容を表示するコントロール。

-   A <xref:System.Windows.Forms.TextBox> XML ファイルの XML スキーマを表示するコントロール。

-   2 つ<xref:System.Windows.Forms.Button>コントロール。

    -   1 つのボタンを選択し、XML ファイルをデータセットに読み込みますで表示、<xref:System.Windows.Forms.DataGridView>コントロール。

    -   2 番目のボタンと、データセットからスキーマを抽出し、<xref:System.IO.StringWriter>で表示、<xref:System.Windows.Forms.TextBox>コントロール。

### <a name="to-add-controls-to-the-form"></a>フォームにコントロールを追加するには

1.  開いている`Form1`デザイン ビューで。

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

この手順でという名前の新しいデータセットを作成する`authors`します。 データセットの詳細については、次を参照してください。 [Visual Studio でのデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)します。

1.  **ソリューション エクスプ ローラー**、ソース ファイルを選択します**Form1**を選び、**ビュー デザイナー**のボタンでは、**ソリューション エクスプ ローラー**ツールバー。

2.  [ツールボックス、[データ] タブ](../ide/reference/toolbox-data-tab.md)、ドラッグ、**データセット**に**Form1**します。

3.  **データセットの追加**ダイアログ ボックスで、**型指定されていないデータセット**、し、 **OK**します。

     **DataSet1**コンポーネント トレイに追加されます。

4.  **プロパティ**ウィンドウで、設定、**名前**と<xref:System.Data.DataSet.DataSetName%2A>プロパティ`AuthorsDataSet`します。

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>データセットに XML ファイルを読み取るためのイベント ハンドラーを作成します。

**読み取り XML**ボタンは、データセットに、XML ファイルを読み取ります。 プロパティを設定します、<xref:System.Windows.Forms.DataGridView>データセットにバインドするコントロール。

1.  **ソリューション エクスプ ローラー**を選択します**Form1**を選び、**ビュー デザイナー**のボタンでは、**ソリューション エクスプ ローラー**ツールバー。

2.  選択、**読み取り XML**ボタンをクリックします。

     **コード エディター**で開き、`ReadXmlButton_Click`イベント ハンドラー。

3.  次のコードを入力、`ReadXmlButton_Click`イベント ハンドラー。

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4.  `ReadXMLButton_Click`イベント ハンドラーのコードの変更、`filepath =`正しいパスへのエントリ。

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>テキスト ボックスに、スキーマを表示するイベント ハンドラーを作成します。

**スキーマの表示**ボタンを作成、<xref:System.IO.StringWriter>スキーマを使用して格納しに表示されるオブジェクト、<xref:System.Windows.Forms.TextBox>コントロール。

1.  **ソリューション エクスプ ローラー**を選択します**Form1**を選び、**ビュー デザイナー**ボタンをクリックします。

2.  選択、**スキーマの表示**ボタンをクリックします。

     **コード エディター**で開き、`ShowSchemaButton_Click`イベント ハンドラー。

3.  `ShowSchemaButton_Click` イベント ハンドラーに次のコードを貼り付けます。

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>フォームをテストします。

フォームをテストして、期待どおりに動作することを確認します。

1.  選択**F5**アプリケーションを実行します。

2.  選択、**読み取り XML**ボタンをクリックします。

     DataGridView は、XML ファイルの内容を表示します。

3.  選択、**スキーマの表示**ボタンをクリックします。

     テキスト ボックスには、XML ファイルの XML スキーマが表示されます。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、データセット、XML ファイルを読み取るだけでなく XML ファイルの内容に基づくスキーマの作成の基本を説明します。 次に実行する可能性のあるいくつかのタスクを次に示します。

-   データセットと書き戻せる XML としてデータを編集します。 詳細については、「<xref:System.Data.DataSet.WriteXml%2A>」を参照してください。

-   データセット内のデータを編集し、データベースに書き込みます。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)
- [Visual Studio の XML ツール](../xml-tools/xml-tools-in-visual-studio.md)