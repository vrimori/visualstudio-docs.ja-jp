---
title: データセットにデータを読み取り XML |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3a4f5a7497e24ccd8e769198938dbd20a6bdf0f2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284558"
---
# <a name="read-xml-data-into-a-dataset"></a>XML データのデータセットへの読み込み
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
ADO.NET では、XML データを操作するための単純なメソッドを提供します。 このチュートリアルでは、データセットに XML データを読み込む Windows アプリケーションを作成します。 データセットが表示し、<xref:System.Windows.Forms.DataGridView>コントロール。 最後に、XML ファイルの内容に基づく XML スキーマは、テキスト ボックスに表示されます。  
  
 このチュートリアルは、5 つの主な手順で構成されます。  
  
1.  新しいプロジェクトを作成します。  
  
2.  データセットに読み込まれる XML ファイルの作成  
  
3.  ユーザー インターフェイスの作成  
  
4.  データセットの作成や、XML ファイルの読み取りで表示する、<xref:System.Windows.Forms.DataGridView>コントロール  
  
5.  XML ファイルに基づく XML スキーマを表示するコードを追加する、<xref:System.Windows.Forms.TextBox>コントロール  
  
> [!NOTE]
>  ダイアログ ボックスとメニュー コマンド、アクティブな設定またはエディションによって、ヘルプの記載を異なる場合がありますを表示するを使用しています。 設定を変更する、**ツール**メニューの **インポートおよびエクスポート設定**します。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="create-a-new-project"></a>新しいプロジェクトを作成する  
 この手順では、このチュートリアルを含む Visual Basic または Visual c# プロジェクトを作成します。  
  
#### <a name="to-create-the-new-windows-project"></a>新しい Windows プロジェクトを作成するには  
  
1.  **ファイル**] メニューの [新しいプロジェクトを作成します。  
  
2.  プロジェクトに `ReadingXML` という名前を付けます。  
  
3.  選択**Windows アプリケーション**、し、**OK**します。 詳細については、次を参照してください。[クライアント アプリケーション](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)します。  
  
     **ReadingXML**プロジェクトが作成されに追加**ソリューション エクスプ ローラー**します。  
  
## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>データセットに読み込まれる XML ファイルを生成します。  
 このチュートリアルでは、データセットに XML データの読み取りに重点を置いています、ため、XML ファイルの内容が提供されます。  
  
#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>データセットに読み込むことが XML ファイルを作成するには  
  
1.  **プロジェクト**メニューの **新しい項目の追加**します。  
  
2.  選択**XML ファイル**、ファイルに名前を`authors.xml`、し、**追加**します。  
  
     XML ファイルでは、デザイナーに読み込まし、編集の準備ができています。  
  
3.  XML 宣言の下のエディターには、次のコードを貼り付けます。  
  
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
  
4.  **ファイル**メニューの **保存 authors.xml**します。  
  
## <a name="create-the-user-interface"></a>ユーザー インターフェイスを作成する  
 このアプリケーションのユーザー インターフェイスを次の構成します。  
  
-   A<xref:System.Windows.Forms.DataGridView>データとして XML ファイルの内容を表示するコントロール。  
  
-   A <xref:System.Windows.Forms.TextBox> XML ファイルの XML スキーマを表示するコントロール。  
  
-   2 つ<xref:System.Windows.Forms.Button>コントロール。  
  
    -   1 つのボタンを選択し、XML ファイルをデータセットに読み込みますで表示、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
    -   2 番目のボタンと、データセットからスキーマを抽出し、<xref:System.IO.StringWriter>で表示、<xref:System.Windows.Forms.TextBox>コントロール。  
  
#### <a name="to-add-controls-to-the-form"></a>フォームにコントロールを追加するには  
  
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
  
## <a name="create-the-dataset-thatreceives-the-xml-data"></a>XML データを作成するには、データセット thatreceives  
 この手順でという名前の新しいデータセットを作成する`authors`します。 データセットの詳細については、次を参照してください。 [Visual Studio でのデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)します。  
  
#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>XML データを受信する新しいデータセットを作成するには  
  
1.  **ソリューション エクスプ ローラー**、ソース ファイルを選択します**Form1**を選び、**ビュー デザイナー**のボタンでは、**ソリューション エクスプ ローラー**ツールバー。  
  
2.  [ツールボックス、[データ] タブ](../ide/reference/toolbox-data-tab.md)、ドラッグ、**データセット**に**Form1**します。  
  
3.  **データセットの追加**ダイアログ ボックスで、**型指定されていないデータセット**、し、**OK**します。  
  
     **DataSet1**コンポーネント トレイに追加されます。  
  
4.  **プロパティ**ウィンドウで、設定、**名前**と<xref:System.Data.DataSet.DataSetName%2A>プロパティ`AuthorsDataSet`します。  
  
## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>データセットに XML ファイルを読み取るためのイベント ハンドラーを作成します。  
 **読み取り XML**ボタンは、データセットに、XML ファイルを読み取ります。 プロパティを設定します、<xref:System.Windows.Forms.DataGridView>データセットにバインドするコントロール。  
  
#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>ReadXmlButton_Click イベント ハンドラーにコードを追加するには  
  
1.  **ソリューション エクスプ ローラー**を選択します**Form1**を選び、**ビュー デザイナー**のボタンでは、**ソリューション エクスプ ローラー**ツールバー。  
  
2.  選択、**読み取り XML**ボタンをクリックします。  
  
     **コード エディター**で開き、`ReadXmlButton_Click`イベント ハンドラー。  
  
3.  次のコードを入力、`ReadXmlButton_Click`イベント ハンドラー。  
  
     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]  
  
4.  `ReadXMLButton_Click`イベント ハンドラーのコードの変更、`filepath =`正しいパスへのエントリ。  
  
## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>テキスト ボックスに、スキーマを表示するイベント ハンドラーを作成します。  
 **スキーマの表示**ボタンを作成、<xref:System.IO.StringWriter>スキーマを使用して格納しに表示されるオブジェクト、<xref:System.Windows.Forms.TextBox>コントロール。  
  
#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>ShowSchemaButton_Click イベント ハンドラーにコードを追加するには  
  
1.  **ソリューション エクスプ ローラー**を選択します**Form1**を選び、**ビュー デザイナー**ボタンをクリックします。  
  
2.  選択、**スキーマの表示**ボタンをクリックします。  
  
     **コード エディター**で開き、`ShowSchemaButton_Click`イベント ハンドラー。  
  
3.  次のコードを入力、`ShowSchemaButton_Click`イベント ハンドラー。  
  
     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>フォームをテストします。  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
1.  選択**F5**アプリケーションを実行します。  
  
2.  選択、**読み取り XML**ボタンをクリックします。  
  
     DataGridView は、XML ファイルの内容を表示します。  
  
3.  選択、**スキーマの表示**ボタンをクリックします。  
  
     テキスト ボックスには、XML ファイルの XML スキーマが表示されます。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、データセット、XML ファイルを読み取るだけでなく XML ファイルの内容に基づくスキーマの作成の基本を説明します。 次に実行する可能性のあるいくつかのタスクを次に示します。  
  
-   データセットと書き戻せる XML としてデータを編集します。 詳細については、「 <xref:System.Data.DataSet.WriteXml%2A> 」を参照してください。  
  
-   データセット内のデータを編集し、データベースに書き込みます。 詳細については、次を参照してください。[データの保存](../data-tools/saving-data.md)します。  
  
## <a name="see-also"></a>関連項目  
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Visual Studio の XML ツール](../xml-tools/xml-tools-in-visual-studio.md)

