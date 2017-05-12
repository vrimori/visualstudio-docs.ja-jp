---
title: "VSTO アドインのプログラミングについて"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.Outlook"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "アドイン [Visual Studio での Office 開発], はじめに"
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発], はじめに"
ms.assetid: 9ac1e6ea-9511-4633-80f9-dc7641f22b63
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# VSTO アドインのプログラミングについて
  VSTO アドインを使用することにより、Microsoft Office アプリケーションを自動化し、アプリケーションの機能を拡張できるほか、アプリケーションのユーザー インターフェイス \(UI\) をカスタマイズすることもできます。  VSTO アドインと、Visual Studio を使用して作成できる他の種類の Office ソリューションの比較方法については、「[Office ソリューションの開発の概要 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)」を参照してください。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## VSTO アドイン プロジェクトの作成  
 VSTO アドイン プロジェクトを作成するには、**\[新しいプロジェクト\]** ダイアログ ボックスにある VSTO アドイン プロジェクト テンプレートのいずれかを使用します。  これらのテンプレートには必要なアセンブリ参照とプロジェクト ファイルが含まれています。  Visual Studio には、Office のほとんどのアプリケーション用の VSTO アドイン プロジェクト テンプレートが用意されています。  
  
 VSTO アドイン プロジェクトを作成する方法の詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  プロジェクト テンプレートの詳細については、「[Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)」を参照してください。  
  
## VSTO アドイン プロジェクトの開発  
 VSTO アドイン プロジェクトを作成すると、Visual Studio によって ThisAddIn.vb \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] の場合\) または ThisAddIn.cs \(C\# の場合\) というコード ファイルが自動的に作成されます。  このファイルには、VSTO アドインの基礎となる `ThisAddIn` クラスが含まれています。  このクラスのメンバーを使用して、VSTO アドインが読み込まれたとき、またはアンロードされたときにコードを実行したり、ホスト アプリケーションのオブジェクト モデルにアクセスしたりすることができます。また、アプリケーションの機能を拡張することも可能です。  詳細については、「[VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)」を参照してください。  
  
## オブジェクト モデルによるアプリケーションの自動化  
 Microsoft Office アプリケーションのオブジェクト モデルは、VSTO アドインでプログラミングに使用できる多くの型を公開します。  それらの型を使用してアプリケーションを自動化できます。  たとえば、Outlook でプログラムによって電子メールを作成および送信することもできれば、Word で文書を開き、コンテンツを追加することも可能です。  コードでホスト アプリケーションのオブジェクト モデルにアクセスする方法の詳細については、「[VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)」を参照してください。  
  
 特定の Microsoft Office アプリケーションのオブジェクト モデルの詳細については、以下のトピックを参照してください。  
  
-   [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)  
  
-   [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)  
  
-   [Outlook オブジェクト モデルの概要](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath ソリューション](../vsto/infopath-solutions.md)  
  
-   [PowerPoint ソリューション](../vsto/powerpoint-solutions.md)  
  
-   [Project ソリューション](../vsto/project-solutions.md)  
  
-   [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)  
  
## アプリケーションのユーザー インターフェイスのカスタマイズ  
 VSTO アドインを使用してホスト アプリケーションの UI をカスタマイズするためのさまざまな方法があります。  
  
-   Excel や Word の場合、ドキュメントにマネージ コントロールを追加できます。  詳細については、「[VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
-   アプリケーションでサポートされている場合は、リボンをカスタマイズできます。  詳細については、「[リボンの概要](../vsto/ribbon-overview.md)」を参照してください。  
  
-   アプリケーションでサポートされている場合は、カスタム作業ウィンドウを作成できます。  詳細については、「[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)」を参照してください。  
  
-   Outlook では、カスタム フォーム領域を作成できます。  詳細については、「[Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)」を参照してください。  
  
-   すべての Microsoft Office アプリケーションで、VSTO アドインに Windows フォームを表示できます。  
  
 Microsoft Office アプリケーションの UI をカスタマイズする方法の詳細については、「[Office UI のカスタマイズ](../vsto/office-ui-customization.md)」を参照してください。  
  
## 次の手順  
 VSTO アドインの作成方法については、次のチュートリアルを参照してください。  
  
-   [チュートリアル : 初めての Excel 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [チュートリアル : 初めての Outlook 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [チュートリアル : 初めての PowerPoint 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [チュートリアル: 初めての Project 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [チュートリアル : 初めての Word 用 VSTO アドインの作成](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 これらのチュートリアルでは、Visual Studio の Office 開発ツール、および VSTO アドインのプログラミング モデルを紹介します。  
  
 Office プロジェクトの一般的なタスクを解説しているトピックの一覧については、「[Office プログラミングの共通タスク](../vsto/common-tasks-in-office-programming.md)」を参照してください。  
  
## 参照  
 [方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [はじめに &#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)  
  
  