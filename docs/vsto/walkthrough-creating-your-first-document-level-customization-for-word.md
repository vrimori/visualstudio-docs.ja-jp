---
title: "チュートリアル : 初めての Word 用ドキュメント レベルのカスタマイズの作成"
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
  - "Visual Studio での Office 開発, 作成 (初めてのプロジェクトを)"
  - "Word [Visual Studio での Office 開発], 作成 (初めてのプロジェクトを)"
ms.assetid: ec9f5173-0923-4aee-985a-e760e80eaae3
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# チュートリアル : 初めての Word 用ドキュメント レベルのカスタマイズの作成
  この入門編のチュートリアルでは、Microsoft Office Word 用のドキュメント レベルのカスタマイズを作成する方法について説明します。  この種のソリューションで作成した機能は、特定の文書が開いている場合にのみ使用可能です。  ドキュメント レベルのカスタマイズでは、文書が開いたときに新しいリボン タブを表示するなどの、アプリケーション全体の変更を行うことはできません。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   新しい Word 文書プロジェクトを作成する。  
  
-   Visual Studio デザイナーでホストされるドキュメントにテキストを追加する。  
  
-   Word のオブジェクト モデルを使用して、カスタマイズされた文書が開かれたときにテキストを追加するコードを記述する。  
  
-   プロジェクトをビルドし、実行してテストする。  
  
-   プロジェクトをクリーンアップして、不要なビルド ファイルやセキュリティ設定を開発用コンピューターから削除する。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## プロジェクトの作成  
  
#### Visual Studio で新しい Word 文書プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
3.  テンプレート ペインで、**\[Visual C\#\]** または **\[Visual Basic\]** を展開してから **\[Office\/SharePoint\]** を展開します。  
  
4.  展開した **\[Office\/SharePoint\]** ノードの下で、**\[Office Add\-ins\]** ノードを選択します。  
  
5.  プロジェクト テンプレートの一覧で、Word VSTO 文書プロジェクトを選択します。  
  
6.  **\[名前\]** ボックスに「**FirstDocumentCustomization**」と入力します。  
  
7.  **\[OK\]** をクリックします。  
  
     **Visual Studio Tools for Office プロジェクト ウィザード**が開きます。  
  
8.  **\[新規ドキュメントの作成\]** を選択し、**\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] により **FirstDocumentCustomization** プロジェクトが作成され、**FirstDocumentCustomization** ドキュメントおよび ThisDocument コード ファイルがプロジェクトに追加されます。  **FirstDocumentCustomization** ドキュメントがデザイナーで自動的に開かれます。  
  
## デザイナーで文書を閉じ、再び開く  
 プロジェクトの開発中にデザイナーで開いたドキュメントを意図的にまたは誤って閉じた場合は、そのドキュメントを再び開くことができます。  
  
#### デザイナーで文書を閉じ、再び開くには  
  
1.  デザイナー ウィンドウの **\[閉じる\]** ボタン \(X\) をクリックしてドキュメントを閉じます。  
  
2.  **ソリューション エクスプローラー**で、**ThisDocument** コード ファイルを右クリックし、**\[デザイナーの表示\]** をクリックします。  
  
     または  
  
     **ソリューション エクスプローラー**で **ThisDocument** コード ファイルをダブルクリックします。  
  
## デザイナーによるドキュメントへのテキストの追加  
 デザイナーで開いたドキュメントを変更することで、カスタマイズのユーザー インターフェイス \(UI\) をデザインできます。  たとえば、テキスト、テーブル、または Word コントロールを追加できます。  デザイナーの使用方法の詳細については、「[Visual Studio 環境における Office プロジェクト](../vsto/office-projects-in-the-visual-studio-environment.md)」を参照してください。  
  
#### デザイナーを使用してドキュメントにテキストを追加するには  
  
1.  デザイナーで開いているドキュメントに次のテキストを入力します。  
  
     **このテキストは、デザイナーを使用して追加されました。**  
  
## プログラムによるドキュメントへのテキストの追加  
 次に、ThisDocument コード ファイルにコードを追加します。  この新しいコードでは、Word のオブジェクト モデルを使用して、ドキュメントに 2 番目のテキスト段落を追加します。  ThisDocument コード ファイルには、既定で次の生成済みコードが含まれています。  
  
-   `ThisDocument` クラスの部分定義。このクラスは、ドキュメントのプログラミング モデルを表し、Word のオブジェクト モデルへのアクセスを提供します。  詳細については、「[Document ホスト項目](../vsto/document-host-item.md)」および「[Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)」を参照してください。  `ThisDocument` クラスの残りの部分は、変更すべきでない非表示のコード ファイルに定義されています。  
  
