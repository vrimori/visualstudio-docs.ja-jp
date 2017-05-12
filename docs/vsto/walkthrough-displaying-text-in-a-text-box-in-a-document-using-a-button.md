---
title: "チュートリアル : ボタンを使用して文書内のテキスト ボックスにテキストを表示する方法"
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
  - "テキスト ボックス, 表示 (文書内のテキストを)"
ms.assetid: 04c54ed7-9f00-4068-aaec-1f3200110116
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# チュートリアル : ボタンを使用して文書内のテキスト ボックスにテキストを表示する方法
  このチュートリアルでは、Microsoft Office Word のドキュメント レベルのカスタマイズでボタンやテキスト ボックスを使用する方法を示します。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   デザイン時にドキュメント レベルのプロジェクトで Word 文書にコントロールを追加する。  
  
-   ボタンがクリックされたときにテキスト ボックスにデータを読み込む。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## プロジェクトの作成  
 最初に、Word 文書のプロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  「My Word Button」という名前の Word 文書プロジェクトを作成します。  ウィザードで、**\[新規ドキュメントの作成\]** をクリックします。  
  
     詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     新しい Word 文書が Visual Studio のデザイナーで開かれ、**My Word Button** プロジェクトが**\[ソリューション エクスプローラー\]**に追加されます。  
  
## Word 文書へのコントロールの追加  
 ユーザー インターフェイス コントロールは、Word 文書上のボタンとテキスト ボックスで構成されます。  
  
#### ボタンとテキスト ボックスを追加するには  
  
1.  Visual Studio デザイナーで文書が開いていることを確認します。  
  
2.  **\[ツールボックス\]** の **\[コモン コントロール\]** タブから、<xref:Microsoft.Office.Tools.Word.Controls.TextBox> コントロールを文書にドラッグします。  
  
    > [!NOTE]  
    >  Word の既定では、コントロールはテキスト中にインラインでドロップされます。  コントロールや図形オブジェクトの挿入方法を変更するには、Word の **\[オプション\]** ダイアログ ボックスの **\[編集\]** タブで既定の設定を変更します。  
  
3.  **\[表示\]** メニューの **\[プロパティ ウィンドウ\]** をクリックします。  
  
4.  **\[プロパティ\]** ウィンドウのドロップダウン ボックスで **\[TextBox1\]** を見つけ、このテキスト ボックスの **\[名前\]** プロパティを「**displayText**」に変更します。  
  
5.  **Button** コントロールを文書にドラッグし、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |**名前**|**insertText**|  
    |**テキスト**|テキストの挿入|  
  
 これで、ボタンがクリックされたときに実行されるコードを記述できるようになりました。  
  
## ボタンがクリックされたときにテキスト ボックスにデータを読み込む  
 ユーザーがボタンをクリックするたびに、テキスト ボックスに **Hello World\!** が追加されます。  
  
#### ボタンがクリックされたときにテキスト ボックスに書き込むには  
  
1.  **\[ソリューション エクスプローラー\]** で **\[ThisDocument\]** を右クリックし、ショートカット メニューの **\[コードの表示\]** をクリックします。  
  
2.  ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#7)]  
  
3.  C\# では、ボタンのイベント ハンドラーを <xref:Microsoft.Office.Tools.Word.Document.Startup> イベントに追加する必要があります。  イベント ハンドラーの作成方法の詳細については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」を参照してください。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#8)]  
  
## アプリケーションのテスト  
 これで、文書をテストできるようになりました。ボタンをクリックした時に、メッセージ "**Hello World\!**" がテキスト ボックスに表示されることを確認します。  
  
#### 文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  ボタンをクリックします。  
  
3.  テキスト ボックスに **Hello World\!** と表示されることを確認します。  
  
## 次の手順  
 このチュートリアルでは、Word 文書でボタンとテキスト ボックスを使用する際の基本事項について説明しました。  ここでは、次の作業を行います。  
  
-   コンボ ボックスを使用して書式設定を変更する。  詳細については、「[チュートリアル : CheckBox コントロールを使用したドキュメント書式の変更](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)」を参照してください。  
  
-   オプション ボタンを使用してグラフのスタイルを選択する。  詳細については、「[チュートリアル : オプション ボタンを使用してドキュメントのグラフを更新する方法](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)」を参照してください。  
  
## 参照  
 [Office ドキュメントでの Windows フォーム コントロールの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Word を使用したチュートリアル](../vsto/walkthroughs-using-word.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [方法 : Office ドキュメントに Windows フォーム コントロールを追加する](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
  