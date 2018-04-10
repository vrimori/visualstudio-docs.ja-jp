---
title: はじめに VSTO アドインのプログラミング |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- office-development
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: f395ce7fb85d71ed6e8c3f7dfb10726907832873
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="getting-started-programming-vsto-add-ins"></a>VSTO アドインのプログラミングについて
  VSTO アドインを使用することにより、Microsoft Office アプリケーションを自動化し、アプリケーションの機能を拡張できるほか、アプリケーションのユーザー インターフェイス (UI) をカスタマイズすることもできます。 Visual Studio を使用して作成することができます、VSTO アドインと Office ソリューションの他の種類との比較に関する情報を参照してください。 [Office ソリューション開発の概要 & #40 です。VSTO & #41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="creating-vsto-add-in-projects"></a>VSTO アドイン プロジェクトの作成  
 VSTO アドイン プロジェクトを作成する VSTO アドイン プロジェクトのテンプレートのいずれかを使用して、**新しいプロジェクト** ダイアログ ボックス。 これらのテンプレートには必要なアセンブリ参照とプロジェクト ファイルが含まれています。 Visual Studio には、Office のほとんどのアプリケーション用の VSTO アドイン プロジェクト テンプレートが用意されています。  
  
 VSTO アドイン プロジェクトを作成する方法の詳細については、次を参照してください。[する方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)です。 プロジェクト テンプレートの詳細については、次を参照してください。 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)です。  
  
## <a name="developing-vsto-add-in-projects"></a>VSTO アドイン プロジェクトの開発  
 VSTO アドイン プロジェクトを作成するときに自動的に作成、ThisAddIn.vb (で[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) または thisaddin.cs (C# の場合)。 このファイルが含まれています、`ThisAddIn`クラスで、VSTO アドインの基礎を提供します。 このクラスのメンバーを使用して、VSTO アドインが読み込まれたとき、またはアンロードされたときにコードを実行したり、ホスト アプリケーションのオブジェクト モデルにアクセスしたりすることができます。また、アプリケーションの機能を拡張することも可能です。 詳細については、「 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。  
  
## <a name="automating-applications-by-using-the-object-models"></a>オブジェクト モデルによるアプリケーションの自動化  
 Microsoft Office アプリケーションのオブジェクト モデルは、VSTO アドインでプログラミングに使用できる多くの型を公開します。 それらの型を使用してアプリケーションを自動化できます。 たとえば、Outlook でプログラムによって電子メールを作成および送信することもできれば、Word で文書を開き、コンテンツを追加することも可能です。 コードで、ホスト アプリケーションのオブジェクト モデルにアクセスする方法の詳細については、次を参照してください。 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)です。  
  
 特定の Microsoft Office アプリケーションのオブジェクト モデルの詳細については、以下のトピックを参照してください。  
  
-   [Excel Object Model Overview](../vsto/excel-object-model-overview.md)  
  
-   [Word Object Model Overview](../vsto/word-object-model-overview.md)  
  
-   [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath ソリューション](../vsto/infopath-solutions.md)  
  
-   [PowerPoint ソリューション](../vsto/powerpoint-solutions.md)  
  
-   [Project ソリューション](../vsto/project-solutions.md)  
  
-   [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)  
  
## <a name="customizing-the-user-interface-of-applications"></a>アプリケーションのユーザー インターフェイスのカスタマイズ  
 VSTO アドインを使用してホスト アプリケーションの UI をカスタマイズするためのさまざまな方法があります。  
  
-   Excel や Word の場合、ドキュメントにマネージ コントロールを追加できます。 詳細については、「 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
-   アプリケーションでサポートされている場合は、リボンをカスタマイズできます。 詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)です。  
  
-   アプリケーションでサポートされている場合は、カスタム作業ウィンドウを作成できます。 詳細については、次を参照してください。[カスタム作業ウィンドウの](../vsto/custom-task-panes.md)します。  
  
-   Outlook では、カスタム フォーム領域を作成できます。 詳細については、「 [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md)」を参照してください。  
  
-   すべての Microsoft Office アプリケーションで、VSTO アドインに Windows フォームを表示できます。  
  
 Microsoft Office アプリケーションの UI をカスタマイズする方法の詳細については、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)です。  
  
## <a name="next-steps"></a>次の手順  
 VSTO アドインの作成方法については、次のチュートリアルを参照してください。  
  
-   [チュートリアル: 初めての Excel 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [チュートリアル: 初めての Outlook 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [チュートリアル: 初めての PowerPoint 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [チュートリアル: 初めての Project 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [チュートリアル: 初めての Word 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 これらのチュートリアルでは、Visual Studio の Office 開発ツール、および VSTO アドインのプログラミング モデルを紹介します。  
  
 Office プロジェクトの一般的なタスクを解説しているトピックの一覧は、次を参照してください。 [Office プログラミングで一般的なタスク](../vsto/common-tasks-in-office-programming.md)です。  
  
## <a name="see-also"></a>参照  
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [作業の開始 (&) #40 です。 Visual Studio & #41; での Office 開発](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  