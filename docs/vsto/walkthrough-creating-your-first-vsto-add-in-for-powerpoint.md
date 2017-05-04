---
title: "チュートリアル : 初めての PowerPoint 用 VSTO アドインの作成 | Microsoft Docs"
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
  - "アドイン [Visual Studio での Office 開発], 作成 (初めてのプロジェクトを)"
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発], 作成 (初めてのプロジェクトを)"
  - "Visual Studio での Office 開発, 作成 (初めてのプロジェクトを)"
  - "PowerPoint [Visual Studio での Office 開発], 作成 (初めてのプロジェクトを)"
ms.assetid: 52d1543a-c9cb-4ee1-aa5b-90759fce9d3a
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# チュートリアル : 初めての PowerPoint 用 VSTO アドインの作成
  このチュートリアルでは Microsoft Office PowerPoint の VSTO アドインを作成する方法を示します。  この種のソリューションに作成した機能は、どのプレゼンテーションが開いているかにかかわらず、アプリケーション自体に対して使用できます。  詳細については、「[Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)」を参照してください。  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   PowerPoint の PowerPoint VSTO アドイン プロジェクトを作成する。  
  
-   PowerPoint のオブジェクト モデルを使用して、新しい各スライドにテキスト ボックスを追加するコードを記述する。  
  
-   テストを行うためにプロジェクトをビルドし、実行する。  
  
-   プロジェクトをクリーンアップして、開発用コンピューターで VSTO アドインが自動的に実行されないようにする。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## プロジェクトの作成  
  
#### 新しいプロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
3.  テンプレート ペインで、**\[Visual C\#\]** または **\[Visual Basic\]** を展開してから、**\[Office\/SharePoint\]** を展開します。  
  
4.  展開した **\[Office\/SharePoint\]** ノードの下で、**\[Office Add\-ins\]** ノードを選択します。  
  
5.  プロジェクト テンプレートの一覧で、PowerPoint VSTO アドイン プロジェクトを選択します。  
  
6.  **\[名前\]** ボックスに、「**FirstPowerPointAddIn**」と入力します。  
  
7.  **\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] により **FirstPowerPointAddIn** プロジェクトが作成され、**ThisAddIn** コード ファイルがエディターで開かれます。  
  
## 新しい各スライドにテキストを追加するコードを記述する  
 次に、ThisAddIn コード ファイルにコードを追加します。  新しいコードは PowerPoint のオブジェクト モデルを使用して、新しい各スライドにテキスト ボックスを追加します。  ThisAddIn コード ファイルには、次の生成コードが既定で含まれています。  
  
-   `ThisAddIn` クラスの部分定義。  このクラスは、コードのエントリ ポイントを提供し、PowerPoint のオブジェクト モデルへのアクセスを提供します。  詳細については、「[VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)」を参照してください。  `ThisAddIn` クラスの残りの部分は、変更することができない非表示のコード ファイルに定義されています。  
  
-   `ThisAddIn_Startup` および `ThisAddIn_Shutdown` イベント ハンドラー。  これらのイベント ハンドラーは、PowerPoint が VSTO アドインを読み込むときとアンロードするときに呼び出されます。  これらのイベント ハンドラーを使用して、読み込まれるときには VSTO アドインを初期化し、アンロードされるときには VSTO アドインが使用したリソースをクリーンアップします。  詳細については、「[Office プロジェクトのイベント](../vsto/events-in-office-projects.md)」を参照してください。  
  
#### 新しい各スライドにテキスト ボックスを追加するには  
  
