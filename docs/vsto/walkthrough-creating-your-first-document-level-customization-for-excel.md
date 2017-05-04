---
title: "チュートリアル : 初めての Excel 用ドキュメント レベルのカスタマイズの作成 | Microsoft Docs"
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
  - "ドキュメント レベルのカスタマイズ [Visual Studio での Office 開発], 作成 (初めてのプロジェクトを)"
  - "Excel [Visual Studio での Office 開発], 作成 (初めてのプロジェクトを)"
  - "Visual Studio での Office 開発, 作成 (初めてのプロジェクトを)"
ms.assetid: 785d3b86-5ed5-4e0d-b5ee-896b6b1330ac
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# チュートリアル : 初めての Excel 用ドキュメント レベルのカスタマイズの作成
  この入門編のチュートリアルでは、Microsoft Office Excel 用のドキュメント レベルのカスタマイズを作成する方法について説明します。  この種のソリューションで作成した機能は、特定のブックが開いている場合にのみ使用可能です。  ドキュメント レベルのカスタマイズでは、ブックが開いたときに新しいリボン タブを表示するなどの、アプリケーション全体の変更を行うことはできません。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   Excel ブック プロジェクトを作成する。  
  
-   Visual Studio デザイナーでホストされるワークシートにテキストを追加する。  
  
-   カスタマイズされたワークシートが開かれたときに Excel のオブジェクト モデルを使用してテキストを追加するコードを記述する。  
  
-   テストを行うためにプロジェクトをビルドし、実行する。  
  
-   完成したプロジェクトをクリーンアップして、不要なビルド ファイルやセキュリティ設定を開発用コンピューターから削除する。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## プロジェクトの作成  
  
