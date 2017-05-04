---
title: "チュートリアル : オプション ボタンを使用してワークシートのグラフを更新する方法 | Microsoft Docs"
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
  - "コントロール [Visual Studio での Office 開発], 更新 (ワークシートを)"
  - "ワークシート, 更新 (マネージ コントロールを使用して)"
  - "ワークシート, オプション ボタンを使用して"
ms.assetid: cacc43a3-6d95-4a47-b943-3457d97a16f8
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# チュートリアル : オプション ボタンを使用してワークシートのグラフを更新する方法
  このチュートリアルでは、Microsoft Office Excel ワークシートでオプション ボタンを使用してオプションをすばやく切り替える際の基本事項について説明します。  ここでは、グラフのスタイルを変更するオプションを扱います。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 この結果として完成したサンプルについては、「[Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)」の Excel コントロールのサンプルを参照してください。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   ワークシートへのオプション ボタン グループの追加  
  
-   オプション選択時のグラフ スタイルの変更  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## ワークシートへのグラフの追加  
 既存のブックをカスタマイズする Excel ブック プロジェクトを作成できます。  このチュートリアルでは、ブックにグラフを追加し、そのブックを新しい Excel ソリューションで使用します。  このチュートリアルで使用するデータ ソースは、**Data for Chart** という名前のワークシートです。  
  
#### データを追加するには  
  
1.  Microsoft Excel を開きます。  
  
2.  **\[Sheet3\]** タブを右クリックし、ショートカット メニューの **\[名前の変更\]** をクリックします。  
  
3.  シートの名前を Data for Chart に変更します。  
  
4.  次のデータを **Data for Chart** に追加します。このとき、左上隅がセル A4、右下隅がセル E8 となるようにします。  
  
    ||Q1|Q2|Q3|Q4|  
    |-|--------|--------|--------|--------|  
    |西|500|550|550|600|  
    |東|600|625|675|700|  
    |北|450|470|490|510|  
    |南|800|750|775|790|  
  
 次に、最初のワークシートにグラフを追加してデータを表示します。  
  
#### Excel でグラフを追加するには  
  
1.  **\[挿入\]** タブの **\[グラフ\]** グループで、**\[縦棒\]** をクリックし、**\[すべてのグラフの種類\]** をクリックします。  
  
2.  **\[グラフの挿入\]** ダイアログ ボックスで、**\[OK\]** をクリックします。  
  
3.  **\[デザイン\]** タブの **\[データ\]** で、**\[データの選択\]** をクリックします。  
  
4.  **\[データ ソースの選択\]** ダイアログ ボックスの **\[グラフ データの範囲\]** ボックス内でクリックし、既定の選択をクリアします。  
  
5.  **Data for Chart** シートで、A4 を左上隅とし E8 を右下隅とする、数値を含んだセル ブロックを選択します。  
  
6.  **\[データ ソースの選択\]** ダイアログ ボックスで、**\[OK\]** をクリックします。  
  
7.  グラフの位置を右上隅がセル **E2** と揃うように調節します。  
  
8.  ドライブCし、それを **\[ExcelChart.xlsx\]**に示すように、ファイルを保存します。  
  
9. Excel を終了します。  
  
## 新規プロジェクトの作成  
 この手順では、**ExcelChart** ブックに基づく Excel ブック プロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  **My Excel Chart** という名前の Excel ブック プロジェクトを作成します。  ウィザードで、**\[既存のドキュメントをコピーする\]** をクリックします。  
  
     詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
2.  **\[参照\]** のボタンをクリックし、このチュートリアルの前半で作成したブックに移動します。  
  
3.  **\[OK\]** をクリックします。  
  
     Visual Studio により、デザイナーで新しい Excel ブックが開き、**My Excel Chart** プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## グラフのプロパティの設定  
 既存のブックを使用する新しい Excel ブック プロジェクトを作成すると、そのブック内にあるすべての名前付き範囲、リスト オブジェクト、およびグラフについて自動的にホスト コントロールが作成されます。  <xref:Microsoft.Office.Tools.Excel.Chart> コントロールの名前は、**\[プロパティ\]** ウィンドウを使用して変更できます。  
  
#### Chart コントロールの名前を変更するには  
  
1.  デザイナーで <xref:Microsoft.Office.Tools.Excel.Chart> コントロールを選択し、**\[プロパティ\]** ウィンドウで以下のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## コントロールの追加  
 このワークシートでは、オプション ボタンを使用して、ユーザーがグラフのスタイルをすばやく変更できるようにします。  ただし、オプション ボタンは一度に 1 つしか選択できないことが必要です。これは、1 つのボタンを選択した場合、同時にグループ内の他のボタンを選択できないことを意味します。  ワークシートに複数のオプション ボタンを追加した場合、既定でこのような動作にはなりません。  
  
 この動作を実現する方法の 1 つとして、オプション ボタンを 1 つのユーザー コントロールにグループ化し、そのユーザー コントロールのコードを作成して、ユーザー コントロールをワークシートに追加することがあります。  
  
#### ユーザー コントロールを追加するには  
  
1.  **ソリューション エクスプローラー**で **My Excel Chart** プロジェクトを選択します。  
  
2.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
3.  **\[新しい項目の追加\]** ダイアログ ボックスで **\[ユーザー コントロール\]** をクリックし、コントロールに **ChartOptions** という名前を指定して、**\[追加\]** をクリックします。  
  
