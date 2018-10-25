---
title: 'チュートリアル: Word の最初の VSTO アドイン作成します。'
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
- Word [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cf20b3f742bfc5ff6de6af080f3651f9d9027234
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940971"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-word"></a>チュートリアル: Word の最初の VSTO アドイン作成します。
  この入門チュートリアルでは、Microsoft Office Word 用の VSTO アドインを作成する方法について説明します。 この種のソリューションに作成した機能は、どのドキュメントが開いているかにかかわらず、アプリケーション自体に対して使用できます。  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
- Word VSTO アドイン プロジェクトの作成  
  
- Word のオブジェクト モデルを使用して、保存時にテキストをドキュメントに追加するコードを記述する。  
  
- テストを行うためにプロジェクトをビルドし、実行する。  
  
- 完成したプロジェクトをクリーンアップして、開発用コンピューターでこの VSTO アドインが自動的に実行されないようにする。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>プロジェクトの作成  
  
### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>Visual Studio で新しい Word VSTO アドイン プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
3.  テンプレート ペインで、 **[Visual C#]** または **[Visual Basic]** を展開してから、 **[Office/SharePoint]** を展開します。  
  
4.  展開した **[Office/SharePoint]** ノードの下で、 **[Office Add-ins]** ノードを選択します。  
  
5.  プロジェクト テンプレートの一覧で、Word VSTO アドイン プロジェクトを選択します。  
  
6.  **名前**ボックスに「 **FirstWordAddIn**します。  
  
7.  **[OK]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 作成、 **FirstWordAddIn**プロジェクトし、エディターで、ThisAddIn コード ファイルを開きます。  
  
## <a name="write-code-to-add-text-to-the-saved-document"></a>保存されたドキュメントにテキストを追加するコードを記述します。  
 次に、ThisAddIn コード ファイルにコードを追加します。 この新しいコードでは、Word のオブジェクト モデルを使用して、保存する各ドキュメントに定型のテキストを追加します。 ThisAddIn コード ファイルには、次の生成コードが既定で含まれています。  
  
-   `ThisAddIn` クラスの部分定義。 このクラスは、コードのエントリ ポイントを提供し、Word のオブジェクト モデルへのアクセスを提供します。 詳細については、次を参照してください。[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)します。`ThisAddIn` クラスの残りの部分は、変更することができない非表示のコード ファイルに定義されています。  
  
-   `ThisAddIn_Startup` および `ThisAddIn_Shutdown` イベント ハンドラー。 これらのイベント ハンドラーは、Word が VSTO アドインを読み込むときとアンロードするときに呼び出されます。 これらのイベント ハンドラーを使用して、VSTO アドインを読み込むときに初期化し、VSTO アドインがアンロードされるときには使用したリソースをクリーンアップします。 詳細については、次を参照してください。 [Office プロジェクト内のイベント](../vsto/events-in-office-projects.md)します。  
  
### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>保存するドキュメントにテキストの段落を追加するには  
  
1. ThisAddIn コード ファイルで、次のコードを `ThisAddIn` クラスに追加します。 この新しいコードでは、ドキュメントが保存されるときに発生する <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> イベントのイベント ハンドラーを定義します。  
  
    ユーザーがドキュメントを保存すると、イベント ハンドラーによって新しいテキストがドキュメントの先頭に追加されます。  
  
    [!code-vb[Trin_WordAddInTutorial#1](../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb#1)]
    [!code-csharp[Trin_WordAddInTutorial#1](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#1)]  
  
   > [!NOTE]  
   >  このコードでは、インデックス値 1 を使用して <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A> コレクション内の最初の段落にアクセスします。 Visual Basic および Visual C# ではインデックスが 0 から始まる配列が使用されますが、Word オブジェクト モデルのほとんどのコレクションでは配列の下限のインデックスが 1 から始まります。 詳細については、次を参照してください。 [Office ソリューションでコードを記述](../vsto/writing-code-in-office-solutions.md)します。  
  
2. C# を使用する場合は、次の必要なコードを `ThisAddIn_Startup` イベント ハンドラーに追加します。 このコードは、 `Application_DocumentBeforeSave` イベント ハンドラーを <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> イベントに接続するために使用します。  
  
    [!code-csharp[Trin_WordAddInTutorial#2](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#2)]  
  
   保存時にドキュメントを変更するために、前のコード例では次のオブジェクトを使用しています。  
  
-   `ThisAddIn` クラスの `Application` フィールド。 `Application` フィールドは Word の現在のインスタンスを表す <xref:Microsoft.Office.Interop.Word.Application> オブジェクトを返します。  
  
-   `Doc` イベントのイベント ハンドラーの <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> パラメーター。 `Doc` パラメーターは、保存されるドキュメントを表す <xref:Microsoft.Office.Interop.Word.Document> オブジェクトです。 詳細については、次を参照してください。 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)します。  
  
## <a name="test-the-project"></a>プロジェクトをテストします。  
  
### <a name="to-test-the-project"></a>プロジェクトをテストするには  
  
1.  **F5** キーを押して、プロジェクトをビルドおよび実行します。  
  
     プロジェクトをビルドすると、プロジェクトのビルド出力フォルダーに含まれるアセンブリにコードがコンパイルされます。 さらに Visual Studio は、Word が VSTO アドインを検出して読み込めるようにする一連のレジストリ エントリを作成し、VSTO アドインを実行できるように開発用コンピューター上のセキュリティを設定します。 詳細については、次を参照してください。[ビルドの Office ソリューション](../vsto/building-office-solutions.md)します。  
  
2.  Word で作業中のドキュメントを保存します。  
  
3.  次のテキストがドキュメントに追加されていることを確認します。  
  
     **This text was added by using code.**  
  
4.  Word を閉じます。  
  
## <a name="clean-up-the-project"></a>プロジェクトをクリーンアップします。  
 プロジェクトの開発が完了したら、VSTO アドイン アセンブリ、レジストリ エントリ、およびセキュリティ設定を開発用コンピューターから削除します。 そうしないと、開発用コンピューター上で Word を起動するたびに VSTO アドインが実行され続けます。  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>開発用コンピューターから完成したプロジェクトをクリーンアップするには  
  
1.  Visual Studio で、 **[ビルド]** メニューの **[ソリューションのクリーン]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 これで Word 用の基本的な VSTO アドインが作成されました。VSTO アドインの開発方法の詳細について、以下のトピックを参照してください。  
  
-   VSTO アドインで実行できる一般的なプログラミング タスク:[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)します。  
  
-   Word VSTO アドインに固有のプログラミング タスク: [Word ソリューション](../vsto/word-solutions.md)します。  
  
-   Word のオブジェクト モデルを使用して: [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)します。  
  
-   Word の UI のカスタマイズなどでリボンにカスタム タブの追加や独自のカスタム作業ウィンドウの作成: [Office UI のカスタマイズ](../vsto/office-ui-customization.md)します。  
  
-   ビルドと Word 用 VSTO アドインをデバッグ:[ビルドの Office ソリューション](../vsto/building-office-solutions.md)します。  
  
-   Word 用 VSTO アドインの展開: [Office ソリューションを配置](../vsto/deploying-an-office-solution.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Word ソリューション](../vsto/word-solutions.md)   
 [VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office ソリューションを構築します。](../vsto/building-office-solutions.md)   
 [Office ソリューションをデプロイします。](../vsto/deploying-an-office-solution.md)   
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)  
  
  