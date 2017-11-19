---
title: "チュートリアル: ブックマークのショートカット メニューを作成する |Microsoft ドキュメント"
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
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
ms.assetid: 86dbf3ff-ba75-42f9-8df6-abfc19b3cf6b
caps.latest.revision: "57"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8dbb248fdaab10aaef6146ae68e36a64b60bb453
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-shortcut-menus-for-bookmarks"></a>チュートリアル : ブックマークのショートカット メニューの作成
  このチュートリアルでは、Word のドキュメント レベルのカスタマイズを使用して <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールのショートカット メニューを作成する方法を示します。 ユーザーがブックマーク内のテキストを右クリックすると、ショートカット メニューにテキストの書式設定オプションが表示されます。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   [プロジェクトを作成する](#BKMK_CreateProject)です。  
  
-   [文書にテキストとブックマークの追加](#BKMK_addtextandbookmarks)です。  
  
-   [ショートカット メニューにコマンドを追加する](#BKMK_AddCmndsShortMenu)です。  
  
-   [ブックマークにテキストを書式設定](#BKMK_formattextbkmk)です。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a>プロジェクトの作成  
 まず、Visual Studio で Word 文書プロジェクトを作成します。  
  
#### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
-   名前を持つ Word 文書プロジェクトを作成**My Bookmark Shortcut Menu**です。 ウィザードで、次のように選択します。**新しいドキュメントを作成する**です。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     デザイナーで新しい Word 文書を開き、 **My Bookmark Shortcut Menu**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
##  <a name="BKMK_addtextandbookmarks"></a>文書にテキストとブックマークの追加  
 文書にテキストを追加し、部分的に重なった 2 つのブックマークを追加します。  
  
#### <a name="to-add-text-to-your-document"></a>文書にテキストを追加するには  
  
-   プロジェクトのデザイナーで表示されているドキュメントに次のテキストを入力します。  
  
     **これは、ブックマーク内のテキストを右クリックすると、ショートカット メニューを作成する例です。**  
  
#### <a name="to-add-a-bookmark-control-to-your-document"></a>ドキュメントにブックマーク コントロールを追加するには  
  
1.  **ツールボックス**から、 **Word コントロール** タブで、ドラッグ、<xref:Microsoft.Office.Tools.Word.Bookmark>をドキュメントにコントロールできます。  
  
     **ブックマーク コントロールの追加** ダイアログ ボックスが表示されます。  
  
2.  「テキストを右クリックしたときに、ショートカット メニューを作成する」という語を選択して、をクリックし、 **[ok]**です。  
  
     `bookmark1` がドキュメントに追加されます。  
  
3.  もう 1 つ追加<xref:Microsoft.Office.Tools.Word.Bookmark>「、ブックマーク内のテキストを右クリックして」という語を制御します。  
  
     `bookmark2` がドキュメントに追加されます。  
  
    > [!NOTE]  
    >  両方に表示されます「のテキストを右クリックして」単語`bookmark1`と`bookmark2`です。  
  
 デザイン時に文書にブックマークを追加すると、<xref:Microsoft.Office.Tools.Word.Bookmark> コントロールが作成されます。 ブックマークの複数のイベントに対してプログラミングを行うことができます。 ブックマークの <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> イベントにコードを作成することで、ユーザーがブックマーク内のテキストを右クリックしたときにショートカット メニューを表示できます。  
  
##  <a name="BKMK_AddCmndsShortMenu"></a>ショートカット メニューにコマンドを追加します。  
 ドキュメントを右クリックすると表示されるショートカット メニューにボタンを追加します。  
  
#### <a name="to-add-commands-to-a-shortcut-menu"></a>ショートカット メニューにコマンドを追加するには  
  
1.  追加、**リボン XML**プロジェクト項目です。 詳細については、「 [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md)」を参照してください。  
  
2.  **ソリューション エクスプ ローラー** **ThisDocument.cs**または**ThisDocument.vb**です。  
  
3.  メニュー バーで **[表示]**、 **[コード]**の順に選択します。  
  
     **ThisDocument**コード エディターでクラス ファイルが開きます。  
  
4.  次のコードを追加、 **ThisDocument**クラスです。 このコードは、CreateRibbonExtensibilityObject メソッドをオーバーライドし、Office アプリケーションにリボン XML クラスを返します。  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]  
  
5.  **[ソリューション エクスプローラー]**でリボン XML ファイルを選択します。 既定では、リボン XML ファイルには Ribbon1.xml という名前が付けられます。  
  
6.  メニュー バーで **[表示]**、 **[コード]**の順に選択します。  
  
     コード エディターでリボン XML ファイルが開きます。  
  
7.  コード エディターを使用して、リボン XML ファイルの内容を次のコードに置き換えます。  
  
    ```  
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
  
8.  **ソリューション エクスプ ローラー**を右クリックして`ThisDocument`、クリックして**コードの表示**です。  
  
9. 次の変数とブックマーク変数をクラス レベルで宣言します。  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]  
  
10. **ソリューション エクスプ ローラー**、リボン コード ファイルを選択します。 既定では、リボン コード ファイルの名前は**Ribbon1.cs**または**Ribbon1.vb**です。  
  
11. メニュー バーで **[表示]**、 **[コード]**の順に選択します。  
  
     コード エディターでリボン コード ファイルが開きます。  
  
12. リボン コード ファイルで、次のメソッドを追加します。 これは、ドキュメントのショートカット メニューに追加した 2 つのボタンのコールバック メソッドです。 このメソッドでは、これらのボタンがショートカット メニューに表示されるかどうかが決定されます。 [太字] ボタンおよび [斜体] ボタンは、ブックマーク内のテキストを右クリックしたときにのみ表示されます。  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a>ブックマークにテキストを書式設定します。  
  
#### <a name="to-format-the-text-in-the-bookmark"></a>ブックマーク内のテキストに書式を設定するには  
  
1.  リボン コード ファイルで、ブックマークに書式を適用するための `ButtonClick` イベント ハンドラーを追加します。  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]  
  
2.  **ソリューション エクスプ ローラー** **ThisDocument.cs**または**ThisDocument.vb**です。  
  
3.  メニュー バーで **[表示]**、 **[コード]**の順に選択します。  
  
     **ThisDocument**コード エディターでクラス ファイルが開きます。  
  
4.  次のコードを追加、 **ThisDocument**クラスです。  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  ブックマークが部分的に重なっている場合を処理するためのコードを作成する必要があります。 これを行わないと、既定でコードは選択範囲内にあるすべてのブックマークについて呼び出されます。  
  
5.  C# では、次に示すように、ブックマーク コントロールのイベント ハンドラーを <xref:Microsoft.Office.Tools.Word.Document.Startup> イベントに追加する必要があります。 イベント ハンドラーの作成方法の詳細については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 ドキュメントをテストして、ブックマーク内のテキストを右クリックしたときにショートカット メニューに太字と斜体のメニュー項目が表示され、テキストが正しく書式設定されることを確認します。  
  
#### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  最初のブックマークを右クリックし、をクリックして**太字**です。  
  
3.  `bookmark1` 内のすべてのテキストが太字になることを確認します。  
  
4.  ブックマークが重なる、テキストを右クリックし、をクリックして**斜体**です。  
  
5.  `bookmark2` ではすべてのテキストが斜体になるが、`bookmark1` では `bookmark2` と重なっている部分のテキストしか斜体にならないことを確認します。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、次のタスクを行います。  
  
-   Excel 内のホスト コントロールのイベントに応答するコードを作成します。 詳細については、「 [Walkthrough: Programming Against Events of a NamedRange Control](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)」を参照してください。  
  
-   チェック ボックスを使用してブックマーク内の書式を変更します。 詳細については、次を参照してください。[チュートリアル: を変更するドキュメントの書式設定 チェック ボックス コントロールを使用した](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)です。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアルを使用して Word](../vsto/walkthroughs-using-word.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [Bookmark コントロール](../vsto/bookmark-control.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  