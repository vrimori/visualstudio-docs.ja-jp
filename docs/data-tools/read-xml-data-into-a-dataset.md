---
title: "チュートリアル : データセットへの XML データの読み込み | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ [Visual Studio], 読み取り (XML ファイルから)"
  - "データ アクセス [Visual Studio], XML データ"
  - "データセット [Visual Basic], 読み取り (XML データの)"
  - "読み取り (データを), XML ファイル"
  - "読み取り (ファイルを), XML"
  - "読み取り (XML の)"
  - "XML [Visual Studio], 読み取り"
  - "XML ドキュメント, 読み取り"
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# チュートリアル : データセットへの XML データの読み込み
ADO.NET には、XML データを使用するための簡単な方法が用意されています。  このチュートリアルでは、XML データをデータセットに読み込む Windows アプリケーションを作成します。  読み込まれたデータセットは <xref:System.Windows.Forms.DataGridView> に表示されます。  最後に、XML ファイルの内容に基づいた XML スキーマがテキスト ボックスに表示されます。  
  
 このチュートリアルは、主に次の 5 つの手順で構成されています。  
  
1.  新しいプロジェクトを作成します。  
  
2.  データセットに読み込む XML ファイルを作成します。  
  
3.  ユーザー インターフェイスを作成します。  
  
4.  データセットを作成し、XML ファイルを読み込んで <xref:System.Windows.Forms.DataGridView> コントロールに表示します。  
  
5.  XML ファイルに基づく XML スキーマを <xref:System.Windows.Forms.TextBox> コントロールに表示するためのコードを追加します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 新しいプロジェクトの作成  
 この手順では、このチュートリアルを含める Visual Basic プロジェクトまたは Visual C\# プロジェクトを作成します。  
  
#### 新しい Windows プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューで新しいプロジェクトを作成します。  
  
2.  プロジェクトに「`ReadingXML`」という名前を付けます。  
  
3.  **\[Windows アプリケーション\]** をクリックし、**\[OK\]** をクリックします。  詳細については、「[クライアント アプリケーション](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)」を参照してください。  
  
     **ReadingXML** プロジェクトが作成されてソリューション エクスプローラーに追加されます。  
  
## データセットに読み込む XML ファイルの作成  
 このチュートリアルでは、データセットへの XML データの読み込みについて重点的に説明するため、XML ファイルの内容を説明します。  
  
#### データセットに読み込む XML ファイルを作成するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **\[XML ファイル\]** をクリックし、ファイルに「`authors.xml`」という名前を付けて、**\[追加\]** をクリックします。  
  
     XML ファイルがデザイナーに読み込まれ、編集できるようになります。  
  
3.  エディターで XML 宣言の下に次のコードを貼り付けます。  
  
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
  
4.  **\[ファイル\]** メニューの **\[authors.xml の保存\]** をポイントします。  
  
## ユーザー インターフェイスの作成  
 このアプリケーションのユーザー インターフェイスは、次のコントロールで構成されています。  
  
-   XML ファイルの内容をデータとして表示する <xref:System.Windows.Forms.DataGridView> コントロール  
  
-   XML ファイルの XML スキーマを表示する <xref:System.Windows.Forms.TextBox> コントロール  
  
-   2 つの <xref:System.Windows.Forms.Button> コントロール  
  
    -   1 つのボタンは XML ファイルをデータセットに読み込んで <xref:System.Windows.Forms.DataGridView> コントロールに表示します。  
  
    -   もう 1 つのボタンは、データセットからスキーマを抽出し、<xref:System.IO.StringWriter> を使用して <xref:System.Windows.Forms.TextBox> コントロールに表示します。  
  
#### フォームにコントロールを追加するには  
  
1.  デザイン ビューで `Form1` を開きます。  
  
2.  **ツールボックス**からフォームに次のコントロールをドラッグします。  
  
    -   1 つの <xref:System.Windows.Forms.DataGridView> コントロール  
  
    -   1 つの <xref:System.Windows.Forms.TextBox> コントロール  
  
    -   2 つの <xref:System.Windows.Forms.Button> コントロール  
  
