---
title: 'チュートリアル: グラフを更新するラジオ ボタンを使用してワークシート内で |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fbdbcc8ae12e1b0f317b53a4f0ffd7e9b2885aec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>チュートリアル : オプション ボタンを使用してワークシートのグラフを更新する方法
  このチュートリアルでは、Microsoft Office Excel ワークシートにオプション ボタンを使用してユーザーに提供する、オプションですばやく切り替える方法の基礎を説明します。 このケースでは、オプションは、グラフのスタイルを変更します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 完成したサンプルの結果を参照してくださいで Excel コントロールのサンプルを参照してください。 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)です。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   ワークシートへのラジオ ボタンのグループを追加します。  
  
-   オプション選択時のグラフ スタイルの変更  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## <a name="adding-a-chart-to-a-worksheet"></a>ワークシートにグラフの追加  
 既存のブックをカスタマイズする Excel ブック プロジェクトを作成することができます。 このチュートリアルでは、ブックにグラフを追加し、新しい Excel ソリューションでこのブックを使用します。 このチュートリアルで、データ ソースがという名前のワークシート**グラフのデータ**です。  
  
#### <a name="to-add-the-data"></a>データを追加するには  
  
1.  Microsoft Excel を開きます。  
  
2.  右クリックし、 **Sheet3** ] タブをクリックして**の名前を変更**ショートカット メニューの [します。  
  
3.  シートの名前**グラフのデータ**です。  
  
4.  次のデータを追加**グラフのデータ**A4 のセルの中で左上隅にあると E8 右下隅です。  
  
    ||第 1 四半期|第 2 四半期|第 3 四半期|第 4 四半期|  
    |-|--------|--------|--------|--------|  
    |西部|500|550|550|600|  
    |東部|600|625|675|700|  
    |北米|450|470|490|510|  
    |南部|800|750|775|790|  
  
 次に、データを表示する最初のワークシートにグラフを追加します。  
  
#### <a name="to-add-a-chart-in-excel"></a>Excel でグラフを追加するには  
  
1.  **挿入** タブの 、**グラフ**グループで、**列**、クリックして**すべてのグラフの種類**です。  
  
2.  **グラフの挿入**ダイアログ ボックスで、をクリックして**OK**です。  
  
3.  **デザイン**] タブで、**データ**グループで、[**データの選択**です。  
  
4.  **データ ソースの選択** ダイアログ ボックス内をクリックし、 **Chartdata 範囲**ボックスし、既定の選択をオフにします。  
  
5.  **グラフのデータ**シートで、左上隅に E8 に右下隅で A4 を含む数値を含むセルのブロックを選択します。  
  
6.  **データ ソースの選択**ダイアログ ボックスで、をクリックして**OK**です。  
  
7.  グラフの右上隅がセルに配置されるよう位置**E2**です。  
  
8.  C ドライブにファイルを保存し、名前を付けます**ExcelChart.xlsx**です。  
  
9. Excel を終了します。  
  
## <a name="creating-a-new-project"></a>新規プロジェクトの作成  
 このステップでは、に基づいて Excel ブック プロジェクトを作成する、 **ExcelChart**ブック。  
  
#### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Excel ブック プロジェクトを作成**個人用の Excel グラフ**です。 ウィザードで、次のように選択します。**ドキュメントをコピーする既存**です。  
  
     詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
2.  クリックして、**参照**ボタンこのチュートリアルで先ほど作成したブックを参照します。  
  
3.  **[OK]**をクリックします。  
  
     デザイナーで新しい Excel ブックを開き、**個人用の Excel グラフ**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="setting-properties-of-the-chart"></a>グラフのプロパティの設定  
 既存のブックを使用する新しい Excel ブック プロジェクトを作成するときに、ホスト コントロールは自動的にすべての名前付き範囲、リスト オブジェクト、および、ブック内のグラフの作成します。 名前を変更することができます、<xref:Microsoft.Office.Tools.Excel.Chart>コントロールを使用して、**プロパティ**ウィンドウです。  
  
#### <a name="to-change-the-name-of-the-chart-control"></a>グラフ コントロールの名前を変更するには  
  
1.  選択、<xref:Microsoft.Office.Tools.Excel.Chart>デザイナーで制御しで次のプロパティを変更、**プロパティ**ウィンドウです。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## <a name="adding-controls"></a>コントロールの追加  
 このワークシートは、グラフのスタイルをすばやく変更するのに方法をユーザーに付与するのにオプション ボタンを使用します。 ただし、オプション ボタンは、排他的である必要があります。-1 つのボタンを選択すると、グループ内の他のボタンを選択できません同時にします。 いくつかのオプション ボタンをワークシートに追加するときは、この動作は既定では発生しません。  
  
 この動作は、ユーザー コントロールのラジオ ボタンのグループを追加する方法の 1 つは、ユーザー コントロールの背後にあるコードを記述し、ワークシートに、ユーザー コントロールを追加します。  
  
#### <a name="to-add-a-user-control"></a>ユーザー コントロールを追加するには  
  
1.  選択、**個人用の Excel グラフ**プロジェクト**ソリューション エクスプ ローラー**です。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
3.  **新しい項目の追加**ダイアログ ボックスで、をクリックして**ユーザー コントロール**、コントロールの名前を付けます**ChartOptions**  をクリック**追加**です。  
  
#### <a name="to-add-radio-buttons-to-the-user-control"></a>ユーザー コントロールにラジオ ボタンを追加するには  
  
1.  ユーザー コントロールがデザイナーで表示されていない場合は、ダブルクリック**ChartOptions**で**ソリューション エクスプ ローラー**です。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**、ドラッグ、**ラジオ ボタン**ユーザー コントロールを制御し、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**付いた円柱グラフ**|  
    |**[テキスト]**|**縦棒グラフ**|  
  
3.  2 番目のオプション ボタンをユーザー コントロールに追加し、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**barChart**|  
    |**[テキスト]**|**横棒グラフ**|  
  
4.  3 番目のオプション ボタンをユーザー コントロールに追加し、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**です折れ線グラフ**|  
    |**[テキスト]**|**線グラフ**|  
  
5.  4 番目のオプション ボタンをユーザー コントロールに追加し、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**areaBlockChart**|  
    |**[テキスト]**|**領域ブロックのグラフ**|  
  
 次に、オプション ボタンがクリックされたときにグラフを更新するコードを記述します。  
  
## <a name="changing-the-chart-style-when-a-radio-button-is-selected"></a>グラフのスタイルと、オプション ボタンの変更が選択されています。  
 今すぐグラフのスタイルを変更するコードを追加できます。 これを行うには、ユーザー コントロールにパブリック イベントを作成、選択の種類を設定するプロパティを追加し、イベント ハンドラーを作成、`CheckedChanged`各ラジオ ボタンのイベントです。  
  
#### <a name="to-create-an-event-and-property-on-a-user-control"></a>ユーザー コントロールにイベントおよびプロパティを作成するには  
  
1.  **ソリューション エクスプ ローラー**ユーザー コントロールを右クリックし、クリックして**コードの表示**です。  
  
2.  コードを追加して、`ChartOptions`クラスを作成する、`SelectionChanged`イベントおよび`Selection`プロパティです。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]  
  
#### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>ラジオ ボタンの CheckedChanged イベントを処理するには  
  
1.  `CheckedChanged` オプション ボタンの `areaBlockChart` イベント ハンドラーでグラフの種類を設定し、イベントを発生させます。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]  
  
2.  `CheckedChanged` オプション ボタンの `barChart` イベント ハンドラーでグラフの種類を設定します。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]  
  
3.  `CheckedChanged` オプション ボタンの `columnChart` イベント ハンドラーでグラフの種類を設定します。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]  
  
4.  `CheckedChanged` オプション ボタンの `lineChart` イベント ハンドラーでグラフの種類を設定します。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]  
  
5.  C# では、オプション ボタンに対してイベント ハンドラーを追加する必要があります。 このコードを、`ChartOptions` への呼び出しの後で `InitializeComponent` コンストラクターに追加できます。 イベント ハンドラーを作成する方法については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]  
  
## <a name="adding-the-user-control-to-the-worksheet"></a>ユーザー コントロールをワークシートに追加します。  
 新しいユーザー コントロールが自動的に追加するソリューションをビルドするときに、**ツールボックス**です。 コントロールをドラッグすることができますし、**ツールボックス**をワークシートにします。  
  
#### <a name="to-add-the-user-control-your-worksheet"></a>ユーザー コントロールをワークシートに追加するには  
  
1.  **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。  
  
     **ChartOptions**にユーザー コントロールを追加、**ツールボックス**です。  
  
2.  **ソリューション エクスプ ローラー**を右クリックして**Sheet1.vb**または**Sheet1.cs**、クリックして**ビュー デザイナー**です。  
  
3.  ドラッグ、 **ChartOptions**から制御、**ツールボックス**ワークシートにします。  
  
     という名前の新しいコントロール`my_Excel_Chart_ChartOptions1`プロジェクトに追加します。  
  
4.  コントロールの名前を変更**ChartOptions1**です。  
  
## <a name="changing-the-chart-type"></a>グラフの種類の変更  
 グラフの種類を変更するには、ユーザー コントロールで選択したオプションに従ってスタイルを設定するイベント ハンドラーを作成します。  
  
#### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>ワークシートに表示されるグラフの種類を変更するには  
  
1.  次のイベント ハンドラーを `Sheet1` クラスに追加します。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]  
  
2.  C# の場合、ユーザー コントロールのイベント ハンドラーを追加する必要があります、<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>イベント次のようにします。 イベント ハンドラーを作成する方法については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 ラジオ ボタンを選択するときに、グラフのスタイルが正しく設定することを確認するブックをテストできます。  
  
#### <a name="to-test-your-workbook"></a>ブックをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  オプション ボタンを選択するには  
  
3.  選択した内容に合わせてグラフのスタイルが変わることを確認します。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、オプション ボタンとグラフのスタイルを使用してワークシート上の基礎を説明します。 ここでは、次のタスクを行います。  
  
-   プロジェクトを配置します。 詳細については、次を参照してください。 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)です。  
  
-   ボタンを使用してテキスト ボックスへデータを挿入する。 詳細については、次を参照してください。[チュートリアル: ボタンを使用してワークシート内のテキスト ボックスに表示するテキスト](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)です。  
  
-   チェック ボックスを使用してワークシートの書式を変更します。 詳細については、次を参照してください。[チュートリアル: 変更ワークシートの書式設定 チェック ボックス コントロールを使用した](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Excel を使用したチュートリアル](../vsto/walkthroughs-using-excel.md)  
  
  