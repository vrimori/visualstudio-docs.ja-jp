---
title: "方法 : Word 文書にコンテンツ コントロールを追加する | Microsoft Docs"
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
  - "制限されたアクセス許可 [Visual Studio での Office 開発]"
  - "DropDownListContentControl、追加 (ドキュメントに)"
  - "BuildingBlockGalleryContentControl、追加 (ドキュメントに)"
  - "部分的なドキュメント保護 [Visual Studio での Office 開発]"
  - "RichTextContentControl、追加 (ドキュメントに)"
  - "Word [Visual Studio での Office 開発]、部分的なドキュメント保護"
  - "コンテンツ コントロール [Visual Studio での Office 開発]、保護"
  - "PictureContentControl、追加 (ドキュメントに)"
  - "GroupContentControl、追加 (ドキュメントに)"
  - "ドキュメント保護 [Visual Studio での Office 開発]"
  - "PlainTextContentControl、追加 (ドキュメントに)"
  - "コンテンツ コントロール [Visual Studio での Office 開発]、追加"
  - "ComboBoxContentControl、追加 (ドキュメントに)"
  - "DatePickerContentControl、追加 (ドキュメントに)"
  - "Word [Visual Studio での Office 開発]、制限されたアクセス許可"
ms.assetid: 68ddb24e-71c6-46f7-8e11-c9899d7814df
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# 方法 : Word 文書にコンテンツ コントロールを追加する
  ドキュメント レベルの Word プロジェクトでは、デザイン時または実行時にプロジェクトの文書にコンテンツ コントロールを追加できます。 Word VSTO アドイン プロジェクトでは、実行時に任意の開いている文書にコンテンツ コントロールを追加できます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [デザイン時のコンテンツ コントロールの追加](#designtime)  
  
-   [実行時のドキュメント レベルのプロジェクトへのコンテンツ コントロールの追加](#runtimedoclevel)  
  
-   [VSTO アドイン プロジェクトでの実行時のコンテンツ コントロールの追加](#runtimeaddin)  
  
 コンテンツ コントロールについて詳しくは、「[コンテンツ コントロール](../vsto/content-controls.md)」をご覧ください。  
  
##  <a name="designtime"></a> デザイン時のコンテンツ コントロールの追加  
 デザイン時にドキュメント レベルのプロジェクトの文書にコンテンツ コントロールを追加する方法はいくつかあります。  
  
-   **\[ツールボックス\]** の **\[Word コントロール\]** タブからコンテンツ コントロールを追加する。  
  
-   Word でネイティブなコンテンツ コントロールを追加するのと同様に、ドキュメントにコンテンツ コントロールを追加します。  
  
-   **\[データ ソース\]** ウィンドウからコンテンツ コントロールを文書にドラッグする。 これは、コントロールの作成時にデータにコントロールをバインドする場合に役立ちます。 詳細については、次のトピックを参照してください。[方法 : オブジェクトのデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md) および[方法 : データベースからドキュメントにデータを読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### \[ツールボックス\] を使用して文書にコンテンツ コントロールを追加するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デザイナーでホストされているドキュメントで、コンテンツ コントロールを追加する場所にカーソルを置くか、または、テキストを置換するコンテンツ コントロールを選択します。  
  
2.  **\[ツールボックス\]** を開き、**\[Word コントロール\]** タブをクリックします。  
  
3.  次のいずれかの方法でコントロールを追加します。  
  
    -   **\[ツールボックス\]** のコンテンツ コントロールをダブルクリックします。  
  
         、または  
  
    -   **\[ツールボックス\]** のコンテンツ コントロールをクリックし、Enter キーを押します。  
  
         、または  
  
    -   **\[ツールボックス\]** からコンテンツ コントロールを文書にドラッグします。 コンテンツ コントロールが、マウス ポインターの場所ではなく、ドキュメント内の現在の選択の場所で追加されます。  
  
> [!NOTE]  
>  **\[ツールボックス\]** を使用して <xref:Microsoft.Office.Tools.Word.GroupContentControl> を追加することはできません。<xref:Microsoft.Office.Tools.Word.GroupContentControl> は Word で、または実行時にのみ追加できます。  
  
> [!NOTE]  
>  Visual Studio では、チェック ボックス コンテンツ コントロールがツールボックスで提供されていません。 文書にチェック ボックス コンテンツ コントロールを追加するには、プログラムを使用して <xref:Microsoft.Office.Tools.Word.ContentControl> オブジェクトを作成する必要があります。 詳細については、「[コンテンツ コントロール](../vsto/content-controls.md)」を参照してください。  
  
#### Word で文書にコンテンツ コントロールを追加するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デザイナーでホストされているドキュメントで、コンテンツ コントロールを追加する場所にカーソルを置くか、または、テキストを置換するコンテンツ コントロールを選択します。  
  
2.  リボンの **\[開発\]** タブをクリックします。  
  
    > [!NOTE]  
    >  **\[開発\]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「[方法 :タブをリボンに表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)」を参照してください。  
  
3.  **\[コントロール\]** グループで、追加するコンテンツ コントロールのアイコンをクリックします。  
  
##  <a name="runtimedoclevel"></a> 実行時のドキュメント レベルのプロジェクトへのコンテンツ コントロールの追加  
 プロジェクトで `ThisDocument` クラスの <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> プロパティのメソッドを使用して、実行時にプログラムによりドキュメントにコンテンツ コントロールを追加できます。 各メソッドには 3 つのオーバーロードがあります。それらを使用することにより、次のようにコンテンツ コントロールを追加できます。  
  
-   現在の選択項目でコントロールを追加します。  
  
-   指定された範囲にコントロールを追加します。  
  
-   文書内のネイティブなコンテンツ コントロールに基づいたコントロールを追加します。  
  
 動的に作成されたコンテンツ コントロールは、文書を閉じる際に文書に残りません。 ただし、ネイティブなコンテンツ コントロールは、文書内に残ります。 文書を次回開くときに、ネイティブのコンテンツ コントロールに基づくコンテンツ コントロールを再作成できます。 詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
> [!NOTE]  
>  Word 2010 プロジェクトで文書にチェック ボックス コンテンツ コントロールを追加するには、<xref:Microsoft.Office.Tools.Word.ContentControl> オブジェクトを作成する必要があります。 詳細については、「[コンテンツ コントロール](../vsto/content-controls.md)」を参照してください。  
  
#### 現在の選択項目でコンテンツ コントロールを追加するには  
  
1.  名前が `Add`\<*control class*\> \(*control class* は、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> などの追加するコンテンツ コントロールのクラス名\) で、パラメーターが 1 個 \(新しいコントロールの名前\) の <xref:Microsoft.Office.Tools.Word.ControlCollection> メソッドを使用します。  
  
     次のコード例では、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> メソッドを使用して文書の先頭に新しい <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を追加しています。 このコードを実行するには、プロジェクトの `ThisDocument` クラスにコードを追加し、`ThisDocument_Startup` イベント ハンドラーから `AddRichTextControlAtSelection` メソッドを呼び出します。  
  
     [!code-csharp[Trin_ContentControlReference#700](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#700)]  
  
#### 指定された範囲にコンテンツ コントロールを追加するには  
  
1.  名前が `Add`\<*control class*\> \(*control class* は、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> などの追加するコンテンツ コントロールのクラス名\) で、<xref:Microsoft.Office.Interop.Word.Range> をパラメーターとする <xref:Microsoft.Office.Tools.Word.ControlCollection> メソッドを使用します。  
  
     次のコード例では、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> メソッドを使用して文書の先頭に新しい <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を追加しています。 このコードを実行するには、プロジェクトの `ThisDocument` クラスにコードを追加し、`ThisDocument_Startup` イベント ハンドラーから `AddRichTextControlAtRange` メソッドを呼び出します。  
  
     [!code-csharp[Trin_ContentControlReference#701](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#701)]  
  
#### ネイティブなコンテンツ コントロールに基づいたコンテンツ コントロールを追加するには  
  
1.  名前が `Add`\<*control class*\> \(*control class* は、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> などの追加するコンテンツ コントロールのクラス名\) で、Microsoft.Office.Interop.Word.ContentControl をパラメーターとする <xref:Microsoft.Office.Tools.Word.ControlCollection> メソッドを使用します。  
  
     次のコード例では、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> メソッドを使用して、ドキュメント内にあるすべてのネイティブなリッチ テキスト コントロールについて新しい <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を作成しています。 このコードを実行するには、プロジェクトの `ThisDocument` クラスにコードを追加し、`ThisDocument_Startup` イベント ハンドラーから `CreateRichTextControlsFromNativeControls` メソッドを呼び出します。  
  
     [!code-csharp[Trin_ContentControlReference#702](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#702)]  
  
##  <a name="runtimeaddin"></a> VSTO アドイン プロジェクトでの実行時のコンテンツ コントロールの追加  
 コンテンツ フォーム コントロールは、実行時に VSTO アドインを使用して任意の開いているドキュメントに追加できます。 そのためには、開いている文書に基づいた <xref:Microsoft.Office.Tools.Word.Document> ホスト項目を生成し、このホスト項目の <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> プロパティのメソッドを使用します。 各メソッドには 3 つのオーバーロードがあります。それらを使用することにより、次のようにコンテンツ コントロールを追加できます。  
  
-   現在の選択項目でコントロールを追加します。  
  
-   指定された範囲にコントロールを追加します。  
  
-   文書内のネイティブなコンテンツ コントロールに基づいたコントロールを追加します。  
  
 動的に作成されたコンテンツ コントロールは、文書を閉じる際に文書に残りません。 ただし、ネイティブなコンテンツ コントロールは、文書内に残ります。 文書を次回開くときに、ネイティブのコンテンツ コントロールに基づくコンテンツ コントロールを再作成できます。 詳細については、「[Office ドキュメントでのダイナミック コントロールの永続化](../vsto/persisting-dynamic-controls-in-office-documents.md)」を参照してください。  
  
 VSTO アドイン プロジェクトでのホスト項目の生成の詳細については、「[VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」をご覧ください。  
  
> [!NOTE]  
>  文書にチェック ボックス コンテンツ コントロールを追加するには、<xref:Microsoft.Office.Tools.Word.ContentControl> オブジェクトを作成する必要があります。 詳細については、「[コンテンツ コントロール](../vsto/content-controls.md)」を参照してください。  
  
#### 現在の選択項目でコンテンツ コントロールを追加するには  
  
1.  名前が `Add`\<*control class*\> \(*control class* は、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> などの追加するコンテンツ コントロールのクラス名\) で、パラメーターが 1 個 \(新しいコントロールの名前\) の <xref:Microsoft.Office.Tools.Word.ControlCollection> メソッドを使用します。  
  
     次のコード例では、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> メソッドを使用してアクティブな文書の先頭に新しい <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を追加しています。 このコードを実行するには、プロジェクトの `ThisAddIn` クラスにコードを追加し、`ThisAddIn_Startup` イベント ハンドラーから `AddRichTextControlAtSelection` メソッドを呼び出します。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDynamicControls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#1)]  
  
#### 指定された範囲にコンテンツ コントロールを追加するには  
  
1.  名前が `Add`\<*control class*\> \(*control class* は、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> などの追加するコンテンツ コントロールのクラス名\) で、<xref:Microsoft.Office.Interop.Word.Range> をパラメーターとする <xref:Microsoft.Office.Tools.Word.ControlCollection> メソッドを使用します。  
  
     次のコード例では、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> メソッドを使用してアクティブな文書の先頭に新しい <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を追加しています。 このコードを実行するには、プロジェクトの `ThisAddIn` クラスにコードを追加し、`ThisAddIn_Startup` イベント ハンドラーから `AddRichTextControlAtRange` メソッドを呼び出します。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDynamicControls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#2)]  
  
#### ネイティブなコンテンツ コントロールに基づいたコンテンツ コントロールを追加するには  
  
1.  名前が `Add`\<*control class*\> \(*control class* は、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> などの追加するコンテンツ コントロールのクラス名\) で、Microsoft.Office.Interop.Word.ContentControl をパラメーターとする <xref:Microsoft.Office.Tools.Word.ControlCollection> メソッドを使用します。  
  
     次のコード例では、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> メソッドを使用して、文書を開いた後に文書内にあるすべてのネイティブなリッチ テキスト コントロールについて、新しい <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を作成しています。 このコードを実行するには、プロジェクトの `ThisAddIn` クラスに次のコードを追加します。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDynamicControls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#3)]  
  
     C\# の場合、`Application_DocumentOpen` イベント ハンドラーを <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> イベントに接続する必要もあります。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#6)]  
  
## 参照  
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)   
 [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)  
  
  