1.  ThisAddIn コード ファイルで、次のコードを `ThisAddIn` クラスに追加します。  このコードは、<xref:Microsoft.Office.Interop.PowerPoint.Application> オブジェクトの <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> イベントを処理するイベント ハンドラーを定義します。  
  
     ユーザーが、アクティブなプレゼンテーションに新しいスライドを追加するとき、このイベント ハンドラーは、新しいスライドの先頭にテキスト ボックスを追加し、テキスト ボックスにテキストを追加します。  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_PowerPointAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  C\# を使用する場合は、次のコードを `ThisAddIn_Startup` イベント ハンドラーに追加します。  このコードは `Application_PresentationNewSlide` イベント ハンドラーを <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> イベントに接続するために必要です。  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 新しい各スライドを変更するために、前のコード例では次のオブジェクトを使用しています。  
  
-   `ThisAddIn` クラスの `Application` フィールド。  `Application` フィールドは PowerPoint の現在のインスタンスを表す <xref:Microsoft.Office.Interop.PowerPoint.Application> オブジェクトを返します。  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> イベントのイベント ハンドラーの `Sld` パラメーター。  `Sld` パラメーターは、新しいスライドを表す <xref:Microsoft.Office.Interop.PowerPoint.Slide> オブジェクトです。  詳細については、「[PowerPoint ソリューション](../vsto/powerpoint-solutions.md)」を参照してください。  
  
## プロジェクトのテスト  
 プロジェクトをビルドして実行するときに、プレゼンテーションに追加した新しいスライドに、テキスト ボックスが表示されることを確認します。  
  
#### プロジェクトをテストするには  
  
1.  **F5** キーを押して、プロジェクトをビルドおよび実行します。  
  
     プロジェクトをビルドすると、プロジェクトのビルド出力フォルダーに置かれるアセンブリにコードがコンパイルされます。  さらに Visual Studio は、PowerPoint が VSTO アドインを検出して読み込めるようにする一連のレジストリ エントリを作成し、VSTO アドインを実行できるように開発用コンピューター上のセキュリティ設定値を構成します。  詳細については、「[Office ソリューションのビルド](../vsto/building-office-solutions.md)」を参照してください。  
  
2.  PowerPoint で、作業中のプレゼンテーションに新しいスライドを追加します。  
  
3.  次のテキストが、スライド上部の新しいテキスト ボックスに追加されていることを確認します。  
  
     **This text was added by using code.**  
  
4.  PowerPoint を閉じます。  
  
## プロジェクトのクリーンアップ  
 プロジェクトの開発が完了したら、VSTO アドイン アセンブリ、レジストリ エントリ、およびセキュリティ設定を開発用コンピューターから削除します。  そうしない場合、開発用コンピューターで PowerPoint を起動するたびに VSTO アドインが実行されます。  
  
#### プロジェクトをクリーンアップするには  
  
1.  Visual Studio で、**\[ビルド\]** メニューの **\[ソリューションのクリーン\]** をクリックします。  
  
## 次の手順  
 これで PowerPoint 用の基本的な VSTO アドインが作成されました。VSTO アドインの開発方法の詳細について、以下のトピックを参照してください。  
  
-   PowerPoint 用 VSTO アドインで実行できる一般的なプログラミング タスク。  詳細については、「[VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)」を参照してください。  
  
-   PowerPoint のオブジェクト モデルの使用  詳細については、「[PowerPoint ソリューション](../vsto/powerpoint-solutions.md)」を参照してください。  
  
-   PowerPoint のユーザー インターフェイス \(UI\) のカスタマイズ \(リボンへのカスタム タブの追加や独自のカスタム作業ウィンドウの作成など\)。  詳細については、「[Office UI のカスタマイズ](../vsto/office-ui-customization.md)」を参照してください。  
  
-   PowerPoint 用 VSTO アドインのビルドおよびデバッグ。  詳細については、「[Office ソリューションのビルド](../vsto/building-office-solutions.md)」を参照してください。  
  
-   PowerPoint 用 VSTO アドインの配置。  詳細については、「[Office ソリューションの配置](../vsto/deploying-an-office-solution.md)」を参照してください。  
  
## 参照  
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)   
 [PowerPoint ソリューション](../vsto/powerpoint-solutions.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Office ソリューションのビルド](../vsto/building-office-solutions.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)  
  
  