-   `ThisDocument_Startup` イベント ハンドラーおよび `ThisDocument_Shutdown` イベント ハンドラー。  これらのイベント ハンドラーは、ドキュメントが開いたとき、および閉じたときに呼び出されます。  これらのイベント ハンドラーを使用して、ドキュメントが開いたときにカスタマイズを初期化し、ドキュメントが閉じたときにカスタマイズが使用したリソースをクリーンアップします。  詳細については、「[Office プロジェクトのイベント](../vsto/events-in-office-projects.md)」を参照してください。  
  
#### コードを使用してドキュメントに 2 番目のテキスト段落を追加するには  
  
1.  **ソリューション エクスプローラー**で **ThisDocument** を右クリックし、**\[コードの表示\]** をクリックします。  
  
     Visual Studio でコード ファイルが開かれます。  
  
2.  `ThisDocument_Startup` イベント ハンドラーを次のコードで置き換えます。  ドキュメントが開かれると、この新しいコードにより、2 番目のテキスト段落がドキュメントに追加されます。  
  
     [!code-csharp[Trin_WordDocumentTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordDocumentTutorial/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_WordDocumentTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordDocumentTutorial/VB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  このコードでは、インデックス値 1 を使用して <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A> プロパティ内の最初の段落にアクセスします。  Visual Basic および Visual C\# ではインデックスが 0 から始まる配列が使用されますが、Word オブジェクト モデルのほとんどのコレクションでは配列の下限のインデックスが 1 から始まります。  詳細については、「[Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)」を参照してください。  
  
## プロジェクトのテスト  
  
#### 文書をテストするには  
  
1.  **F5** キーを押して、プロジェクトをビルドおよび実行します。  
  
     プロジェクトをビルドすると、コードがアセンブリにコンパイルされ、ドキュメントに関連付けられます。  Visual Studio は、ドキュメントとアセンブリのコピーをプロジェクトのビルド出力フォルダーに格納し、カスタマイズを実行できるように開発用コンピューターのセキュリティ設定を行います。  詳細については、「[Office ソリューションのビルド](../vsto/building-office-solutions.md)」を参照してください。  
  
2.  次のテキストがドキュメントに表示されることを確認します。  
  
     **このテキストは、デザイナーを使用して追加されました。**  
  
     **このテキストは、コードを使用して追加されました。**  
  
3.  ドキュメントを閉じます。  
  
## プロジェクトのクリーンアップ  
 プロジェクトの開発が完了したら、ビルド プロセスによって作成されたビルド出力フォルダー内のファイルおよびセキュリティ設定を削除する必要があります。  
  
#### 開発用コンピューターから、完成したプロジェクトをクリーンアップするには  
  
1.  Visual Studio で、**\[ビルド\]** メニューの **\[ソリューションのクリーン\]** をクリックします。  
  
## 次の手順  
 Word 用の基本的なドキュメント レベルのカスタマイズを作成した後は、カスタマイズの開発方法の詳細について、以下のトピックを参照してください。  
  
-   ドキュメント レベルのカスタマイズで実行できる一般的なプログラミング タスク: [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)。  
  
-   Word 用のドキュメント レベルのカスタマイズに固有のプログラミング タスク: [Word ソリューション](../vsto/word-solutions.md)。  
  
-   Word のオブジェクト モデルの使用方法: [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)。  
  
-   Word の UI のカスタマイズ \(リボンへのカスタム タブの追加や、独自のカスタム作業ウィンドウの作成など\): [Office UI のカスタマイズ](../vsto/office-ui-customization.md)。  
  
-   Word オブジェクト モデルを使用して実行できないタスク \(たとえば、ドキュメント上でマネージ コントロールをホストする、Windows フォーム データ バインディング モデルを使用して Word コントロールをデータにバインドするなど\) を、Visual Studio の Office ソリューションで提供される拡張 Word オブジェクトを使用して実行する: [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)。  
  
-   Word 用のドキュメント レベルのカスタマイズのビルドとデバッグ: [Office ソリューションのビルド](../vsto/building-office-solutions.md)。  
  
-   Word 用のドキュメント レベルのカスタマイズの配置: [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)。  
  
## 参照  
 [Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Word ソリューション](../vsto/word-solutions.md)   
 [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office ソリューションのビルド](../vsto/building-office-solutions.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)  
  
  