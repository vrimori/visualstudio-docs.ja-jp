---
title: 'チュートリアル: 初めての Excel 用ドキュメント レベルのカスタマイズを作成します。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ce16e3c2aca99acf6de9a7ce74c0c2ff46c0dcbb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849035"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>チュートリアル: 初めての Excel 用ドキュメント レベルのカスタマイズを作成します。
  この入門編のチュートリアルでは、Microsoft Office Excel 用のドキュメント レベルのカスタマイズを作成する方法について説明します。 この種のソリューションで作成した機能は、特定のブックが開いている場合にのみ使用可能です。 ドキュメント レベルのカスタマイズでは、ブックが開いたときに新しいリボン タブを表示するなどの、アプリケーション全体の変更を行うことはできません。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
- Excel ブック プロジェクトを作成する。  
  
- Visual Studio デザイナーでホストされるワークシートにテキストを追加する。  
  
- カスタマイズされたワークシートが開かれたときに Excel のオブジェクト モデルを使用してテキストを追加するコードを記述する。  
  
- プロジェクトをビルドし、実行してテストする。  
  
- 完成したプロジェクトをクリーンアップして、不要なビルド ファイルやセキュリティ設定を開発用コンピューターから削除する。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## <a name="create-the-project"></a>プロジェクトの作成  
  
### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Visual Studio で新しい Excel ブック プロジェクトを作成するには  
  