#### ユーザー コントロールにオプション ボタンを追加するには  
  
1.  デザイナーでユーザー コントロールが非表示になっている場合は、**ソリューション エクスプローラー**で **ChartOptions** をダブルクリックします。  
  
2.  **\[ツールボックス\]** の **\[コモン コントロール\]** タブから **\[Radio Button\]** コントロールをユーザー コントロールにドラッグし、以下のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**columnChart**|  
    |**テキスト**|Column Chart|  
  
3.  2 番目のオプション ボタンをユーザー コントロールに追加し、以下のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**barChart**|  
    |**テキスト**|Bar Chart|  
  
4.  3 番目のオプション ボタンをユーザー コントロールに追加し、以下のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**lineChart**|  
    |**テキスト**|Line Chart|  
  
5.  4 番目のオプション ボタンをユーザー コントロールに追加し、以下のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**areaBlockChart**|  
    |**テキスト**|Area Block Chart|  
  
 次に、オプション ボタンがクリックされたときにグラフを更新するコードを記述します。  
  
## オプション ボタンが選択されたときのグラフ スタイルの変更  
 次に、グラフ スタイルを変更するコードを追加します。  これを行うには、ユーザー コントロールにパブリック イベントを作成し、選択の種類を設定するプロパティを追加し、各オプション ボタンの `CheckedChanged` イベントにイベント ハンドラーを作成します。  
  
#### ユーザー コントロールのイベントおよびプロパティを作成するには  
  
1.  **ソリューション エクスプローラー**でユーザー コントロールを右クリックし、**\[コードの表示\]** をクリックします。  
  
2.  `SelectionChanged` イベントと `Selection` プロパティを作成するコードを `ChartOptions` クラスに追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#13)]  
  
#### オプション ボタンの CheckedChanged イベントを処理するには  
  
1.  `areaBlockChart` オプション ボタンの `CheckedChanged` イベント ハンドラーでグラフの種類を設定し、イベントを発生させます。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#14)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#14)]  
  
2.  `barChart` オプション ボタンの `CheckedChanged` イベント ハンドラーで、グラフの種類を設定します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#15)]  
  
3.  `columnChart` オプション ボタンの `CheckedChanged` イベント ハンドラーで、グラフの種類を設定します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#16)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#16)]  
  
4.  `lineChart` オプション ボタンの `CheckedChanged` イベント ハンドラーで、グラフの種類を設定します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#17)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#17)]  
  
5.  C\# では、オプション ボタンのイベント ハンドラーを追加する必要があります。  このコードを `ChartOptions` コンストラクターの `InitializeComponent` の呼び出しの後に追加できます。  イベント ハンドラーの作成方法については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」を参照してください。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#18)]  
  
## ワークシートへのユーザー コントロールの追加  
 ソリューションをビルドすると、新しいユーザー コントロールは自動的に**ツールボックス**に追加されます。  このコントロールは、**\[ツールボックス\]** からワークシートにドラッグできます。  
  
#### ユーザー コントロールをワークシートに追加するには  
  
1.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
     **ChartOptions** ユーザー コントロールが**ツールボックス**に追加されます。  
  
2.  **ソリューション エクスプローラー**で **Sheet1.vb** または **Sheet1.cs** を右クリックし、**\[デザイナーの表示\]** をクリックします。  
  
3.  **ツールボックス**から **ChartOptions** コントロールをワークシートにドラッグします。  
  
     `my_Excel_Chart_ChartOptions1` という名前の新しいコントロールがプロジェクトに追加されます。  
  
4.  コントロールの名前を ChartOptions1 に変更します。  
  
## グラフの種類の変更  
 グラフの種類を変更するには、ユーザー コントロールで選択されたオプションに基づいてスタイルを設定するイベント ハンドラーを作成します。  
  
#### ワークシートに表示されるグラフの種類を変更するには  
  
1.  `Sheet1` クラスに以下のイベント ハンドラーを追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#19)]  
  
2.  C\# では、次に示すように、ユーザー コントロールのイベント ハンドラーを <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> イベントに追加する必要があります。  イベント ハンドラーの作成方法については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」を参照してください。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#20)]  
  
## アプリケーションのテスト  
 ブックをテストして、オプション ボタンを選択したときにグラフのスタイルが正しく設定されることを確認できます。  
  
#### ブックをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  各種のオプション ボタンを選択します。  
  
3.  選択に合わせてグラフ スタイルが変更されることを確認します。  
  
## 次の手順  
 このチュートリアルでは、ワークシートでオプション ボタンとグラフ スタイルを使用するときの基本事項について説明します。  次に行う作業は以下のとおりです。  
  
-   プロジェクトの配置。  詳細については、「[Office ソリューションの配置](../vsto/deploying-an-office-solution.md)」を参照してください。  
  
-   ボタンを使用したテキスト ボックスへのデータの読み込み。  詳細については、「[チュートリアル : ボタンを使用してワークシート内テキスト ボックスにテキストを表示する方法](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)」を参照してください。  
  
-   チェック ボックスを使用したワークシートの書式の変更。  詳細については、「[チュートリアル : CheckBox コントロールを使用したワークシート書式の変更](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)」を参照してください。  
  
## 参照  
 [Excel を使用したチュートリアル](../vsto/walkthroughs-using-excel.md)  
  
  