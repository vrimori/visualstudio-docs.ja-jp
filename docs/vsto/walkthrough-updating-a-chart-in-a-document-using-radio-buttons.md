---
title: "チュートリアル : オプション ボタンを使用してドキュメントのグラフを更新する方法"
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
  - "コントロール [Visual Studio での Office 開発], 更新 (ドキュメントを)"
  - "ドキュメント [Visual Studio での Office 開発], 更新 (コントロールを使用して)"
ms.assetid: 56e6d1f2-65a4-41f0-aff5-f0cfd96d7185
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# チュートリアル : オプション ボタンを使用してドキュメントのグラフを更新する方法
  このチュートリアルでは、Microsoft Office Word のドキュメント レベルのカスタマイズでオプション ボタンを使用して、文書上でグラフのスタイルを選択するオプションをユーザーに提供する方法を示します。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   デザイン時におけるドキュメント レベルのプロジェクトの文書へのグラフの追加  
  
-   ユーザー コントロールへの追加によるオプション ボタンのグループ化  
  
-   オプション選択時のグラフ スタイルの変更  
  
 完成したサンプルとして結果を確認するには、[Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md) で Word コントロールのサンプルを参照してください。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## プロジェクトの作成  
 最初に、Word 文書のプロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  **My Chart Options** という名前の Word 文書プロジェクトを作成します。  ウィザードで、**\[新規ドキュメントの作成\]** をクリックします。  詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     新しい Word 文書が Visual Studio のデザイナーに開かれ、**My Chart Options** プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## 文書へのグラフの追加  
  
#### グラフを追加するには  
  
1.  Visual Studio デザイナーでホストされている Word 文書のリボンで **\[挿入\]** タブをクリックします。  
  
2.  **\[テキスト\]** グループで **\[オブジェクトの挿入\]** ドロップダウン ボタンをクリックし、**\[オブジェクト\]** をクリックします。  
  
     **\[オブジェクト\]** ダイアログ ボックスが開きます。  
  
3.  **\[新規作成\]** タブの **\[オブジェクトの種類\]** リストで **\[Microsoft Graph グラフ\]** を選択して **\[OK\]** をクリックします。  
  
     文書のカーソル位置にグラフが追加され、**\[データシート\]** ウィンドウに既定のデータが表示されます。  
  
4.  **\[データシート\]** ウィンドウを閉じてグラフの既定値を使用することを承認し、文書の中をクリックしてグラフからフォーカスを移動します。  
  
5.  グラフを右クリックし、**\[オブジェクトの書式設定\]** をクリックします。  
  
6.  **\[オブジェクトの書式設定\]** ダイアログ ボックスの **\[レイアウト\]** タブで **\[四角\]** を選択し、**\[OK\]** をクリックします。  
  
## プロジェクトへのユーザー コントロールの追加  
 文書のオプション ボタンは、既定では 1 つしか指定できないようになっています。  オプション ボタンをユーザー コントロールに追加し、選択を制御するためのコードを記述することによって、オプション ボタンを機能させることができます。  
  
#### ユーザー コントロールを追加するには  
  
1.  **ソリューション エクスプローラー**で **\[My Chart Options\]** プロジェクトを選択します。  
  
2.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
3.  **\[新しい項目の追加\]** ダイアログ ボックスで **\[ユーザー コントロール\]** をクリックし、コントロールに「**ChartOptions**」という名前を指定して **\[追加\]** をクリックします。  
  
#### Windows フォームのコントロールをユーザー コントロールへ追加するには  
  
1.  デザイナーにユーザー コントロールが表示されていない場合は、**ソリューション エクスプローラー**で **\[ChartOptions\]** をクリックします。  
  
2.  **\[ツールボックス\]** の **\[コモン コントロール\]** タブから、最初の **\[オプション ボタン\]** コントロールをユーザー コントロールへドラッグし、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |**名前**|**columnChart**|  
    |**Text**|Column Chart|  
  
3.  2 番目の **\[オプション ボタン\]** をユーザー コントロールへ追加し、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |**名前**|**barChart**|  
    |**Text**|Bar Chart|  
  
4.  3 番目の **\[オプション ボタン\]** をユーザー コントロールへ追加し、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |**名前**|**lineChart**|  
    |**Text**|Line Chart|  
  
5.  4 番目の **\[オプション ボタン\]** をユーザー コントロールへ追加し、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |**名前**|**areaBlockChart**|  
    |**Text**|Area Block Chart|  
  
