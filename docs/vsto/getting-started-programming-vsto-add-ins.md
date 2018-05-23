---
title: VSTO アドインのプログラミングを始める
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7249c3971c8008f70b9e5add79adddde17fe6a82
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2018
---
# <a name="get-started-programming-vsto-add-ins"></a>VSTO アドインのプログラミングを始める
  VSTO アドインを使用することにより、Microsoft Office アプリケーションを自動化し、アプリケーションの機能を拡張できるほか、アプリケーションのユーザー インターフェイス (UI) をカスタマイズすることもできます。 Visual Studio を使用して作成することができます、VSTO アドインと Office ソリューションの他の種類との比較に関する情報を参照してください。 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)です。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="create-vsto-add-in-projects"></a>VSTO アドイン プロジェクトを作成します。  
 VSTO アドイン プロジェクトを作成する VSTO アドイン プロジェクトのテンプレートのいずれかを使用して、**新しいプロジェクト** ダイアログ ボックス。 これらのテンプレートには必要なアセンブリ参照とプロジェクト ファイルが含まれています。 Visual Studio には、Office のほとんどのアプリケーション用の VSTO アドイン プロジェクト テンプレートが用意されています。  
  
 VSTO アドイン プロジェクトを作成する方法の詳細については、次を参照してください。[する方法: Visual Studio で作成する Office プロジェクト](../vsto/how-to-create-office-projects-in-visual-studio.md)です。 プロジェクト テンプレートの詳細については、次を参照してください。 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)です。  
  
## <a name="develop-vsto-add-in-projects"></a>VSTO アドイン プロジェクトを開発します。  
 VSTO アドイン プロジェクトを作成すると、Visual Studio は自動的に作成、 *ThisAddIn.vb* (で[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) または*ThisAddIn.cs* (コードでは、C# の場合) ファイル。 このファイルが含まれています、`ThisAddIn`クラスで、VSTO アドインの基礎を提供します。 このクラスのメンバーを使用して、VSTO アドインが読み込まれたとき、またはアンロードされたときにコードを実行したり、ホスト アプリケーションのオブジェクト モデルにアクセスしたりすることができます。また、アプリケーションの機能を拡張することも可能です。 詳細については、次を参照してください。[プログラムは、VSTO アドイン](../vsto/programming-vsto-add-ins.md)です。  
  
## <a name="automate-applications-by-using-the-object-models"></a>オブジェクト モデルを使用してアプリケーションを自動化します。  
 Microsoft Office アプリケーションのオブジェクト モデルは、VSTO アドインでプログラミングに使用できる多くの型を公開します。 それらの型を使用してアプリケーションを自動化できます。 たとえば、Outlook でプログラムによって電子メールを作成および送信することもできれば、Word で文書を開き、コンテンツを追加することも可能です。 コードで、ホスト アプリケーションのオブジェクト モデルにアクセスする方法の詳細については、次を参照してください。[プログラムは、VSTO アドイン](../vsto/programming-vsto-add-ins.md)です。  
  
 特定の Microsoft Office アプリケーションのオブジェクト モデルの詳細については、以下のトピックを参照してください。  
  
-   [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)  
  
-   [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)  
  
-   [Outlook オブジェクト モデルの概要](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath ソリューション](../vsto/infopath-solutions.md)  
  
-   [PowerPoint ソリューション](../vsto/powerpoint-solutions.md)  
  
-   [プロジェクトから成るソリューション](../vsto/project-solutions.md)  
  
-   [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)  
  
## <a name="customize-the-user-interface-of-applications"></a>アプリケーションのユーザー インターフェイスをカスタマイズします。  
 VSTO アドインを使用してホスト アプリケーションの UI をカスタマイズするためのさまざまな方法があります。  
  
-   Excel や Word の場合、ドキュメントにマネージ コントロールを追加できます。 詳細については、次を参照してください。[拡張 Word 文書と実行時に VSTO アドイン内の Excel ブック](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)です。  
  
-   アプリケーションでサポートされている場合は、リボンをカスタマイズできます。 詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)です。  
  
-   アプリケーションでサポートされている場合は、カスタム作業ウィンドウを作成できます。 詳細については、次を参照してください。[カスタム作業ウィンドウの](../vsto/custom-task-panes.md)します。  
  
-   Outlook では、カスタム フォーム領域を作成できます。 詳細については、次を参照してください。[作成 Outlook フォーム領域の](../vsto/creating-outlook-form-regions.md)します。  
  
-   すべての Microsoft Office アプリケーションで、VSTO アドインに Windows フォームを表示できます。  
  
 Microsoft Office アプリケーションの UI をカスタマイズする方法の詳細については、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)です。  
  
## <a name="next-steps"></a>次の手順  
 VSTO アドインの作成方法については、次のチュートリアルを参照してください。  
  
-   [Excel 用チュートリアル: を初めて VSTO アドインの作成します。](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [チュートリアル: は、最初に VSTO アドイン Outlook の作成します。](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [チュートリアル: 初めて VSTO アドインの PowerPoint を作成します。](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [チュートリアル: は、最初に VSTO アドイン プロジェクトの作成します。](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [チュートリアル: 初めて VSTO アドインの Word の作成します。](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 これらのチュートリアルでは、Visual Studio の Office 開発ツール、および VSTO アドインのプログラミング モデルを紹介します。  
  
 Office プロジェクトの一般的なタスクを解説しているトピックの一覧は、次を参照してください。 [Office プログラミングの共通タスク](../vsto/common-tasks-in-office-programming.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [開始&#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Office ソリューションでコードを記述します。](../vsto/writing-code-in-office-solutions.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)  
  
  