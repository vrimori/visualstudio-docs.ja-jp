---
title: "チュートリアル: 初めての Project 用 VSTO アドインの作成"
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
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発]、作成 (初めてのプロジェクトを)"
  - "Visual Studio での Office 開発、作成 (初めてのプロジェクトを)"
  - "プロジェクト [Visual Studio での Office 開発]、作成 (初めてのプロジェクトを)"
  - "アドイン [Visual Studio での Office 開発]、作成 (初めてのプロジェクトを)"
ms.assetid: da2b727e-6db8-4853-bf00-7afe0ef13213
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# チュートリアル: 初めての Project 用 VSTO アドインの作成
  このチュートリアルでは Microsoft Office Project 用の VSTO アドインを作成する方法を示します。 この種のソリューションに作成した機能は、どのプロジェクトが開いているかにかかわらず、アプリケーション自体に対して使用できます。 詳細については、「[Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)」を参照してください。  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   Project VSTO アドイン プロジェクトを作成する。  
  
-   Project のオブジェクト モデルを使用して、新しいプロジェクトにタスクを追加するコードを記述する。  
  
-   プロジェクトをビルドし、実行してテストする。  
  
-   完成したプロジェクトをクリーンアップして、開発用コンピューターでこの VSTO アドインが自動的に実行されないようにする。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] または [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)]。  
  
## プロジェクトの作成  
  
#### Visual Studio で新しいプロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
3.  テンプレート ペインで、**\[Visual C\#\]** または **\[Visual Basic\]** を展開してから、**\[Office\/SharePoint\]** を展開します。  
  
4.  展開した **\[Office\/SharePoint\]** ノードの下で、**\[Office Add\-ins\]** ノードを選択します。  
  
5.  プロジェクト テンプレートの一覧で、**\[Project 2010 アドイン\]** または **\[Project 2013 アドイン\]** を選びます。  
  
6.  **\[名前\]** ボックスに「**FirstProjectAddIn**」と入力します。  
  
7.  **\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] により **FirstProjectAddIn** プロジェクトが作成され、**ThisAddIn** コード ファイルがエディターで開かれます。  
  
## プロジェクトに新しいタスクを追加するコードの記述  
 次に、ThisAddIn コード ファイルにコードを追加します。 新しいコードでは、Project のオブジェクト モデルを使用して、プロジェクトに新しいタスクを追加します。 ThisAddIn コード ファイルには、次の生成コードが既定で含まれています。  
  
-   `ThisAddIn` クラスの部分定義。 このクラスは、コードのエントリ ポイントを提供し、Project のオブジェクト モデルへのアクセスを提供します。 詳細については、「[VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)」を参照してください。`ThisAddIn` クラスの残りの部分は、変更することができない非表示のコード ファイルに定義されています。  
  
-   `ThisAddIn_Startup` および `ThisAddIn_Shutdown` イベント ハンドラー。 これらのイベント ハンドラーは、Project が VSTO アドインを読み込むときとアンロードするときに呼び出されます。 これらのイベント ハンドラーを使用して、VSTO アドインを読み込むときに初期化し、VSTO アドインがアンロードされるときには使用したリソースをクリーンアップします。 詳細については、「[Office プロジェクトのイベント](../vsto/events-in-office-projects.md)」を参照してください。  
  
#### 新しいプロジェクトにタスクを追加するには  
  
1.  ThisAddIn コード ファイルで、次のコードを `ThisAddIn` クラスに追加します。 このコードでは、NewProject クラスの Microsoft.Office.Interop.MSProject.Application イベントのイベント ハンドラーを定義します。  
  
     ユーザーが新しいプロジェクトを作成すると、このイベント ハンドラーによってタスクがプロジェクトに追加されます。  
  
     [!code-csharp[Trin_ProjectAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ProjectAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/VB/ThisAddIn.vb#1)]  
  
 プロジェクトを変更するため、このコード例では次のオブジェクトを使用しています。  
  
-   `ThisAddIn` クラスの `Application` フィールド。`Application` フィールドは、Project の現在のインスタンスを表す Microsoft.Office.Interop.MSProject.Application オブジェクトを返します。  
  
-   NewProject イベントのイベント ハンドラーの `pj` パラメーター。`pj` パラメーターは、プロジェクトを表す Microsoft.Office.Interop.MSProject.Project オブジェクトです。 詳細については、「[Project ソリューション](../vsto/project-solutions.md)」を参照してください。  
  
1.  C\# を使用する場合は、次のコードを `ThisAddIn_Startup` イベント ハンドラーに追加します。 このコードは、`Application_Newproject` イベント ハンドラーを NewProject イベントに接続します。  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/CS/ThisAddIn.cs#2)]  
  
-  
  
## プロジェクトのテスト  
 プロジェクトをビルドして実行し、新しいプロジェクトに新しいタスクが表示されることを確認します。  
  
#### プロジェクトをテストするには  
  
1.  **F5** キーを押して、プロジェクトをビルドおよび実行します。 Microsoft Project が起動し、新しい空のプロジェクトが自動的に開きます。  
  
     プロジェクトをビルドすると、プロジェクトのビルド出力フォルダーに含まれるアセンブリにコードがコンパイルされます。 さらに Visual Studio は、Project が VSTO アドインを検出して読み込めるようにする一連のレジストリ エントリを作成し、VSTO アドインを実行できるように開発用コンピューター上のセキュリティを設定します。 詳細については、「[Office ソリューション ビルド処理の概要](http://msdn.microsoft.com/ja-jp/a9d12e4f-c9ea-4a62-a841-c42b91f831ee)」を参照してください。  
  
2.  新しいタスクが空のプロジェクトに追加されることを確認します。  
  
3.  次のテキストがタスクの **\[タスク名\]** フィールドに表示されることを確認します。  
  
     **This text was added by using code.**  
  
4.  Microsoft Project を閉じます。  
  
## プロジェクトのクリーンアップ  
 プロジェクトの開発が完了したら、VSTO アドイン アセンブリ、レジストリ エントリ、およびセキュリティ設定を開発用コンピューターから削除します。 この操作を行わないと、開発用コンピューター上で Microsoft Project を起動するたびに VSTO アドインが実行されます。  
  
#### プロジェクトをクリーンアップするには  
  
1.  Visual Studio で、**\[ビルド\]** メニューの **\[ソリューションのクリーン\]** をクリックします。  
  
## 次の手順  
 これで Project 用の基本的な VSTO アドインの作成が完了しました。VSTO アドインの開発方法について詳しくは、次に示すトピックをご覧ください。  
  
-   Project 用の VSTO アドインで実行できる一般的なプログラミング タスク: [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)  
  
-   Project のオブジェクト モデルの使用法: [Project ソリューション](../vsto/project-solutions.md)  
  
-   Project 用の VSTO アドインのビルドとデバッグ: [Office ソリューションのビルド](../vsto/building-office-solutions.md)  
  
-   Project 用の VSTO アドインの配置: [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)  
  
## 参照  
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)   
 [Project ソリューション](../vsto/project-solutions.md)   
 [Office ソリューションのビルド](../vsto/building-office-solutions.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)  
  
  