## 参照の追加  
 文書のユーザー コントロールからグラフにアクセスするには、プロジェクト内に Microsoft.Office.Interop.Graph アセンブリへの参照が必要です。  
  
#### Microsoft.Office.Interop.Graph アセンブリへの参照を追加するには  
  
1.  **\[プロジェクト\]** メニューの **\[参照の追加\]** をクリックします。  
  
     **\[参照の追加\]** ダイアログ ボックスが表示されます。  
  
2.  **\[.NET\]** タブで **\[Microsoft.Office.Interop.Graph\]** をクリックし、**\[OK\]** をクリックします。  アセンブリの 14.0.0.0 バージョンを選択します。  
  
## オプション ボタンが選択されたときのグラフ スタイルの変更  
 ボタンを正しく動作させるために、ユーザー コントロールにパブリック イベントを作成し、選択の種類を設定するプロパティを追加して、各オプション ボタンの `CheckedChanged` イベントにプロシージャを作成します。  
  
#### ユーザー コントロールにイベントおよびプロパティを作成するには  
  
1.  **ソリューション エクスプローラー**でユーザー コントロールを右クリックし、**\[コードの表示\]** をクリックします。  
  
2.  `SelectionChanged` イベントと `Selection` プロパティを作成するコードを `ChartOptions` クラスに追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#9)]  
  
#### オプション ボタンの CheckedChange イベントを処理するには  
  
1.  `areaBlockChart` オプション ボタンの `CheckedChanged` イベント ハンドラーでグラフの種類を設定し、イベントを発生させます。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#10)]  
  
2.  `barChart` オプション ボタンの `CheckedChanged` イベント ハンドラーでグラフの種類を設定します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#11)]  
  
3.  `columnChart` オプション ボタンの `CheckedChanged` イベント ハンドラーでグラフの種類を設定します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#12)]  
  
4.  `lineChart` オプション ボタンの `CheckedChanged` イベント ハンドラーでグラフの種類を設定します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#13)]  
  
5.  C\# では、オプション ボタンに対してイベント ハンドラーを追加する必要があります。  このコードを、`InitializeComponent` への呼び出しの後で `ChartOptions` コンストラクターに追加できます。  イベンド ハンドラーの作成方法の詳細については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」を参照してください。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#14)]  
  
## 文書へのユーザー コントロールの追加  
 ソリューションをビルドすると、新しいユーザー コントロールが自動的に**ツールボックス**に追加されます。  このコントロールは**ツールボックス**から文書へドラッグできます。  
  
#### 文書にユーザー コントロールを追加するには  
  
1.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
     **ChartOptions** ユーザー コントロールが**ツールボックス**に追加されます。  
  
2.  **ソリューションエクスプローラー**で **ThisDocument.vb** または **ThisDocument.cs** を右クリックしてから、**\[デザイナーの表示\]** をクリックします。  
  
3.  **ツールボックス**から `ChartOptions` コントロールを文書にドラッグします。  
  
     **\[プロパティ\]** ウィンドウで、文書に追加したばかりのコントロールに `ChartOptions1` という名前を付けます。  
  
## グラフの種類の変更  
 ユーザー コントロールで選択したオプションに基づいてグラフの種類を変更するイベント ハンドラーを作成します。  
  
#### 文書に表示されるグラフの種類を変更するには  
  
1.  次のイベント ハンドラーを `ThisDocument` クラスに追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#15)]  
  
2.  C\# では、ユーザー コントロールのイベント ハンドラーを <xref:Microsoft.Office.Tools.Word.Document.Startup> イベントに追加する必要があります。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#16)]  
  
## アプリケーションのテスト  
 文書をテストして、オプション ボタンを選択したときにグラフのスタイルが正しく更新されることを確認できます。  
  
#### 文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  オプション ボタンを選択するには  
  
3.  選択した内容に合わせてグラフのスタイルが変わることを確認します。  
  
## 次の手順  
 ここでは、次の作業を行います。  
  
-   ボタンを使用してテキスト ボックスへデータを挿入する。  詳細については、「[チュートリアル : ボタンを使用して文書内のテキスト ボックスにテキストを表示する方法](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)」を参照してください。  
  
-   コンボ ボックスからスタイルを選択して書式を変更する。  詳細については、「[チュートリアル : CheckBox コントロールを使用したドキュメント書式の変更](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)」を参照してください。  
  
## 参照  
 [Word を使用したチュートリアル](../vsto/walkthroughs-using-word.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [Office ドキュメントでの Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  