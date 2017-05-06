---
title: "チュートリアル : ボタンを使用してワークシート内テキスト ボックスにテキストを表示する方法"
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
  - "テキスト [Visual Studio での Office 開発], 表示 (ワークシートを)"
  - "テキスト [Visual Studio での Office 開発], テキスト ボックス"
  - "テキスト ボックス, 表示 (ワークシートにテキストを)"
  - "ワークシート, 表示 (テキストを)"
ms.assetid: 59b73159-aab7-4f61-9ace-1723c18d78d6
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# チュートリアル : ボタンを使用してワークシート内テキスト ボックスにテキストを表示する方法
  このチュートリアルでは、Microsoft Office Excel ワークシートでボタンとテキスト ボックスを使用する際の基本事項と、Visual Studio の Office 開発ツールを使用して Excel プロジェクトを作成する方法について説明します。  この結果として完成したサンプルについては、「[Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)」の Excel コントロールのサンプルを参照してください。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   ワークシートにコントロールを追加します。  
  
-   ボタンがクリックされたときにテキスト ボックスに値を設定します。  
  
-   プロジェクトのテスト  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## プロジェクトの作成  
 この手順では、Visual Studio を使用して Excel ブック プロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  My Excel Button という名前で Excel ブックのプロジェクトを作成します。  **\[新規ドキュメントの作成\]** が選択されていることを確認します。  詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     新しい Excel ブックが Visual Studio のデザイナーで開かれ、**My Excel Button** プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## ワークシートへのコントロールの追加  
 このチュートリアルでは、最初のワークシートにボタンとテキスト ボックスが必要になります。  
  
#### ボタンとテキスト ボックスを追加するには  
  
1.  **\[My Excel Button.xlsx\]** ブックが Visual Studio のデザイナーで開いていると、表示 `Sheet1` ことを確認します。  
  
2.  ツールボックスの **\[コモン コントロール\]** タブで <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> を `Sheet1` にドラッグします。  
  
3.  **\[表示\]** メニューの **\[プロパティ ウィンドウ\]** をクリックします。  
  
4.  **\[プロパティ\]** ウィンドウのドロップダウン ボックスの一覧に **\[textBox1\]** が表示されることを確認し、テキストの **Name** プロパティを **displayText** に変更します。  
  
5.  **Button** コントロールを `Sheet1` にドラッグし、次のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**insertText**|  
    |**テキスト**|Insert Text|  
  
 次に、ボタンがクリックされたときに実行するコードを記述します。  
  
## ボタン クリック時のテキスト ボックスへの値設定  
 ユーザーがボタンをクリックするたびに、**\[Hello World\]\!** は、テキスト ボックスに追加されます。  
  
#### ボタンがクリックされたときにテキスト ボックスに値を書き込むには  
  
1.  **ソリューション エクスプローラー**で **\[Sheet1\]** を右クリックし、ショートカット メニューの **\[コードの表示\]** をクリックします。  
  
2.  ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#11)]  
  
3.  C\# では、次に示すように、イベント ハンドラーを <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> イベントに追加する必要があります。  イベント ハンドラーの作成については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」を参照してください。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#12)]  
  
## アプリケーションのテスト  
 、ボタンのクリック時にメッセージ **\[Hello World\]\!** がテキスト ボックスに表示されることを確認するために、ブックをテストできます。  
  
#### ブックをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  ボタンをクリックします。  
  
3.  **\[Hello World\]\!** がテキスト ボックスに表示されることを確認します。  
  
## 次の手順  
 このチュートリアルでは、Excel ワークシートでボタンとテキスト ボックスを使用するときの基本事項について説明します。  次に行う作業は以下のとおりです。  
  
-   プロジェクトの配置。  詳細については、「[Office ソリューションの配置](../vsto/deploying-an-office-solution.md)」を参照してください。  
  
-   チェック ボックスを使用して書式を変更します。  詳細については、「[チュートリアル : CheckBox コントロールを使用したワークシート書式の変更](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)」を参照してください。  
  
## 参照  
 [方法 : Office ドキュメントに Windows フォーム コントロールを追加する](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Excel を使用したチュートリアル](../vsto/walkthroughs-using-excel.md)   
 [Office ドキュメントでの Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  