3.  次のプロパティを設定します。  
  
    |Control|プロパティ|設定|  
    |-------------|-----------|--------|  
    |`TextBox1`|**Multiline**|`true`|  
    ||**ScrollBars**|**\[垂直方向\]**|  
    |`Button1`|**名前**|`ReadXmlButton`|  
    ||**テキスト**|`Read XML`|  
    |`Button2`|**名前**|`ShowSchemaButton`|  
    ||**テキスト**|`Show Schema`|  
  
## XML データを受け取るデータセットの作成  
 次に、`authors` という名前の新しいデータセットを作成します。  データセットの詳細については、「[Visual Studio でのデータセットの操作](../data-tools/dataset-tools-in-visual-studio.md)」を参照してください。  
  
#### XML データを受け取るデータセットを新規作成するには  
  
1.  **ソリューション エクスプローラー**で **Form1** のソース ファイルを選択し、**ソリューション エクスプローラー**の **\[デザイナーの表示\]** をクリックします。  
  
2.  [ツールボックス、\[データ\] タブ](../Topic/Toolbox,%20Data%20Tab.md)から **Form1** に**データセット**をドラッグします。  
  
3.  \[ENT3ENT\] ダイアログ ボックスの \[ENT1ENT\] を選択し次に \[ENT4ENT\] をクリックします。  
  
     **DataSet1** がコンポーネント トレイに追加されます。  
  
4.  **\[プロパティ\]** ウィンドウで、**Name** プロパティおよび <xref:System.Data.DataSet.DataSetName%2A> プロパティを `AuthorsDataSet` に設定します。  
  
## XML をデータセットに読み込むイベント ハンドラーの作成  
 **\[Read XML\]** ボタンを使うと、XML ファイルがデータセットに読み込まれ、ファイルをデータセットにバインドする <xref:System.Windows.Forms.DataGridView> コントロールのプロパティが設定されます。  
  
#### ReadXmlButton\_Click イベント ハンドラーにコードを追加するには  
  
1.  **ソリューション エクスプローラー**の **\[Form1\]** をクリックし、**ソリューション エクスプローラー** ツール バーの **\[デザイナーの表示\]** をクリックします。  
  
2.  **\[Read XML\]** をダブルクリックします。  
  
     **コード エディター**が開き、`ReadXmlButton_Click` イベント ハンドラーが表示されます。  
  
3.  `ReadXmlButton_Click` イベント ハンドラー内に次のコードを入力します。  
  
     [!code-cs[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]  
  
4.  `ReadXMLButton_Click` イベント ハンドラーのコードで、`filepath =` の設定を正しいパスに変更します。  
  
## テキスト ボックスにスキーマを表示するイベント ハンドラーの作成  
 **\[Show Schema\]** をクリックすると、<xref:System.IO.StringWriter> オブジェクトが作成されます。このオブジェクトは、スキーマを格納しており、<xref:System.Windows.Forms.TextBox> に表示されます。  
  
#### ShowSchemaButton\_Click イベント ハンドラーにコードを追加するには  
  
1.  **ソリューション エクスプローラー**で **Form1** を選択し、**\[デザイナーの表示\]** をクリックします。  
  
2.  **\[Show Schema\]** をダブルクリックします。  
  
     **コード エディター**が開き、`ShowSchemaButton_Click` イベント ハンドラーが表示されます。  
  
3.  `ShowSchemaButton_Click` イベント ハンドラー内に次のコードを入力します。  
  
     [!code-cs[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]  
  
## テスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### フォームをテストするには  
  
1.  F5 キーを押してアプリケーションを実行します。  
  
2.  **\[Read XML\]** をクリックします。  
  
     XML ファイルの内容が DataGridView に表示されます。  
  
3.  **\[Show Schema\]** をクリックします。  
  
     XML ファイルの XML スキーマがテキスト ボックスに表示されます。  
  
## 次の手順  
 このチュートリアルでは、データセットに XML ファイルを読み込む方法の基本と、XML ファイルの内容に基づくスキーマの作成方法の基本を示します。  次に行う作業は以下のとおりです。  
  
-   データセットのデータを編集し、XML としてデータセットに書き込みます。  詳細については、「<xref:System.Data.DataSet.WriteXml%2A>」を参照してください。  
  
-   データセットのデータを編集し、データベースに書き込みます。  詳細については、「[データの保存](../data-tools/saving-data.md)」を参照してください。  
  
## 参照  
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)   
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Visual Studio の XML ツール](../xml-tools/xml-tools-in-visual-studio.md)