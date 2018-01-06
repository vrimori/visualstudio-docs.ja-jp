---
title: "チュートリアル: グラフを更新するオプション ボタンを使用してドキュメントの |Microsoft ドキュメント"
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
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
ms.assetid: 56e6d1f2-65a4-41f0-aff5-f0cfd96d7185
caps.latest.revision: "60"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 35f5a865faafc730a13f5d0cd3a432a724434dde
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-updating-a-chart-in-a-document-using-radio-buttons"></a>チュートリアル : オプション ボタンを使用してドキュメントのグラフを更新する方法
  このチュートリアルでは、Microsoft Office Word のドキュメント レベルのカスタマイズでオプション ボタンを使用して、文書上でグラフのスタイルを選択するオプションをユーザーに提供する方法を示します。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   デザイン時におけるドキュメント レベルのプロジェクトの文書へのグラフの追加  
  
-   ユーザー コントロールへの追加によるオプション ボタンのグループ化  
  
-   オプション選択時のグラフ スタイルの変更  
  
 完成したサンプルの結果を参照してくださいで Word コントロールのサンプルを参照してください。 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)です。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初に、Word 文書のプロジェクトを作成します。  
  
#### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Word 文書プロジェクトを作成**My Chart Options**です。 ウィザードで、次のように選択します。**新しいドキュメントを作成する**です。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     デザイナーで新しい Word 文書を開き、 **My Chart Options**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-a-chart-to-the-document"></a>文書へのグラフの追加  
  
#### <a name="to-add-a-chart"></a>グラフを追加するには  
  
1.  リボンで、Visual Studio デザイナーでホストされている Word ドキュメント内をクリックして、**挿入**タブです。  
  
2.  **テキスト**グループで、、**オブジェクトの挿入**ドロップダウン ボタンをクリック**オブジェクト**です。  
  
     **オブジェクト** ダイアログ ボックスが表示されます。  
  
3.  **オブジェクトの種類**ボックスの一覧、**新規作成** タブで **Microsoft Graph グラフ** をクリックし、 **ok**です。  
  
     カーソル位置にあるドキュメントにグラフが追加され、**データシート**ウィンドウは、既定のデータが表示されます。  
  
4.  閉じる、**データシート**ウィンドウをグラフの既定値をそのまま使用し、ドキュメント内で、グラフからフォーカスを移動 をクリックします。  
  
5.  グラフを右クリックし、をクリックして**オブジェクトの書式設定**です。  
  
6.  **レイアウト**のタブ、**オブジェクトの書式設定**ダイアログ ボックスで、**正方形** をクリック**OK**。  
  
## <a name="adding-a-user-control-to-the-project"></a>プロジェクトへのユーザー コントロールの追加  
 文書のオプション ボタンは、既定では 1 つしか指定できないようになっています。 オプション ボタンをユーザー コントロールに追加し、選択を制御するためのコードを記述することによって、オプション ボタンを機能させることができます。  
  
#### <a name="to-add-a-user-control"></a>ユーザー コントロールを追加するには  
  
1.  選択、 **My Chart Options**プロジェクト**ソリューション エクスプ ローラー**です。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
3.  **新しい項目の追加**ダイアログ ボックスで、をクリックして**ユーザー コントロール**、コントロールの名前を付けます**ChartOptions**  をクリック**追加**です。  
  
#### <a name="to-add-windows-form-controls-to-the-user-control"></a>Windows フォームのコントロールをユーザー コントロールへ追加するには  
  
1.  ユーザー コントロールがデザイナーで表示されていない場合は、ダブルクリック**ChartOptions**で**ソリューション エクスプ ローラー**です。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**、最初にドラッグ**ラジオ ボタン**ユーザー コントロールを制御し、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**付いた円柱グラフ**|  
    |**[テキスト]**|**縦棒グラフ**|  
  
3.  1 秒あたりの追加**ラジオ ボタン**ユーザーを制御して、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**barChart**|  
    |**[テキスト]**|**横棒グラフ**|  
  
4.  3 つ目の追加**ラジオ ボタン**ユーザーを制御して、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**です折れ線グラフ**|  
    |**[テキスト]**|**線グラフ**|  
  
5.  4 つ目の追加**ラジオ ボタン**をユーザーを制御して、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**areaBlockChart**|  
    |**[テキスト]**|**領域ブロックのグラフ**|  
  
## <a name="adding-references"></a>参照の追加  
 文書のユーザー コントロールからグラフにアクセスするには、プロジェクト内に Microsoft.Office.Interop.Graph アセンブリへの参照が必要です。  
  
#### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Microsoft.Office.Interop.Graph アセンブリへの参照を追加するには  
  
1.  **[プロジェクト]** メニューの **[参照の追加]** をクリックします。  
  
     **[参照の追加]** ダイアログ ボックスが表示されます。  
  
2.  **.NET**  タブで **Microsoft.Office.Interop.Graph** をクリック**OK**です。 アセンブリの 14.0.0.0 バージョンを選択します。  
  
## <a name="changing-the-chart-style-when-a-radio-button-is-selected"></a>オプション ボタンが選択されたときのグラフ スタイルの変更  
 ボタンを正しく動作させるために、ユーザー コントロールにパブリック イベントを作成し、選択の種類を設定するプロパティを追加して、各オプション ボタンの `CheckedChanged` イベントにプロシージャを作成します。  
  
#### <a name="to-create-an-event-and-property-on-a-user-control"></a>ユーザー コントロールにイベントおよびプロパティを作成するには  
  
1.  **ソリューション エクスプ ローラー**ユーザー コントロールを右クリックし、クリックして**コードの表示**です。  
  
2.  `SelectionChanged` イベントと `Selection` プロパティを作成するコードを `ChartOptions` クラスに追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]  
  
#### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>オプション ボタンの CheckedChange イベントを処理するには  
  
1.  `CheckedChanged` オプション ボタンの `areaBlockChart` イベント ハンドラーでグラフの種類を設定し、イベントを発生させます。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]  
  
2.  `CheckedChanged` オプション ボタンの `barChart` イベント ハンドラーでグラフの種類を設定します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]  
  
3.  `CheckedChanged` オプション ボタンの `columnChart` イベント ハンドラーでグラフの種類を設定します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]  
  
4.  `CheckedChanged` オプション ボタンの `lineChart` イベント ハンドラーでグラフの種類を設定します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]  
  
5.  C# では、オプション ボタンに対してイベント ハンドラーを追加する必要があります。 このコードを、`ChartOptions` への呼び出しの後で `InitializeComponent` コンストラクターに追加できます。 イベント ハンドラーの作成方法の詳細については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]  
  
## <a name="adding-the-user-control-to-the-document"></a>文書へのユーザー コントロールの追加  
 新しいユーザー コントロールが自動的に追加するソリューションをビルドするときに、**ツールボックス**です。 コントロールをドラッグすることができますし、**ツールボックス**をドキュメントにします。  
  
#### <a name="to-add-the-user-control-your-document"></a>文書にユーザー コントロールを追加するには  
  
1.  **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。  
  
     **ChartOptions**にユーザー コントロールを追加、**ツールボックス**です。  
  
2.  **ソリューション エクスプ ローラー**を右クリックして**ThisDocument.vb**または**ThisDocument.cs**、クリックして**ビュー デザイナー**です。  
  
3.  ドラッグ、`ChartOptions`から制御、**ツールボックス**ドキュメントにします。  
  
     **プロパティ**ウィンドウで、ドキュメントに追加したコントロール名`ChartOptions1`です。  
  
## <a name="changing-the-chart-type"></a>グラフの種類の変更  
 ユーザー コントロールで選択したオプションに基づいてグラフの種類を変更するイベント ハンドラーを作成します。  
  
#### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>文書に表示されるグラフの種類を変更するには  
  
1.  次のイベント ハンドラーを `ThisDocument` クラスに追加します。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]  
  
2.  C# では、ユーザー コントロールのイベント ハンドラーを <xref:Microsoft.Office.Tools.Word.Document.Startup> イベントに追加する必要があります。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 文書をテストして、オプション ボタンを選択したときにグラフのスタイルが正しく更新されることを確認できます。  
  
#### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  オプション ボタンを選択するには  
  
3.  選択した内容に合わせてグラフのスタイルが変わることを確認します。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、次のタスクを行います。  
  
-   ボタンを使用してテキスト ボックスへデータを挿入する。 詳細については、次を参照してください。[チュートリアル: ボタンを使用してドキュメント内のテキスト ボックスに表示するテキスト](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)です。  
  
-   コンボ ボックスからスタイルを選択して書式を変更する。 詳細については、次を参照してください。[チュートリアル: を変更するドキュメントの書式設定 チェック ボックス コントロールを使用した](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)です。  
  
## <a name="see-also"></a>参照  
 [チュートリアルを使用して Word](../vsto/walkthroughs-using-word.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [Office ドキュメントでの Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  