#### Visual Studio で新しい Excel ブック プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
3.  テンプレート ペインで、**\[Visual C\#\]** または **\[Visual Basic\]** を展開してから、**\[Office\/SharePoint\]** を展開します。  
  
4.  展開した **\[Office\/SharePoint\]** ノードの下で、**\[Office Add\-ins\]** ノードを選択します。  
  
5.  プロジェクト テンプレートの一覧で、Excel VSTO アドイン プロジェクトを選択します。  
  
6.  **\[名前\]** ボックスに「**FirstWorkbookCustomization**」と入力します。  
  
7.  **\[OK\]** をクリックします。  
  
     **Visual Studio Tools for Office プロジェクト ウィザード**が開きます。  
  
8.  **\[新しいドキュメントを作成する\]** を選択し、**\[OK\]** をクリックします。  
  
    -   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] により **FirstWorkbookCustomization** プロジェクトが作成され、次のファイルがプロジェクトに追加されます。  
  
    -   *FirstWorkbookCustomization*.xlsx は、プロジェクト内の Excel ブックを表します。  すべてのワークシートとグラフが含まれます。  
  
    -   Sheet1 \(Visual Basic では .vb ファイル、Visual C\# では .cs ファイル\) は、ブックの最初のワークシートのデザイン画面とコードを提供します。  詳細については、「[Worksheet ホスト項目](../vsto/worksheet-host-item.md)」を参照してください。  
  
    -   Sheet2 \(Visual Basic では .vb ファイル、Visual C\# では .cs ファイル\) は、ブックの 2 番目のワークシートのデザイン画面とコードを提供します。  
  
    -   Sheet3 \(Visual Basic では .vb ファイル、Visual C\# では .cs ファイル\) は、ブックの 3 番目のワークシートのデザイン画面とコードを提供します。  
  
    -   ThisWorkbook \(Visual Basic では .vb ファイル、Visual C\# では .cs ファイル\) には、ブック レベルのカスタマイズのデザイン画面とコードが含まれます。  詳細については、「[Workbook ホスト項目](../vsto/workbook-host-item.md)」を参照してください。  
  
     デザイナーで、Sheet1 コード ファイルが自動的に開かれます。  
  
## デザイナーでワークシートを閉じ、再び開く  
 プロジェクトの開発中にデザイナーで開いたブックまたはワークシートを意図的にまたは誤って閉じた場合は、それを再び開くことができます。  
  
#### デザイナーでワークシートを閉じ、再び開くには  
  
1.  デザイナー ウィンドウの **\[閉じる\]** ボタン \(X\) をクリックしてブックを閉じます。  
  
2.  **ソリューション エクスプローラー**で、**Sheet1** コード ファイルを右クリックし、**\[デザイナーの表示\]** をクリックします。  
  
     または  
  
     **ソリューション エクスプローラー**で **Sheet1** コード ファイルをダブルクリックします。  
  
## デザイナーによるワークシートへのテキストの追加  
 デザイナーで開いたワークシートを変更することで、カスタマイズのユーザー インターフェイス \(UI\) をデザインできます。  たとえば、セルにテキストを追加したり、式を適用したり、Excel のコントロールを追加したりできます。  デザイナーの使用方法の詳細については、「[Visual Studio 環境における Office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)」を参照してください。  
  
#### デザイナーを使用してワークシートにテキストを追加するには  
  
1.  デザイナーで開かれているワークシートで、セル **A1** を選択してから、次のテキストを入力します。  
  
     **This text was added by using the designer.**  
  
> [!WARNING]  
>  このテキスト行をセル **A2** に追加する場合、この例では、他のコードにより上書きされます。  
  
## プログラムによってテキストをワークシートに追加する  
 次に、Sheet1 コード ファイルにコードを追加します。  この新しいコードでは、Excel のオブジェクト モデルを使用して、ブックに 2 行目のテキストを追加します。  Sheet1 コード ファイルには、次の生成コードが既定で含まれています。  
  
-   `Sheet1` クラスの部分定義。このクラスは、ワークシートのプログラミング モデルを表し、Excel のオブジェクト モデルへのアクセスを提供します。  詳細については、「[Worksheet ホスト項目](../vsto/worksheet-host-item.md)」および「[Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)」を参照してください。  `Sheet1` クラスの残りの部分は、変更することができない非表示のコード ファイルに定義されています。  
  
-   `Sheet1_Startup` および `Sheet1_Shutdown` イベント ハンドラー。  これらのイベント ハンドラーは、Excel がユーザーのカスタマイズを読み込むときとアンロードするときに呼び出されます。  これらのイベント ハンドラーを使用して、読み込まれるときにはカスタマイズを初期化し、アンロードされるときにはカスタマイズが使用したリソースをクリーンアップします。  詳細については、「[Office プロジェクトのイベント](../vsto/events-in-office-projects.md)」を参照してください。  
  
#### コードを使用してワークシートに 2 行目のテキストを追加するには  
  
1.  **ソリューション エクスプローラー**で **Sheet1** を右クリックし、**\[コードの表示\]** をクリックします。  
  
     Visual Studio でコード ファイルが開かれます。  
  
2.  `Sheet1_Startup` イベント ハンドラーを次のコードで置き換えます。  Sheet1 が開かれると、このコードは、ワークシートに 2 行目のテキストを追加します。  
  
     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookTutorial/CS/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookTutorial/VB/Sheet1.vb#1)]  
  
## プロジェクトのテスト  
  
#### ブックをテストするには  
  
1.  **F5** キーを押して、プロジェクトをビルドおよび実行します。  
  
     プロジェクトをビルドすると、コードがアセンブリにコンパイルされ、ブックに関連付けられます。  Visual Studio は、ブックおよびアセンブリのコピーをプロジェクトのビルド出力フォルダーに格納し、カスタマイズを実行できるように開発用コンピューターのセキュリティ設定を行います。  詳細については、「[Office ソリューションのビルド](../vsto/building-office-solutions.md)」を参照してください。  
  
2.  次のテキストがブックに表示されることを確認します。  
  
     **This text was added by using the designer.**  
  
     **This text was added by using code.**  
  
3.  ブックを閉じます。  
  
## プロジェクトのクリーンアップ  
 プロジェクトの開発が完了したら、ビルド プロセスによって作成されたビルド出力フォルダー内のファイルおよびセキュリティ設定を削除する必要があります。  
  
#### 開発用コンピューターから完成したプロジェクトをクリーンアップするには  
  
1.  Visual Studio で、**\[ビルド\]** メニューの **\[ソリューションのクリーン\]** をクリックします。  
  
## 次の手順  
 Excel 用の基本的なドキュメント レベルのカスタマイズを作成したので、カスタマイズ開発の詳細な方法について、以下のトピックを参照してください。  
  
-   ドキュメント レベルのカスタマイズで実行できる一般的なプログラミング タスク: [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)。  
  
-   Excel 用のドキュメント レベルのカスタマイズに固有のプログラミング タスク: [Excel ソリューション](../vsto/excel-solutions.md)。  
  
-   Excel のオブジェクト モデルの使用: [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)  
  
-   Excel の UI のカスタマイズ \(リボンへのカスタム タブの追加や独自のカスタム作業ウィンドウの作成など\): [Office UI のカスタマイズ](../vsto/office-ui-customization.md)。  
  
-   Visual Studio の Office ソリューションで提供される拡張 Excel オブジェクトを使用して、Excel オブジェクト モデルを使用して実行できないタスクを実行する \(たとえば、ドキュメント上でマネージ コントロールをホストする、Windows フォーム データ バインディング モデルを使用して Excel コントロールをデータにバインドするなど\): [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)。  
  
-   Excel 用のドキュメント レベルのカスタマイズのビルドとデバッグ: [Office ソリューションのビルド](../vsto/building-office-solutions.md)。  
  
-   Excel 用のドキュメント レベルのカスタマイズの配置: [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)。  
  
## 参照  
 [Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Excel ソリューション](../vsto/excel-solutions.md)   
 [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)   
 [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office ソリューションのビルド](../vsto/building-office-solutions.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)  
  
  