1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2. **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
3. テンプレート ペインで、 **[Visual C#]** または **[Visual Basic]** を展開してから、 **[Office/SharePoint]** を展開します。  
  
4. 展開した **[Office/SharePoint]** ノードの下で、 **[Office Add-ins]** ノードを選択します。  
  
5. プロジェクト テンプレートの一覧で、Excel VSTO アドイン プロジェクトを選択します。  
  
6. **名前**ボックスに「 **FirstWorkbookCustomization**します。  
  
7. **[OK]** をクリックします。  
  
    **Visual Studio Tools for Office プロジェクト ウィザード** が開きます。  
  
8. 選択**新しい文書を作成**、 をクリック**OK**します。  
  
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 作成、 **FirstWorkbookCustomization**プロジェクトし、次のファイルをプロジェクトに追加します。  
  
   - *FirstWorkbookCustomization*.xlsx は、プロジェクト内の Excel ブックを表します。 すべてのワークシートとグラフが含まれます。  
  
   - Sheet1 (*.vb* Visual basic のファイルまたは *.cs* Visual c# ファイル) のブック内の最初のワークシートのデザイン画面とコードを提供します。 詳細については、次を参照してください。 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)します。  
  
   - Sheet2 (*.vb* Visual basic のファイルまたは *.cs* Visual c# ファイル)-ブックの 2 番目のワークシートのデザイン画面とコードを提供します。  
  
   - Sheet3 (*.vb* Visual basic のファイルまたは *.cs* Visual c# ファイル) の 3 番目のワークシートをブック内のデザイン画面とコードを提供します。  
  
   - ThisWorkbook (*.vb* Visual basic のファイルまたは *.cs* Visual c# ファイル) のデザイン画面とブック レベルのカスタマイズのコードが含まれています。 詳細については、次を参照してください。 [Workbook ホスト項目](../vsto/workbook-host-item.md)します。  
  
     デザイナーで、Sheet1 コード ファイルが自動的に開かれます。  
  
## <a name="close-and-reopen-worksheets-in-the-designer"></a>デザイナーでワークシートを閉じてから開き  
 プロジェクトの開発中にデザイナーで開いたブックまたはワークシートを意図的にまたは誤って閉じた場合は、それを再び開くことができます。  
  
### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>デザイナーでワークシートを閉じ、再び開くには  
  
1.  クリックしてブックを閉じる、**閉じる**デザイナー ウィンドウのボタン (X)。  
  
2.  **ソリューション エクスプ ローラー**を右クリックし、 **Sheet1**コード ファイル、およびクリックして**ビュー デザイナー**します。  
  
     \- または -  
  
     **ソリューション エクスプ ローラー**、ダブルクリックして、 **Sheet1**コード ファイル。  
  
## <a name="add-text-to-a-worksheet-in-the-designer"></a>デザイナーでワークシートにテキストを追加します。  
 デザイナーで開いたワークシートを変更することで、カスタマイズのユーザー インターフェイス (UI) をデザインできます。 たとえば、セルにテキストを追加したり、式を適用したり、Excel のコントロールを追加したりできます。 デザイナーを使用する方法の詳細については、次を参照してください。 [Visual Studio 環境における Office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)します。  
  
### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>デザイナーを使用してワークシートにテキストを追加するには  
  
1.  デザイナーで開いているワークシートでセルを選択します。 **A1**、し、次のテキストを入力します。  
  
     **このテキストは、デザイナーを使用して追加されました。**  
  
> [!WARNING]  
>  この行のテキストをセルに追加する場合**A2**、この例では、他のコードは上書きされます。  
  
## <a name="add-text-to-a-worksheet-programmatically"></a>プログラムによってワークシートにテキストを追加します。  
 次に、Sheet1 コード ファイルにコードを追加します。 この新しいコードでは、Excel のオブジェクト モデルを使用して、ブックに 2 行目のテキストを追加します。 Sheet1 コード ファイルには、次の生成コードが既定で含まれています。  
  
-   `Sheet1` クラスの部分定義。このクラスは、ワークシートのプログラミング モデルを表し、Excel のオブジェクト モデルへのアクセスを提供します。 詳細については、 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)と[Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)します。 `Sheet1` クラスの残りの部分は、変更することができない非表示のコード ファイルに定義されています。  
  
-   `Sheet1_Startup` および `Sheet1_Shutdown` イベント ハンドラー。 これらのイベント ハンドラーは、Excel がユーザーのカスタマイズを読み込むときとアンロードするときに呼び出されます。 これらのイベント ハンドラーを使用して、読み込まれるときにはカスタマイズを初期化し、アンロードされるときにはカスタマイズが使用したリソースをクリーンアップします。 詳細については、次を参照してください。 [Office プロジェクト内のイベント](../vsto/events-in-office-projects.md)します。  
  
### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>コードを使用してワークシートに 2 行目のテキストを追加するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**Sheet1**、 をクリックし、**コードの表示**します。  
  
     Visual Studio でコード ファイルが開かれます。  
  
2.  `Sheet1_Startup` イベント ハンドラーを次のコードで置き換えます。 Sheet1 が開かれると、このコードは、ワークシートに 2 行目のテキストを追加します。  
  
     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]  
  
## <a name="test-the-project"></a>プロジェクトをテストします。  
  
### <a name="to-test-your-workbook"></a>ブックをテストするには  
  
1.  **F5** キーを押して、プロジェクトをビルドおよび実行します。  
  
     プロジェクトをビルドすると、コードがアセンブリにコンパイルされ、ブックに関連付けられます。 Visual Studio は、ブックおよびアセンブリのコピーをプロジェクトのビルド出力フォルダーに格納し、カスタマイズを実行できるように開発用コンピューターのセキュリティ設定を行います。 詳細については、次を参照してください。[ビルドの Office ソリューション](../vsto/building-office-solutions.md)します。  
  
2.  次のテキストがブックに表示されることを確認します。  
  
     **このテキストは、デザイナーを使用して追加されました。**  
  
     **This text was added by using code.**  
  
3.  ブックを閉じます。  
  
## <a name="clean-up-the-project"></a>プロジェクトをクリーンアップします。  
 プロジェクトの開発が完了したら、ビルド プロセスによって作成されたビルド出力フォルダー内のファイルおよびセキュリティ設定を削除する必要があります。  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>開発用コンピューターから完成したプロジェクトをクリーンアップするには  
  
1.  Visual Studio で、 **[ビルド]** メニューの **[ソリューションのクリーン]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 Excel 用の基本的なドキュメント レベルのカスタマイズを作成したので、カスタマイズ開発の詳細な方法について、以下のトピックを参照してください。  
  
-   ドキュメント レベルのカスタマイズで実行できる一般的なプログラミング タスク:[ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)します。  
  
-   Excel のドキュメント レベルのカスタマイズに固有のプログラミング タスク: [Excel ソリューション](../vsto/excel-solutions.md)します。  
  
-   Excel のオブジェクト モデルの使用: [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)します。  
  
-   Excel の UI のカスタマイズなどによってリボンにカスタム タブの追加や独自の作業ウィンドウの作成: [Office UI のカスタマイズ](../vsto/office-ui-customization.md)します。  
  
-   Visual Studio での Office 開発ツールによって提供される拡張 Excel のオブジェクトを使用して、Excel オブジェクト モデル (たとえば、ドキュメント上でマネージ コントロールをホストしていると Windows フォームを使用して Excel コントロールをデータにバインドを使用してで不可能なタスクを実行するにはデータ バインディング モデル):[拡張オブジェクトを使用して Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)します。  
  
-   ビルドとデバッグの Excel のドキュメント レベルのカスタマイズ:[ビルドの Office ソリューション](../vsto/building-office-solutions.md)します。  
  
-   Excel 用ドキュメント レベル カスタマイズの配置: [Office ソリューションを配置](../vsto/deploying-an-office-solution.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Excel ソリューション](../vsto/excel-solutions.md)   
 [プログラムのドキュメント レベルのカスタマイズ](../vsto/programming-document-level-customizations.md)   
 [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)   
 [拡張オブジェクトを使用して Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office ソリューションを構築します。](../vsto/building-office-solutions.md)   
 [Office ソリューションをデプロイします。](../vsto/deploying-an-office-solution.md)   
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)  
  
  