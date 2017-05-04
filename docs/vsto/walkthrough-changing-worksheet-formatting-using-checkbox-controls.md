---
title: "チュートリアル : CheckBox コントロールを使用したワークシート書式の変更 | Microsoft Docs"
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
  - "コントロール [Visual Studio での Office 開発], 追加 (ワークシートに)"
  - "ワークシート, 変更 (マネージ コントロールを使って書式設定を)"
  - "ワークシート, チェック ボックス コントロール"
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# チュートリアル : CheckBox コントロールを使用したワークシート書式の変更
  このチュートリアルでは、Microsoft Office Excel ワークシートでチェック ボックスを使用して、書式を変更する際の基本事項について説明します。  Visual Studio の Office 開発ツールを使用して、コードを作成し、プロジェクトに追加します。  この結果として完成したサンプルについては、「[Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)」の Excel コントロールのサンプルを参照してください。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   ワークシートにテキストやコントロールを追加します。  
  
-   オプション選択時にテキストを書式設定します。  
  
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
  
1.  My Excel Formatting という名前で Excel ブックのプロジェクトを作成します。  **\[新規ドキュメントの作成\]** が選択されていることを確認します。  詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     新しい Excel ブックが Visual Studio のデザイナーに開かれ、**\[My Excel Formatting\]** プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## ワークシートへのテキストとコントロールの追加  
 このチュートリアルでは、3 つの <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> コントロール、および <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロール内のテキストが必要です。  
  
#### 3 つのチェック ボックスを追加するには  
  
1.  ブックが Visual Studio のデザイナーで開かれ、`Sheet1` が開かれていることを確認します。  
  
2.  **ツールボックス**の **\[コモン コントロール\]** タブから <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> コントロールを **\[Sheet1\]** のセル **B2** の内側または近辺にドラッグします。  
  
3.  **\[表示\]** メニューの **\[プロパティ\]** ウィンドウをクリックします。  
  
4.  **\[プロパティ\]** ウィンドウのオブジェクト名リスト ボックスに **\[Checkbox1\]** が表示されていることを確認し、次のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**applyBoldFont**|  
    |**テキスト**|太字|  
  
5.  2 番目のチェック ボックスをセル **B4** の内部または近辺にドラッグし、次のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**applyItalicFont**|  
    |**テキスト**|イタリック体|  
  
6.  3 番目のチェック ボックスをセル **B6** の内部または近辺にドラッグし、次のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**applyUnderlineFont**|  
    |**テキスト**|Underline|  
  
7.  Ctrl キーを押しながら、3 つのチェック ボックス コントロールを選択します。  
  
8.  Excel形式の配置のタブのグループで、**\[配置\]**をクリックし、**\[左揃え\]**をクリックします。  
  
     3種類のチェック ボックス コントロールは、選択した最初のコントロールの位置の左側に配置されます。  
  
     次に、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールをワークシートにドラッグします。  
  
    > [!NOTE]  
    >  **\[名前ボックス\]** に「**textFont**」と入力しても <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを追加できます。  
  
#### テキストを NamedRange コントロールに追加するには  
  
1.  ツールボックスの **\[Excel コントロール\]** タブから <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールをセル **B9** にドラッグします。  
  
2.  編集可能なテキスト ボックスに **\[$B$10\]** と表示され、セル **B9** が選択されていることを確認します。  選択されていない場合は、セル **B9** をクリックして選択します。  
  
3.  **\[OK\]** をクリックします。  
  
4.  セル **B9** は、`NamedRange1` という名前の範囲になります。  
  
     ワークシート上には範囲を示す表示はありませんが、セル **B9** の選択時に `NamedRange1` が **\[名前ボックス\]**\(左側のワークシートのすぐ上\) に表示されます。  
  
5.  **\[プロパティ\]** ウィンドウのオブジェクト名リスト ボックスに **\[NamedRange1\]** が表示されていることを確認し、次のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**textFont**|  
    |**Value2**|チェック ボックスをクリックしてこのテキストの書式を変更します。|  
  
 次に、オプションの選択時にテキストに書式を設定するコードを記述します。  
  
## オプション選択時のテキストへの書式設定  
 ここでは、ユーザーが書式設定オプションを選択したときにワークシート内のテキストの書式が変更されるようにするコードを記述します。  
  
#### チェック ボックス選択時に書式を変更するには  
  
1.  **\[Sheet1\]** を右クリックし、ショートカット メニューの **\[コードの表示\]** をクリックします。  
  
2.  `applyBoldFont` チェック ボックスの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#7)]  
  
3.  `applyItalicFont` チェック ボックスの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#8)]  
  
4.  `applyUnderlineFont` チェック ボックスの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#9)]  
  
5.  C\# では、次に示すように、チェック ボックスのイベント ハンドラーを <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> イベントに追加する必要があります。  イベント ハンドラーの作成については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」を参照してください。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#10)]  
  
## アプリケーションのテスト  
 ブックをテストして、チェック ボックスをオンまたはオフにしたときにテキストの書式が正しく設定されることを確認できます。  
  
#### ブックをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  チェック ボックスをオンまたはオフにします。  
  
3.  テキストの書式が正しく設定されることを確認します。  
  
## 次の手順  
 このチュートリアルでは、Excel ワークシートでのチェック ボックスの使用とテキストの書式設定に関する基本事項について説明します。  次に行う作業は以下のとおりです。  
  
-   プロジェクトの配置。  詳細については、「[ClickOnce を使用した Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)」を参照してください。  
  
-   ボタンを使用したテキスト ボックスへのデータの読み込み。  詳細については、「[チュートリアル : ボタンを使用してワークシート内テキスト ボックスにテキストを表示する方法](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)」を参照してください。  
  
## 参照  
 [Excel を使用したチュートリアル](../vsto/walkthroughs-using-excel.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [Office ドキュメントでの Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  