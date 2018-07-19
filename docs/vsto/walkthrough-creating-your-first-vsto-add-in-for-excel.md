---
title: 'Excel 用の最初の VSTO アドインのチュートリアル: 作成します。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6421df0109d68d2647cafff5713aecb297c3536d
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38797800"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>Excel 用の最初の VSTO アドインのチュートリアル: 作成します。
  この入門チュートリアルでは、Microsoft Office Excel 用のアプリケーション レベルのアドインを作成する方法について説明します。 この種のソリューションに作成した機能は、どのブックが開いているかにかかわらず、アプリケーション自体に対して使用できます。  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   Excel 用の Excel VSTO アドイン プロジェクトを作成する。  
  
-   Excel のオブジェクト モデルを使用して、保存時にテキストをブックに追加するコードを記述する。  
  
-   プロジェクトをビルドし、実行してテストする。  
  
-   完成したプロジェクトをクリーンアップして、開発用コンピューターでこの VSTO アドインが自動的に実行されないようにする。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>前提条件  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## <a name="create-the-project"></a>プロジェクトの作成  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Visual Studio で新しい Excel VSTO アドイン プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
3.  テンプレート ペインで、 **[Visual C#]** または **[Visual Basic]** を展開してから、 **[Office/SharePoint]** を展開します。  
  
4.  展開した **[Office/SharePoint]** ノードの下で、 **[Office Add-ins]** ノードを選択します。  
  
5.  プロジェクト テンプレートの一覧で、 **[Excel 2010 アドイン]** または **[Excel 2013 アドイン]** を選択します。  
  
6.  **[名前]** ボックスに、「 **FirstExcelAddIn**」と入力します。  
  
7.  **[OK]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] により **FirstExcelAddIn** プロジェクトが作成され、ThisAddIn コード ファイルがエディターで開かれます。  
  
## <a name="write-code-to-add-text-to-the-saved-workbook"></a>保存されたブックにテキストを追加するコードを記述します。  
 次に、ThisAddIn コード ファイルにコードを追加します。 この新しいコードでは、Excel のオブジェクト モデルを使用して、アクティブなワークシートの最初の行に定型句を挿入します。 アクティブなワークシートとは、ユーザーがブックを保存したときに開いているワークシートのことです。 ThisAddIn コード ファイルには、次の生成コードが既定で含まれています。  
  
-   `ThisAddIn` クラスの部分定義。 このクラスは、コードのエントリ ポイントを提供し、Excel のオブジェクト モデルへのアクセスを提供します。 詳細については、次を参照してください。[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)します。`ThisAddIn` クラスの残りの部分は、変更することができない非表示のコード ファイルに定義されています。  
  
-   `ThisAddIn_Startup` および `ThisAddIn_Shutdown` イベント ハンドラー。 これらのイベント ハンドラーは、Excel が VSTO アドインを読み込むときとアンロードするときに呼び出されます。 これらのイベント ハンドラーを使用して、読み込まれるときには VSTO アドインを初期化し、アンロードされるときにはアドインが使用したリソースをクリーンアップします。 詳細については、次を参照してください。 [Office プロジェクト内のイベント](../vsto/events-in-office-projects.md)します。  
  
### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>保存するブックにテキストの行を追加するには  
  
1.  ThisAddIn コード ファイルで、次のコードを `ThisAddIn` クラスに追加します。 この新しいコードでは、ブックが保存されるときに発生する <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> イベントのイベント ハンドラーを定義します。  
  
     ユーザーがブックを保存すると、イベント ハンドラーによって新しいテキストがアクティブなワークシートの先頭に追加されます。  
  
     [!code-vb[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#1)]  
  
2.  C# を使用する場合は、次の必要なコードを `ThisAddIn_Startup` イベント ハンドラーに追加します。 このコードは、 `Application_WorkbookBeforeSave` イベント ハンドラーを <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> イベントに接続するために使用します。  
  
     [!code-csharp[Trin_ExcelAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#2)]  
  
 保存時にブックを変更するために、前のコード例では次のオブジェクトを使用しています。  
  
-   `Application` クラスの `ThisAddIn` フィールド。 `Application` フィールドは Excel の現在のインスタンスを表す <xref:Microsoft.Office.Interop.Excel.Application> オブジェクトを返します。  
  
-   `Wb` イベントのイベント ハンドラーの <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> パラメーター。 `Wb` パラメーターは、保存されるブックを表す <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトです。 詳細については、次を参照してください。 [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)します。  
  
## <a name="test-the-project"></a>プロジェクトをテストします。  
  
### <a name="to-test-the-project"></a>プロジェクトをテストするには  
  
1.  **F5** キーを押して、プロジェクトをビルドおよび実行します。  
  
     プロジェクトをビルドすると、プロジェクトのビルド出力フォルダーに含まれるアセンブリにコードがコンパイルされます。 さらに Visual Studio は、Excel が VSTO アドインを検出して読み込めるようにする一連のレジストリ エントリを作成し、VSTO アドインを実行できるように開発用コンピューター上のセキュリティを設定します。 詳細については、次を参照してください。[ビルドの Office ソリューション](../vsto/building-office-solutions.md)します。  
  
2.  Excel で、ブックを保存します。  
  
3.  次のテキストがブックに追加されていることを確認します。  
  
     **This text was added by using code.**  
  
4.  Excel を終了します。  
  
## <a name="clean-up-the-project"></a>プロジェクトをクリーンアップします。  
 プロジェクトの開発が完了したら、VSTO アドイン アセンブリ、レジストリ エントリ、およびセキュリティ設定を開発用コンピューターから削除します。 そうしないと、開発用コンピューター上で Excel を起動するたびに VSTO アドインが実行され続けます。  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>開発用コンピューターから完成したプロジェクトをクリーンアップするには  
  
1.  Visual Studio で、 **[ビルド]** メニューの **[ソリューションのクリーン]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 これで Excel 用の基本的な VSTO アドインが作成されました。VSTO アドインの開発方法の詳細について、以下のトピックを参照してください。  
  
-   VSTO アドインで実行できる一般的なプログラミング タスク:[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)します。  
  
-   Excel VSTO アドインに固有のプログラミング タスク: [Excel ソリューション](../vsto/excel-solutions.md)します。  
  
-   Excel のオブジェクト モデルの使用: [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)します。  
  
-   Excel のユーザー インターフェイス (UI) のカスタマイズなどによってリボンにカスタム タブの追加や独自のカスタム作業ウィンドウの作成: [Office UI のカスタマイズ](../vsto/office-ui-customization.md)します。  
  
-   ビルドと Excel 用 VSTO アドインをデバッグ:[ビルドの Office ソリューション](../vsto/building-office-solutions.md)します。  
  
-   Excel 用 VSTO アドインの配置: [Office ソリューションを配置](../vsto/deploying-an-office-solution.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Excel ソリューション](../vsto/excel-solutions.md)   
 [VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)   
 [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office ソリューションを構築します。](../vsto/building-office-solutions.md)   
 [Office ソリューションをデプロイします。](../vsto/deploying-an-office-solution.md)   
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)  
  
  