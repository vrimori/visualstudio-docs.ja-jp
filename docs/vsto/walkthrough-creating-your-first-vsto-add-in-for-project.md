---
title: "チュートリアル: は、初めて VSTO アドイン プロジェクトの作成 |Microsoft ドキュメント"
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
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
ms.assetid: da2b727e-6db8-4853-bf00-7afe0ef13213
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 391bd4bbdfe87f1bc00ac14356c61f988b8bf041
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-project"></a>チュートリアル: 初めての Project 用 VSTO アドインの作成
  このチュートリアルでは Microsoft Office Project 用の VSTO アドインを作成する方法を示します。 この種のソリューションに作成した機能は、どのプロジェクトが開いているかにかかわらず、アプリケーション自体に対して使用できます。 詳細については、次を参照してください。 [Office ソリューション開発の概要 &#40;です。VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   Project VSTO アドイン プロジェクトを作成する。  
  
-   Project のオブジェクト モデルを使用して、新しいプロジェクトにタスクを追加するコードを記述する。  
  
-   プロジェクトをビルドし、実行してテストする。  
  
-   完成したプロジェクトをクリーンアップして、開発用コンピューターでこの VSTO アドインが自動的に実行されないようにする。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] または [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)]。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
  
#### <a name="to-create-a-new-project-in-visual-studio"></a>Visual Studio で新しいプロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  **[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。  
  
3.  テンプレート ペインで、 **[Visual C#]** または **[Visual Basic]**を展開してから、 **[Office/SharePoint]**を展開します。  
  
4.  展開した **[Office/SharePoint]** ノードの下で、 **[Office Add-ins]** ノードを選択します。  
  
5.  プロジェクト テンプレートの一覧で、 **[Project 2010 アドイン]** または **[Project 2013 アドイン]**を選びます。  
  
6.  **[名前]** ボックスに「 **FirstProjectAddIn**」と入力します。  
  
7.  **[OK]**をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] により **FirstProjectAddIn** プロジェクトが作成され、 **ThisAddIn** コード ファイルがエディターで開かれます。  
  
## <a name="writing-code-that-adds-a-new-task-to-a-project"></a>プロジェクトに新しいタスクを追加するコードの記述  
 次に、ThisAddIn コード ファイルにコードを追加します。 新しいコードでは、Project のオブジェクト モデルを使用して、プロジェクトに新しいタスクを追加します。 ThisAddIn コード ファイルには、次の生成コードが既定で含まれています。  
  
-   `ThisAddIn` クラスの部分定義。 このクラスは、コードのエントリ ポイントを提供し、Project のオブジェクト モデルへのアクセスを提供します。 詳細については、「 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。`ThisAddIn` クラスの残りの部分は、変更することができない非表示のコード ファイルに定義されています。  
  
-   `ThisAddIn_Startup` および `ThisAddIn_Shutdown` イベント ハンドラー。 これらのイベント ハンドラーは、Project が VSTO アドインを読み込むときとアンロードするときに呼び出されます。 これらのイベント ハンドラーを使用して、VSTO アドインを読み込むときに初期化し、VSTO アドインがアンロードされるときには使用したリソースをクリーンアップします。 詳細については、「 [Events in Office Projects](../vsto/events-in-office-projects.md)」を参照してください。  
  
#### <a name="to-add-a-task-to-a-new-project"></a>新しいプロジェクトにタスクを追加するには  
  
1.  ThisAddIn コード ファイルで、次のコードを `ThisAddIn` クラスに追加します。 このコードでは、Microsoft.Office.Interop.MSProject.Application クラスの新しいプロジェクトのイベントのイベント ハンドラーを定義します。  
  
     ユーザーが新しいプロジェクトを作成すると、このイベント ハンドラーによってタスクがプロジェクトに追加されます。  
  
     [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]  
  
 プロジェクトを変更するため、このコード例では次のオブジェクトを使用しています。  
  
-   `Application` クラスの `ThisAddIn` フィールド。 `Application`フィールドは、プロジェクトの現在のインスタンスを表す Microsoft.Office.Interop.MSProject.Application オブジェクトを返します。  
  
-   `pj`プロジェクトに新しいイベントのイベント ハンドラーのパラメーターです。 `pj`パラメーターは、Microsoft.Office.Interop.MSProject.Project オブジェクト、プロジェクトを表します。 詳細については、「 [Project Solutions](../vsto/project-solutions.md)」を参照してください。  
  
1.  C# を使用する場合は、次のコードを `ThisAddIn_Startup` イベント ハンドラーに追加します。 このコードでは接続、`Application_Newproject`プロジェクトに新しいイベントにイベント ハンドラー。  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]  
  
-  
  
## <a name="testing-the-project"></a>プロジェクトのテスト  
 プロジェクトをビルドして実行し、新しいプロジェクトに新しいタスクが表示されることを確認します。  
  
#### <a name="to-test-the-project"></a>プロジェクトをテストするには  
  
1.  **F5** キーを押して、プロジェクトをビルドおよび実行します。 Microsoft Project が起動し、新しい空のプロジェクトが自動的に開きます。  
  
     プロジェクトをビルドすると、プロジェクトのビルド出力フォルダーに含まれるアセンブリにコードがコンパイルされます。 さらに Visual Studio は、Project が VSTO アドインを検出して読み込めるようにする一連のレジストリ エントリを作成し、VSTO アドインを実行できるように開発用コンピューター上のセキュリティを設定します。 詳細については、「 [Office ソリューション ビルド処理の概要](http://msdn.microsoft.com/en-us/a9d12e4f-c9ea-4a62-a841-c42b91f831ee)」を参照してください。  
  
2.  新しいタスクが空のプロジェクトに追加されることを確認します。  
  
3.  次のテキストがタスクの **[タスク名]** フィールドに表示されることを確認します。  
  
     **This text was added by using code.**  
  
4.  Microsoft Project を閉じます。  
  
## <a name="cleaning-up-the-project"></a>プロジェクトのクリーンアップ  
 プロジェクトの開発が完了したら、VSTO アドイン アセンブリ、レジストリ エントリ、およびセキュリティ設定を開発用コンピューターから削除します。 この操作を行わないと、開発用コンピューター上で Microsoft Project を起動するたびに VSTO アドインが実行されます。  
  
#### <a name="to-clean-up-your-project"></a>プロジェクトをクリーンアップするには  
  
1.  Visual Studio で、 **[ビルド]** メニューの **[ソリューションのクリーン]**をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 これで Project 用の基本的な VSTO アドインの作成が完了しました。VSTO アドインの開発方法について詳しくは、次に示すトピックをご覧ください。  
  
-   Project 用の VSTO アドインで実行できる一般的なプログラミング タスク: [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
-   Project のオブジェクト モデルの使用法: [Project Solutions](../vsto/project-solutions.md)  
  
-   ビルドとは、VSTO アドイン プロジェクトのデバッグ: [Office ソリューションのビルド](../vsto/building-office-solutions.md)です。  
  
-   Project 用の VSTO アドインを配置: [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)です。  
  
## <a name="see-also"></a>参照  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [プロジェクトから成るソリューション](../vsto/project-solutions.md)   
 [Office ソリューションのビルド](../vsto/building-office-solutions.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)  
  
  