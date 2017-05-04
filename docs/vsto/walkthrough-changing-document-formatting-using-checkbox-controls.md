---
title: "チュートリアル : CheckBox コントロールを使用したドキュメント書式の変更 | Microsoft Docs"
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
  - "チェック ボックス, Word ドキュメント"
  - "コントロール [Visual Studio での Office 開発], 追加 (ドキュメントに)"
  - "ドキュメント [Visual Studio での Office 開発], チェック ボックス コントロール"
  - "ドキュメント [Visual Studio での Office 開発], 書式指定"
  - "Word ドキュメント, 変更 (コントロールを使って書式設定を)"
ms.assetid: 3740e41d-a57e-43bb-87e7-6e5481ef290b
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# チュートリアル : CheckBox コントロールを使用したドキュメント書式の変更
  このチュートリアルでは、Microsoft Office Word のドキュメント レベルのカスタマイズで Windows フォーム コントロールを使用してテキストの書式設定を変更する方法を示します。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   デザイン時におけるドキュメント レベルのプロジェクトの文書へのテキストおよびコントロールの追加  
  
-   オプション選択時のテキストの書式設定  
  
 この結果として完成したサンプルについては、「[Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)」の Word コントロールのサンプルを参照してください。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## プロジェクトの作成  
 まず、Word 文書プロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  My Word Formatting という名前の Word 文書プロジェクトを作成します。  ウィザードで、**\[新規ドキュメントの作成\]** をクリックします。  
  
     詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     新しい Word 文書がデザイナーで開き、**My Word Formatting** プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## テキストとコントロールの Word 文書への追加  
 このチュートリアルでは、Word 文書に 3 つのチェック ボックスを追加し、<xref:Microsoft.Office.Tools.Word.Bookmark> コントロールにテキストを指定します。  3 つのチェック ボックスは、ユーザーにテキストの書式設定オプションを提供します。  
  
#### 3 つのチェック ボックスを追加するには  
  
1.  Visual Studio デザイナーで文書が開いていることを確認します。  
  
2.  **\[ツールボックス\]** の **\[コモン コントロール\]** タブから 1 つ目の <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> コントロールを文書にドラッグします。  
  
3.  **\[プロパティ\]** ウィンドウで、次のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**applyBoldFont**|  
    |**テキスト**|太字|  
  
4.  **Enter** キーを押して、1 番目のチェック ボックスの下にカーソルを移動します。  
  
5.  文書の `ApplyBoldFont` チェック ボックスの下に 2 つ目のチェック ボックスを追加し、次のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**applyItalicFont**|  
    |**テキスト**|イタリック体|  
  
6.  **Enter** キーを押して、2 番目のチェック ボックスの下にカーソルを移動します。  
  
7.  文書の `ApplyItalicFont` チェック ボックスの下に 3 つ目のチェック ボックスを追加し、次のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**applyUnderlineFont**|  
    |**テキスト**|Underline|  
  
#### テキストと Bookmark コントロールを追加するには  
  
1.  チェック ボックス コントロールの下にカーソルを移動し、次のテキストを入力します。  
  
     チェック ボックスをクリックしてこのテキストの書式を変更します。  
  
2.  **\[ツールボックス\]** の **\[Word コントロール\]** タブから <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを文書にドラッグします。  
  
     **\[ブックマーク コントロールの追加\]** ダイアログ ボックスが表示されます。  
  
3.  文書に追加するテキストを選択し、**\[OK\]** をクリックします。  
  
     **Bookmark1** という名前の <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールが、文書内で選択されているテキストに追加されます。  
  
4.  **\[プロパティ\]** ウィンドウで、**\[\(名前\)\]** プロパティの値を **fontText** に変更します。  
  
 次に、チェック ボックスがオンまたはオフにされたときにテキストの書式を設定するコードを記述します。  
  
## チェック ボックスのオンまたはオフ時のテキストの書式設定  
 ユーザーが書式指定のオプションを選択したときに、文書内のテキストの書式を変更します。  
  
#### チェック ボックス選択時に書式を変更するには  
  
1.  **ソリューション エクスプローラー**で `ThisDocument` を右クリックし、ショートカット メニューの **\[コードの表示\]** をクリックします。  
  
2.  C\# の場合のみ、次の定数を **ThisDocument** クラスに追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#2)]  
  
3.  `applyBoldFont` チェック ボックスの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#3)]  
  
4.  `applyItalicFont` チェック ボックスの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#4)]  
  
5.  `applyUnderlineFont` チェック ボックスの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#5)]  
  
6.  C\# では、次に示すように、テキスト ボックスのイベント ハンドラーを <xref:Microsoft.Office.Tools.Word.Document.Startup> イベントに追加する必要があります。  イベント ハンドラーの作成方法については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」を参照してください。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#6)]  
  
## アプリケーションのテスト  
 文書をテストして、チェック ボックスをオンまたはオフにしたときにテキストの書式が正しく設定されることを確認できます。  
  
#### 文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  チェック ボックスをオンまたはオフにします。  
  
3.  テキストの書式が正しく設定されることを確認します。  
  
## 次の手順  
 このチュートリアルでは、Word 文書でチェック ボックスを使用して、プログラムからテキストの書式を変更する際の基本事項について説明します。  次に行う作業は以下のとおりです。  
  
-   ボタンを使用したテキスト ボックスへのデータの読み込み。  詳細については、「[チュートリアル : ボタンを使用して文書内のテキスト ボックスにテキストを表示する方法](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)」を参照してください。  
  
-   オプション ボタンを使用したグラフのスタイルの選択。  詳細については、「[チュートリアル : オプション ボタンを使用してドキュメントのグラフを更新する方法](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)」を参照してください。  
  
## 参照  
 [Word を使用したチュートリアル](../vsto/walkthroughs-using-word.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [Office ドキュメントでの Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  