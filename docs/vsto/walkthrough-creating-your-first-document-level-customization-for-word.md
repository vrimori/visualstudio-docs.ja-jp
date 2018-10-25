---
title: 'チュートリアル: 初めての Word 用ドキュメント レベルのカスタマイズを作成します。'
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
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1c5c25163a49e51b0759e57318d6119edec97983
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928816"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-word"></a>チュートリアル: 初めての Word 用ドキュメント レベルのカスタマイズを作成します。
  この入門編のチュートリアルでは、Microsoft Office Word 用のドキュメント レベルのカスタマイズを作成する方法について説明します。 この種のソリューションで作成した機能は、特定の文書が開いている場合にのみ使用可能です。 ドキュメント レベルのカスタマイズでは、文書が開いたときに新しいリボン タブを表示するなどの、アプリケーション全体の変更を行うことはできません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
- 新しい Word 文書プロジェクトを作成する。  
  
- Visual Studio デザイナーでホストされるドキュメントにテキストを追加する。  
  
- Word のオブジェクト モデルを使用して、カスタマイズされた文書が開かれたときにテキストを追加するコードを記述する。  
  
- プロジェクトをビルドし、実行してテストする。  
  
- プロジェクトをクリーンアップして、不要なビルド ファイルやセキュリティ設定を開発用コンピューターから削除する。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>プロジェクトの作成  
  
### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Visual Studio で新しい Word 文書プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
3.  テンプレート ペインで、 **[Visual C#]** または **[Visual Basic]** を展開してから、 **[Office/SharePoint]** を展開します。  
  
4.  展開した **[Office/SharePoint]** ノードの下で、 **[Office Add-ins]** ノードを選択します。  
  
5.  プロジェクト テンプレートの一覧で、Word VSTO 文書プロジェクトを選択します。  
  
6.  **名前**ボックスに「 **FirstDocumentCustomization**します。  
  
7.  **[OK]** をクリックします。  
  
     **Visual Studio Tools for Office プロジェクト ウィザード** が開きます。  
  
8.  選択**新しい文書を作成**、 をクリック**OK**します。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 作成、 **FirstDocumentCustomization**プロジェクト、および追加、 **FirstDocumentCustomization**ドキュメントおよび ThisDocument コード ファイルをプロジェクト。 **FirstDocumentCustomization**ドキュメントがデザイナーで自動的に開かれます。  
  
## <a name="close-and-reopen-the-document-in-the-designer"></a>デザイナーでドキュメントを閉じてから開き  
 プロジェクトの開発中にデザイナーで開いたドキュメントを意図的にまたは誤って閉じた場合は、そのドキュメントを再び開くことができます。  
  
### <a name="to-close-and-reopen-the-document-in-the-designer"></a>デザイナーで文書を閉じ、再び開くには  
  
1.  クリックして、ドキュメントを閉じる、**閉じる**デザイナー ウィンドウのボタン (X)。  
  
2.  **ソリューション エクスプ ローラー**を右クリックし、 **ThisDocument**コード ファイル、およびクリックして**ビュー デザイナー**します。  
  
     \- または -  
  
     **ソリューション エクスプ ローラー**、ダブルクリックして、 **ThisDocument**コード ファイル。  
  
## <a name="add-text-to-the-document-in-the-designer"></a>デザイナーで文書にテキストを追加します。  
 デザイナーで開いたドキュメントを変更することで、カスタマイズのユーザー インターフェイス (UI) をデザインできます。 たとえば、テキスト、テーブル、または Word コントロールを追加できます。 デザイナーを使用する方法の詳細については、次を参照してください。 [Visual Studio 環境における Office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)します。  
  
### <a name="to-add-text-to-your-document-by-using-the-designer"></a>デザイナーを使用してドキュメントにテキストを追加するには  
  
1.  デザイナーで開いているドキュメントに次のテキストを入力します。  
  
     **このテキストは、デザイナーを使用して追加されました。**  
  
## <a name="add-text-to-the-document-programmatically"></a>プログラムによって文書にテキストを追加します。  
 次に、ThisDocument コード ファイルにコードを追加します。 この新しいコードでは、Word のオブジェクト モデルを使用して、ドキュメントに 2 番目のテキスト段落を追加します。 ThisDocument コード ファイルには、既定で次の生成済みコードが含まれています。  
  
-   `ThisDocument` クラスの部分定義。このクラスは、ドキュメントのプログラミング モデルを表し、Word のオブジェクト モデルへのアクセスを提供します。 詳細については、次を参照してください。 [Document ホスト項目](../vsto/document-host-item.md)と[Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)します。 `ThisDocument` クラスの残りの部分は、変更することができない非表示のコード ファイルに定義されています。  
  
-   `ThisDocument_Startup` イベント ハンドラーおよび `ThisDocument_Shutdown` イベント ハンドラー。 これらのイベント ハンドラーは、ドキュメントが開いたとき、および閉じたときに呼び出されます。 これらのイベント ハンドラーを使用して、ドキュメントが開いたときにカスタマイズを初期化し、ドキュメントが閉じたときにカスタマイズが使用したリソースをクリーンアップします。 詳細については、次を参照してください。 [Office プロジェクト内のイベント](../vsto/events-in-office-projects.md)します。  
  
### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>コードを使用してドキュメントに 2 番目のテキスト段落を追加するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**ThisDocument**、 をクリックし、**コードの表示**します。  
  
     Visual Studio でコード ファイルが開かれます。  
  
2.  `ThisDocument_Startup` イベント ハンドラーを次のコードで置き換えます。 ドキュメントが開かれると、この新しいコードにより、2 番目のテキスト段落がドキュメントに追加されます。  
  
     [!code-vb[Trin_WordDocumentTutorial#1](../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb#1)]
     [!code-csharp[Trin_WordDocumentTutorial#1](../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs#1)]  
  
    > [!NOTE]  
    >  このコードでは、インデックス値 1 を使用して <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A> プロパティ内の最初の段落にアクセスします。 Visual Basic および Visual C# ではインデックスが 0 から始まる配列が使用されますが、Word オブジェクト モデルのほとんどのコレクションでは配列の下限のインデックスが 1 から始まります。 詳細については、次を参照してください。 [Office ソリューションでコードを記述](../vsto/writing-code-in-office-solutions.md)します。  
  
## <a name="test-the-project"></a>プロジェクトをテストします。  
  
### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  **F5** キーを押して、プロジェクトをビルドおよび実行します。  
  
     プロジェクトをビルドすると、コードがアセンブリにコンパイルされ、ドキュメントに関連付けられます。 Visual Studio は、ドキュメントとアセンブリのコピーをプロジェクトのビルド出力フォルダーに格納し、カスタマイズを実行できるように開発用コンピューターのセキュリティ設定を行います。 詳細については、次を参照してください。[ビルドの Office ソリューション](../vsto/building-office-solutions.md)します。  
  
2.  次のテキストがドキュメントに表示されることを確認します。  
  
     **このテキストは、デザイナーを使用して追加されました。**  
  
     **This text was added by using code.**  
  
3.  ドキュメントを閉じます。  
  
## <a name="clean-up-the-project"></a>プロジェクトをクリーンアップします。  
 プロジェクトの開発が完了したら、ビルド プロセスによって作成されたビルド出力フォルダー内のファイルおよびセキュリティ設定を削除する必要があります。  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>開発用コンピューターから完成したプロジェクトをクリーンアップするには  
  
1.  Visual Studio で、 **[ビルド]** メニューの **[ソリューションのクリーン]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 Word 用の基本的なドキュメント レベルのカスタマイズを作成した後は、カスタマイズの開発方法の詳細について、以下のトピックを参照してください。  
  
-   ドキュメント レベルのカスタマイズで実行できる一般的なプログラミング タスク:[ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)します。  
  
-   Word 用ドキュメント レベルのカスタマイズに固有のプログラミング タスク: [Word ソリューション](../vsto/word-solutions.md)します。  
  
-   Word のオブジェクト モデルを使用して: [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)します。  
  
-   Word の UI のカスタマイズなどによってリボンにカスタム タブの追加や独自の作業ウィンドウの作成: [Office UI のカスタマイズ](../vsto/office-ui-customization.md)します。  
  
-   Visual Studio での Office ソリューションで提供される拡張 Word のオブジェクトを使用して、Word オブジェクト モデル (たとえば、ドキュメント上でマネージ コントロールをホストしていると Windows フォーム データを使用して Word コントロールをデータにバインドを使用してで不可能なタスクを実行するにはバインド モデル):[拡張オブジェクトを使用して Word の自動化](../vsto/automating-word-by-using-extended-objects.md)します。  
  
-   ビルドとデバッグの Word 用ドキュメント レベルのカスタマイズ:[ビルドの Office ソリューション](../vsto/building-office-solutions.md)します。  
  
-   Word 用ドキュメント レベル カスタマイズの配置: [Office ソリューションを配置](../vsto/deploying-an-office-solution.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Word ソリューション](../vsto/word-solutions.md)   
 [プログラムのドキュメント レベルのカスタマイズ](../vsto/programming-document-level-customizations.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [拡張オブジェクトを使用して Word を自動化します。](../vsto/automating-word-by-using-extended-objects.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office ソリューションを構築します。](../vsto/building-office-solutions.md)   
 [Office ソリューションをデプロイします。](../vsto/deploying-an-office-solution.md)   
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)  
  
  