---
title: 'チュートリアル: ブックマークのショートカット メニューを作成します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fb09bc2ee3f9278026be2046ff249fb2ca4c558f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863995"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>チュートリアル: ブックマークのショートカット メニューを作成します。
  このチュートリアルでは、Word のドキュメント レベルのカスタマイズを使用して <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールのショートカット メニューを作成する方法を示します。 ユーザーがブックマーク内のテキストを右クリックすると、ショートカット メニューにテキストの書式設定オプションが表示されます。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
- [プロジェクトを作成する](#BKMK_CreateProject)します。  
  
- [文書にテキストとブックマークを追加](#BKMK_addtextandbookmarks)します。  
  
- [ショートカット メニューにコマンドを追加](#BKMK_AddCmndsShortMenu)します。  
  
- [ブックマークにテキストの書式設定](#BKMK_formattextbkmk)します。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a> プロジェクトを作成します。  
 まず、Visual Studio で Word 文書プロジェクトを作成します。  
  
### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
-   名前を持つ Word 文書プロジェクトを作成**My Bookmark Shortcut Menu**します。 ウィザードで、次のように選択します。**新しい文書を作成**です。 詳細については、「[方法 :Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
     デザイナーで新しい Word 文書を開き、 **My Bookmark Shortcut Menu**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
##  <a name="BKMK_addtextandbookmarks"></a> 文書にテキストとブックマークを追加します。  
 文書にテキストを追加し、部分的に重なった 2 つのブックマークを追加します。  
  
### <a name="to-add-text-to-your-document"></a>文書にテキストを追加するには  
  
-   プロジェクトのデザイナーで表示されているドキュメントに次のテキストを入力します。  
  
     **これは、ブックマーク内のテキストを右クリックすると、ショートカット メニューを作成する例です。**  
  
### <a name="to-add-a-bookmark-control-to-your-document"></a>ドキュメントにブックマーク コントロールを追加するには  
  
1. **ツールボックス**から、 **Word コントロール** タブで、ドラッグ、<xref:Microsoft.Office.Tools.Word.Bookmark>コントロールをドキュメント。  
  
    **ブックマーク コントロールの追加** ダイアログ ボックスが表示されます。  
  
2. 「テキストを右クリックするとショートカット メニューを作成する」単語を選択する、 をクリックし、 **OK**。  
  
    `bookmark1` がドキュメントに追加されます。  
  
3. もう 1 つ追加<xref:Microsoft.Office.Tools.Word.Bookmark>「ブックマーク内のテキストを右クリックして」単語を制御します。  
  
    `bookmark2` がドキュメントに追加されます。  
  
   > [!NOTE]  
   >  両方に表示されます「テキストを右クリックして」単語`bookmark1`と`bookmark2`します。  
  
   デザイン時に文書にブックマークを追加すると、<xref:Microsoft.Office.Tools.Word.Bookmark> コントロールが作成されます。 ブックマークの複数のイベントに対してプログラミングを行うことができます。 ブックマークの <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> イベントにコードを作成することで、ユーザーがブックマーク内のテキストを右クリックしたときにショートカット メニューを表示できます。  
  
##  <a name="BKMK_AddCmndsShortMenu"></a> ショートカット メニューにコマンドを追加します。  
 ドキュメントを右クリックすると表示されるショートカット メニューにボタンを追加します。  
  
### <a name="to-add-commands-to-a-shortcut-menu"></a>ショートカット メニューにコマンドを追加するには  
  
1.  追加、**リボン XML**プロジェクト項目。 詳細については、「[方法 :リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)します。  
  
2.  **ソリューション エクスプ ローラー**、 **ThisDocument.cs**または**ThisDocument.vb**します。  
  
3.  メニュー バーで **[表示]** > **[コード]** の順に選択します。  
  
     **ThisDocument**クラス ファイルがコード エディターでを開きます。  
  
4.  次のコードを追加、 **ThisDocument**クラス。 このコードでは、CreateRibbonExtensibilityObject メソッドをオーバーライドし、Office アプリケーションにリボン XML クラスを返します。  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]  
  
5.  **[ソリューション エクスプローラー]** でリボン XML ファイルを選択します。 既定では、リボン XML ファイルには Ribbon1.xml という名前が付けられます。  
  
6.  メニュー バーで **[表示]** > **[コード]** の順に選択します。  
  
     コード エディターでリボン XML ファイルが開きます。  
  
7.  コード エディターを使用して、リボン XML ファイルの内容を次のコードに置き換えます。  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8"?>  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="BoldButton" label="Bold" onAction="ButtonClick"          
               getVisible="GetVisible" />  
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"   
              getVisible="GetVisible"/>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
     このコードでは、ドキュメントを右クリックすると表示されるショートカット メニューに 2 つのボタンが追加されます。  
  
8.  **ソリューション エクスプ ローラー**、右クリック`ThisDocument`、 をクリックし、**コードの表示**します。  
  
9. 次の変数とブックマーク変数をクラス レベルで宣言します。  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]  
  
10. **ソリューション エクスプ ローラー**、リボン コード ファイルを選択します。 既定では、リボン コード ファイルの名前は**Ribbon1.cs**または**Ribbon1.vb**します。  
  
11. メニュー バーで **[表示]** > **[コード]** の順に選択します。  
  
     コード エディターでリボン コード ファイルが開きます。  
  
12. リボン コード ファイルで、次のメソッドを追加します。 これは、ドキュメントのショートカット メニューに追加した 2 つのボタンのコールバック メソッドです。 このメソッドでは、これらのボタンがショートカット メニューに表示されるかどうかが決定されます。 [太字] ボタンおよび [斜体] ボタンは、ブックマーク内のテキストを右クリックしたときにのみ表示されます。  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a> ブックマークにテキストの書式設定します。  
  
### <a name="to-format-the-text-in-the-bookmark"></a>ブックマーク内のテキストに書式を設定するには  
  
1.  リボン コード ファイルで、ブックマークに書式を適用するための `ButtonClick` イベント ハンドラーを追加します。  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]  
  
2.  **ソリューション エクスプ ローラー**、 **ThisDocument.cs**または**ThisDocument.vb**します。  
  
3.  メニュー バーで **[表示]** > **[コード]** の順に選択します。  
  
     **ThisDocument**クラス ファイルがコード エディターでを開きます。  
  
4.  次のコードを追加、 **ThisDocument**クラス。  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  ブックマークが部分的に重なっている場合を処理するためのコードを作成する必要があります。 これを行わないと、既定でコードは選択範囲内にあるすべてのブックマークについて呼び出されます。  
  
5.  C# では、次に示すように、ブックマーク コントロールのイベント ハンドラーを <xref:Microsoft.Office.Tools.Word.Document.Startup> イベントに追加する必要があります。 イベント ハンドラーの作成方法の詳細については、次を参照してください。[方法。Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)します。  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]  
  
## <a name="test-the-application"></a>アプリケーションをテストする  
 ドキュメントをテストして、ブックマーク内のテキストを右クリックしたときにショートカット メニューに太字と斜体のメニュー項目が表示され、テキストが正しく書式設定されることを確認します。  
  
### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  キーを押して**F5**プロジェクトを実行します。  
  
2.  最初のブックマークを右クリックし、をクリックし、**太字**します。  
  
3.  `bookmark1` 内のすべてのテキストが太字になることを確認します。  
  
4.  ブックマークが重複してテキストを右クリックし、**斜体**。  
  
5.  `bookmark2` ではすべてのテキストが斜体になるが、`bookmark1` では `bookmark2` と重なっている部分のテキストしか斜体にならないことを確認します。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、次のタスクを行います。  
  
-   Excel 内のホスト コントロールのイベントに応答するコードを作成します。 詳細については、「[チュートリアル:NamedRange コントロールのイベントに対してプログラム](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)します。  
  
-   チェック ボックスを使用してブックマーク内の書式を変更します。 詳細については、「[チュートリアル:CheckBox コントロールを使用して書式設定の変更ドキュメント](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Word を使用したチュートリアル](../vsto/walkthroughs-using-word.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [拡張オブジェクトを使用して Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)   
 [Bookmark コントロール](../vsto/bookmark-control.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
