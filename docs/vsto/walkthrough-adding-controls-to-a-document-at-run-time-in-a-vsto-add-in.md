---
title: "チュートリアル: 実行時における VSTO アドインの文書へのコントロールの追加 | Microsoft Docs"
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
  - "アドイン [Visual Studio での Office 開発]、追加 (コントロールを)"
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発]、追加 (コントロールを)"
  - "コントロール [Visual Studio での Office 開発]、追加 (実行時にドキュメントに)"
  - "ドキュメント [Visual Studio での Office 開発]、追加 (実行時のコントロールを)"
ms.assetid: ab6dff40-9964-468a-938c-a71a3ac23718
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# チュートリアル: 実行時における VSTO アドインの文書へのコントロールの追加
  VSTO アドインを使用して、開いている Microsoft Office の Word 文書にコントロールを追加できます。 このチュートリアルでは、リボンを使用してユーザーがドキュメントに <xref:Microsoft.Office.Tools.Word.Controls.Button> または <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を追加できるようにする方法を説明します。  
  
 **対象:** このトピックの情報は、Word 2010 の VSTO アドインのプロジェクトに適用されます。 詳細については、「[Office アプリケーションおよびプロジェクト タイプ別の使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   新しい Word VSTO アドイン プロジェクトの作成。  
  
-   ドキュメントにコントロールを追加するためのユーザー インターフェイス \(UI\) の提供。  
  
-   実行時のドキュメントへのコントロールの追加。  
  
-   ドキュメントからのコントロールの削除。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## 新しい Word アドイン プロジェクトの作成  
 まず Word VSTO アドイン プロジェクトを作成します。  
  
#### 新しい Word VSTO アドイン プロジェクトを作成するには  
  
1.  **WordDynamicControls** という名前で Word 用 VSTO アドイン プロジェクトを作成します。 詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
2.  **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** アセンブリへの参照を追加します。 この参照は、このチュートリアルの後半でプログラムを使用して Windows フォーム コントロールをドキュメントに追加するのに必要です。  
  
## ドキュメントにコントロールを追加するための UI の提供  
 Word のリボンにカスタム タブを追加します。 ユーザーはタブにあるチェック ボックスをオンにして、ドキュメントにコントロールを追加できます。  
  
#### ドキュメントにコントロールを追加するための UI を提供するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[リボン \(ビジュアル デザイナー\)\]** をクリックします。  
  
3.  新しいリボンの名前を "**MyRibbon**" に変更し、**\[追加\]** をクリックします。  
  
     リボン デザイナーで **MyRibbon.cs** ファイルまたは **MyRibbon.vb** ファイルが開き、既定のタブとグループが表示されます。  
  
4.  リボン デザイナーで、**group1** グループをクリックします。  
  
5.  **\[プロパティ\]** ウィンドウで、**group1** の **\[ラベル\]** プロパティを **\[コントロールの追加\]** に変更します。  
  
6.  **ツールボックス**の **\[Office リボン コントロール\]** タブから、**CheckBox** コントロールを **group1** にドラッグします。  
  
7.  **\[CheckBox1\]** をクリックしてオンにします。  
  
8.  **\[プロパティ\]** ウィンドウで、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |**名前**|**addButtonCheckBox**|  
    |**ラベル**|**追加ボタン**|  
  
9. **group1** に 2 つ目のチェック ボックスを追加し、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |**名前**|**addRichTextCheckBox**|  
    |**ラベル**|**リッチ テキスト コントロールの追加**|  
  
10. リボン デザイナーで **\[ボタンの追加\]** をダブルクリックします。  
  
     **\[ボタンの追加\]** チェック ボックスの <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> イベント ハンドラーがコード エディターで開きます。  
  
11. リボン デザイナーに戻り、**\[リッチ テキスト コントロールの追加\]** をダブルクリックします。  
  
     **\[リッチ テキスト コントロールの追加\]** チェック ボックスの <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> イベント ハンドラーがコード エディターで開きます。  
  
 このチュートリアルの後半で、アクティブなドキュメントにコントロールを追加および削除するためのコードをこれらのイベント ハンドラーに追加します。  
  
## アクティブなドキュメントでのコントロールの追加と削除  
 VSTO アドインのコードでは、コントロールを追加するには、その前にアクティブなドキュメントを <xref:Microsoft.Office.Tools.Word.Document> *ホスト項目*に変換する必要があります。 Office ソリューションではマネージ コントロールを追加できるのはホスト項目に対してだけです。これはコントロールのコンテナーとして機能します。 VSTO アドイン プロジェクトでは、GetVstoObject メソッドを使用すると、実行時にホスト項目を作成できます。  
  
 アクティブなドキュメントに <xref:Microsoft.Office.Tools.Word.Controls.Button> または <xref:Microsoft.Office.Tools.Word.RichTextContentControl> を追加または削除するために呼び出せるメソッドを `ThisAddIn` クラスに追加します。 このチュートリアルの後半で、これらのメソッドをリボンのチェック ボックスの <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> イベント ハンドラーから呼び出します。  
  
#### アクティブなドキュメントでコントロールを追加または削除するには  
  
1.  **ソリューション エクスプローラー**で ThisAddIn.cs または ThisAddIn.vb をダブルクリックし、コード エディターでファイルを開きます。  
  
2.  `ThisAddIn` クラスに次のコードを追加します。 このコードは、ドキュメントに追加されるコントロールを表す <xref:Microsoft.Office.Tools.Word.Controls.Button> オブジェクトと <xref:Microsoft.Office.Tools.Word.RichTextContentControl> オブジェクトを宣言します。  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#1)]  
  
3.  `ThisAddIn` クラスに次のメソッドを追加します。 ユーザーがリボンの **\[ボタンの追加\]** チェック ボックスをクリックしてこれがオンになると、このメソッドによって <xref:Microsoft.Office.Tools.Word.Controls.Button> がドキュメントの現在の選択項目に追加されます。チェック ボックスがオフになると <xref:Microsoft.Office.Tools.Word.Controls.Button> が削除されます。  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#2)]  
  
4.  `ThisAddIn` クラスに次のメソッドを追加します。 ユーザーがリボンの **\[リッチ テキスト コントロールの追加\]** チェック ボックスをクリックしてこれがオンになると、このメソッドによって <xref:Microsoft.Office.Tools.Word.RichTextContentControl> がドキュメントの現在の選択項目に追加されます。チェック ボックスがオフになると <xref:Microsoft.Office.Tools.Word.RichTextContentControl> が削除されます。  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#3)]  
  
## ドキュメントを保存するときにボタン コントロールを削除する  
 ドキュメントを保存して閉じるときに Windows フォーム コントロールは保存されません。 ただし、各コントロールの ActiveX ラッパーはドキュメントに残るため、エンド ユーザーがドキュメントを再び開くときにこのラッパーの枠線が表示される場合があります。 VSTO アドインに作成された Windows フォーム コントロールを動的にクリーン アップする方法は、いくつかあります。 このチュートリアルでは、ドキュメントを保存するときに、<xref:Microsoft.Office.Tools.Word.Controls.Button> コントロールをプログラムで削除します。  
  
#### ドキュメントを保存するときにボタン コントロールを削除するには  
  
1.  ThisAddIn.cs または ThisAddIn.vb コード ファイルで、次のメソッドを `ThisAddIn` クラスに追加します。 このメソッドは、<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> イベントのイベント ハンドラーです。 保存されるドキュメントに <xref:Microsoft.Office.Tools.Word.Document> ホスト項目が関連付けられている場合、イベント ハンドラーはホスト項目を取得し、<xref:Microsoft.Office.Tools.Word.Controls.Button> コントロールが存在する場合にそれを削除します。  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#4)]  
  
2.  C\# では、`ThisAddIn_Startup` イベント ハンドラーに次のコードを追加します。 C\# では、`Application_DocumentBeforeSave` イベント ハンドラーを <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> イベントに接続するためにこのコードが必要です。  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#5)]  
  
## ユーザーがリボンのチェック ボックスをクリックしたときにコントロールを追加または削除する  
 最後に、リボンに追加したチェック ボックスの <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> イベント ハンドラーに対し、ドキュメント上のコントロールを追加または削除するための変更を加えます。  
  
#### ユーザーがリボンのチェック ボックスをクリックしたときにコントロールを追加または削除するには  
  
1.  MyRibbon.cs または MyRibbon.vb のコード ファイルで、生成された `addButtonCheckBox_Click` および `addRichTextCheckBox_Click` イベント ハンドラーを次のコードで置き換えます。 このコードは、このチュートリアルの前半で `ThisAddIn` クラスに追加した `ToggleButtonOnDocument` および `ToggleRichTextControlOnDocument` メソッドを呼び出すように、これらのイベント ハンドラーを再定義します。  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/MyRibbon.cs#6)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/MyRibbon.vb#6)]  
  
## ソリューションのテスト  
 リボンのカスタム タブからコントロールを選んでドキュメントに追加します。 ドキュメントを保存すると、<xref:Microsoft.Office.Tools.Word.Controls.Button> コントロールが削除されます。  
  
#### ソリューションをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  アクティブなドキュメントで Enter キーを何度か押して、ドキュメントに新しい空の段落を追加します。  
  
3.  最初の段落を選びます。  
  
4.  **\[アドイン\]** タブをクリックします。  
  
5.  **\[コントロールの追加\]** グループで **\[ボタンの追加\]** をクリックします。  
  
     最初の段落にボタンが表示されます。  
  
6.  最後の段落を選びます。  
  
7.  **\[コントロールの追加\]** グループで **\[リッチ テキスト コントロールの追加\]** をクリックします。  
  
     リッチ テキスト コンテンツのコントロールが最後の段落に追加されます。  
  
8.  ドキュメントを保存します。  
  
     ボタンがドキュメントから削除されます。  
  
## 次の手順  
 VSTO アドインのコントロールについて詳しくは、次の各トピックをご覧ください。  
  
-   実行時に他のさまざまな種類のコントロールをドキュメントに追加したり、ドキュメントを再び開くときにコントロールを再作成したりする方法を示すサンプルについては、「[Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)」にある Word アドイン動的コントロールのサンプルをご覧ください。  
  
-   Excel 用の VSTO アドインを使用してワークシートにコントロールを追加する方法を示すチュートリアルについては、「[チュートリアル : 実行時における VSTO アドイン プロジェクトのワークシートへのコントロールの追加](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)」をご覧ください。  
  
## 参照  
 [Word ソリューション](../vsto/word-solutions.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office ドキュメントでのダイナミック コントロールの永続化](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [方法 : Office ドキュメントに Windows フォーム コントロールを追加する](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [方法 : Word 文書にコンテンツ コントロールを追加する](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  