---
title: "チュートリアル : NamedRange コントロールのイベントのプログラミング
"
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
  - "NamedRange コントロール, イベント"
  - "範囲, プログラミング (イベントに対して)"
  - "ワークシート, 自動化"
  - "ワークシート, 変更 (セル値を)"
  - "ワークシート, イベント"
ms.assetid: b69676f9-23b2-4ed6-83ab-8868c3f10948
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 56
---
# チュートリアル : NamedRange コントロールのイベントのプログラミング

  Microsoft Office Excel ワークシートに <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを追加し、Visual Studio の Office 開発ツールを使用してそのコントロールのイベントをプログラミングする手順を説明します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   ワークシートへの <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールの追加  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールのイベントのプログラミング  
  
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
  
1.  My Named Range Events という名前の Excel ブック プロジェクトを作成します。  **\[新規ドキュメントの作成\]** が選択されていることを確認します。  詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     Visual Studio により、デザイナーで新しい Excel ブックが開き、My Named Range Events プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## ワークシートへのテキストと名前付き範囲の追加  
 ホスト コントロールは Office オブジェクトを拡張したものであり、ネイティブ オブジェクトをドキュメントに追加するのと同じ方法でドキュメントに追加できます。  たとえば、Excel の <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールをワークシートに追加するには、**\[挿入\]** メニューの **\[名前\]** をポイントし、**\[定義\]** をクリックします。  **ツールボックス**から <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールをワークシートにドラッグして追加することもできます。  
  
 この手順では、**ツールボックス**を使用して 2 つの名前付き範囲コントロールをワークシートに追加し、その後でワークシートにテキストを追加します。  
  
#### ワークシートに範囲を追加するには  
  
1.  **\[My Named Range Events.xlsx\]** ブックがVisual Studioのデザイナーで開かれ、`Sheet1` と、表示されることを確認します。  
  
2.  ツールボックスの **\[Excel コントロール\]** タブから、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを `Sheet1` のセル **A1** にドラッグします。  
  
     **\[NamedRange コントロールの追加\]** ダイアログ ボックスが表示されます。  
  
3.  編集可能なテキスト ボックスに "**$A$1**" と表示され、セル **A1** が選択されていることを確認します。  選択されていない場合は、セル **A1** をクリックして選択します。  
  
4.  **\[OK\]** をクリックします。  
  
     セル **A1** が、`namedRange1` という名前の範囲になります。  ワークシート上には範囲を示す表示はありませんが、セル **A1** の選択時に `namedRange1` が **\[名前ボックス\]**\(左側のワークシートのすぐ上\) に表示されます。  
  
5.  セル **B3** に、もう 1 つの <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを追加します。  
  
6.  編集可能なテキスト ボックスに "**$B$3**" と表示され、セル **B3** が選択されていることを確認します。  選択されていない場合は、セル **B3** をクリックして選択します。  
  
7.  **\[OK\]** をクリックします。  
  
     セル **B3** が、`namedRange2` という名前の範囲になります。  
  
#### ワークシートにテキストを追加するには  
  
1.  セル **A1** に以下のテキストを入力します。  
  
     This is an example of a NamedRange control.  
  
2.  セル **A3** \(`namedRange2` の左側\) に以下のテキストを入力します。  
  
     Events:  
  
 以下の各セクションでは、`namedRange1` の <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> イベント、<xref:Microsoft.Office.Tools.Excel.NamedRange.Change> イベント、および <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> イベントに応答して、`namedRange2` にテキストを挿入し、`namedRange2` コントロールのプロパティを変更するコードを記述します。  
  
## BeforeDoubleClick イベントに応答するコードを追加するには  
  
#### BeforeDoubleClick イベントに基づいて NamedRange2 にテキストを挿入するには  
  
1.  **ソリューション エクスプローラー**で **Sheet1.vb** または **Sheet1.cs** を右クリックし、**\[コードの表示\]** をクリックします。  
  
2.  `namedRange1_BeforeDoubleClick` イベント ハンドラーに次のようにコードを追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#24)]  
  
3.  C\# では、次の <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> イベントで示すとおり、名前付き範囲のイベント ハンドラーを追加する必要があります。  イベント ハンドラーの作成については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」を参照してください。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#25)]  
  
## Change イベントに応答するコードの追加  
  
#### Change イベントに基づいて namedRange2 にテキストを挿入するには  
  
1.  `NamedRange1_Change` イベント ハンドラーに次のようにコードを追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Excel の範囲にあるセルをダブルクリックすると編集モードになるので、選択が範囲の外に移動すると、テキストは変更されていなくても <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> イベントが発生します。  
  
## SelectionChange イベントに応答するコードの追加  
  
#### SelectionChange イベントに基づいて namedRange2 にテキストを挿入するには  
  
1.  **NamedRange1\_SelectionChange** イベント ハンドラーに次のようにコードを追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Excel の範囲にあるセルをダブルクリックすると選択が範囲内に移動するので、<xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> イベントが発生する前に <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> イベントが発生します。  
  
## アプリケーションのテスト  
 ここで、ブックをテストして、イベントが発生したときに <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールのイベントを示すテキストがもう 1 つの名前付き範囲に挿入されることを確認できます。  
  
#### 文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  `namedRange1` にカーソルを置き、<xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> イベントに関するテキストが挿入されており、ワークシートにコメントが挿入されていることを確認します。  
  
3.  `namedRange1` 内をダブルクリックし、<xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> イベントに関するテキストが赤い斜体文字で `namedRange2` に挿入されることを確認します。  
  
4.  `namedRange1` の外部をクリックし、編集モードを終了すると、テキストは変更されていなくても Change イベントが発生することを確認します。  
  
5.  `namedRange1` 内のテキストを変更します。  
  
6.  `namedRange1` の外部をクリックし、<xref:Microsoft.Office.Tools.Excel.NamedRange.Change> イベントに関するテキストが青い文字で `namedRange2` に挿入されることを確認します。  
  
## 次の手順  
 このチュートリアルは、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールのイベントについてプログラムを記述する際の基本事項を示しています。  次は、以下の作業を行います。  
  
-   プロジェクトの配置。  詳細については、「[Office ソリューションの配置](../vsto/deploying-an-office-solution.md)」を参照してください。  
  
## 参照  
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [方法 : NamedRange コントロールのサイズを変更する](../vsto/how-to-resize-namedrange-controls.md)   
 [方法 : ワークシートに NamedRange コントロールを追加する](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  