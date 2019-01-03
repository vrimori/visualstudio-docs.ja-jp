---
title: VSTO アドインをプログラミングします。
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b3520eb8af160a12de5cb74fa40094004e041c0e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830652"
---
# <a name="program-vsto-add-ins"></a>VSTO アドインをプログラミングします。
  VSTO アドインを作成して Microsoft Office アプリケーションを拡張するときは、プロジェクトの `ThisAddIn` クラスに対して直接コードを記述します。 このクラスを使用し、Microsoft Office ホスト アプリケーションのオブジェクト モデルにアクセスする、アプリケーションのユーザー インターフェイス (UI) をカスタマイズする、その他の Office ソリューションに VSTO アドインのオブジェクトを公開するなどの作業を実行できます。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 VSTO アドイン プロジェクトのコードの記述には、Visual Studio の他のプロジェクトの種類とは異なる点があります。 相違点の多くは、Office オブジェクト モデルがマネージド コードに公開される方法に起因しています。 詳細については、次を参照してください。 [Office ソリューションでコードを記述](../vsto/writing-code-in-office-solutions.md)します。  
  
 Visual Studio の Office 開発ツールを使用して作成できます VSTO アドインとソリューションの他の種類に関する全般情報を参照してください。 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)します。  
  
## <a name="use-the-thisaddin-class"></a>ThisAddIn クラスを使用します。  
 VSTO アドイン コードの記述は `ThisAddIn` クラスから開始することができます。 Visual Studio でこのクラスを自動的に生成する、 *ThisAddIn.vb* (で[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) または*ThisAddIn.cs* (c#) のコードでは、VSTO アドイン プロジェクト内のファイル。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は、Microsoft Office アプリケーションが VSTO アドインを読み込むと、このクラスを自動的にインスタンス化します。  
  
 `ThisAddIn` クラスには既定のイベント ハンドラーが 2 つあります。 VSTO アドインが読み込まれるときにコードを実行するには、 `ThisAddIn_Startup` イベント ハンドラーにコードを追加します。 VSTO アドインが読み込み解除される直前にコードを実行するには、 `ThisAddIn_Shutdown` イベント ハンドラーにコードを追加します。 これらのイベント ハンドラーの詳細については、次を参照してください。 [Office プロジェクト内のイベント](../vsto/events-in-office-projects.md)します。  
  
> [!NOTE]  
>  Outlook の場合、既定では、VSTO アドインが読み込み解除されるときに `ThisAddIn_Shutdown` イベント ハンドラーが常に呼び出されるとは限りません。 詳細については、次を参照してください。 [Office プロジェクト内のイベント](../vsto/events-in-office-projects.md)します。  
  
### <a name="access-the-object-model-of-the-host-application"></a>ホスト アプリケーションのオブジェクト モデルへのアクセスします。  
 ホスト アプリケーションのオブジェクト モデルにアクセスするには、 `Application` クラスの `ThisAddIn` フィールドを使用します。 このフィールドはホスト アプリケーションの現在のインスタンスを表すオブジェクトを返します。 次の表は各 VSTO アドイン プロジェクトの `Application` フィールドの戻り値の型をまとめたものです。  
  
|ホスト アプリケーション|戻り値の型|  
|----------------------|-----------------------|  
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|  
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|  
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|  
|Microsoft Office PowerPoint|<xref:Microsoft.Office.Interop.PowerPoint.Application>|  
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|  
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|  
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|  
  
 次のコード例を使用する方法を示しています、`Application`フィールドを Microsoft Office Excel 用 VSTO アドインで新しいブックを作成します。 この例は `ThisAddIn` クラスから実行することを意図しています。  
  
```vb  
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 同じ処理を `ThisAddIn` クラスの外から行うには、 `Globals` オブジェクトを使用して `ThisAddIn` クラスにアクセスします。 詳細については、`Globals`オブジェクトを参照してください[Office プロジェクト内のオブジェクトへのアクセスをグローバル](../vsto/global-access-to-objects-in-office-projects.md)します。  
  
```vb  
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 特定の Microsoft Office アプリケーションのオブジェクト モデルの詳細については、以下のトピックを参照してください。  
  
-   [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)  
  
-   [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)  
  
-   [Outlook オブジェクト モデルの概要](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath ソリューション](../vsto/infopath-solutions.md)  
  
-   [PowerPoint ソリューション](../vsto/powerpoint-solutions.md)  
  
-   [プロジェクトから成るソリューション](../vsto/project-solutions.md)  
  
-   [Visio オブジェクト モデルの概要](../vsto/visio-object-model-overview.md)  
  
###  <a name="AccessingDocuments"></a> Office アプリケーションの起動時にドキュメントへのアクセスします。  
 すべての [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] アプリケーションが起動時にドキュメントを自動的に開くわけではありません。 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] アプリケーションの場合、起動時にドキュメントは開きません。 そのため、コードを追加しないでください、`ThisAdd-In_Startup`イベント ハンドラーの場合は、コードがドキュメントを開く必要があります。 代わりに、ユーザーがドキュメントを作成するとき、または開くときに Office アプリケーションが発生させるイベントにそのコードを追加します。 この方法により、コードがドキュメントに操作を実行する前にドキュメントが確実に開きます。  
  
 次のコード例は、ユーザーがドキュメントを作成した、または既存のドキュメントを開いたときにのみ、Word のドキュメントと連動します。  
  
 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]  
  
### <a name="thisaddin-members-to-use-for-other-tasks"></a>その他のタスクを使用する ThisAddIn メンバー  
 次の表は、他の一般的なタスクに関する説明とタスクを実行するために使用できる `ThisAddIn` クラスのメンバーをまとめたものです。  
  
|タスク|使用するメンバー|  
|----------|-------------------|  
|VSTO アドインが読み込まれるときに VSTO アドインを初期化するコードを実行します。|`ThisAddIn_Startup` メソッドにコードを追加します。 これは <xref:Microsoft.Office.Tools.AddInBase.Startup> イベントの既定のイベント ハンドラーです。 詳細については、次を参照してください。 [Office プロジェクト内のイベント](../vsto/events-in-office-projects.md)します。|  
|VSTO アドインが読み込み解除される前に VSTO アドインにより使用されるリソースを消去するコードを実行します。|`ThisAddIn_Shutdown` メソッドにコードを追加します。 これは <xref:Microsoft.Office.Tools.AddInBase.Shutdown> イベントの既定のイベント ハンドラーです。 詳細については、次を参照してください。 [Office プロジェクト内のイベント](../vsto/events-in-office-projects.md)します。 **注:** Outlook の場合、既定では、VSTO アドインが読み込み解除されるときに `ThisAddIn_Startup` イベント ハンドラーが常に呼び出されるとは限りません。 詳細については、次を参照してください。 [Office プロジェクト内のイベント](../vsto/events-in-office-projects.md)します。|  
|カスタム作業ウィンドウを表示します。|`CustomTaskPanes` フィールドを使用します。 詳細については、次を参照してください。[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)します。|  
|その他の Microsoft Office ソリューションに VSTO アドインのオブジェクトを公開します。|<xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> メソッドをオーバーライドします。 詳細については、次を参照してください。[他の Office ソリューションから VSTO アドイン内のコードを呼び出す](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)します。|  
|機能拡張インターフェイスを実装することで Microsoft Office システムの機能をカスタマイズします。|<xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> メソッドをオーバーライドし、このインターフェイスを実装するクラスのインスタンスを返します。 詳細については、次を参照してください。[機能拡張インターフェイスによる UI のカスタマイズ機能](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)します。 **注:** リボン UI をカスタマイズするには、<xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> メソッドをオーバーライドすることもできます。|  
  
### <a name="understand-the-design-of-the-thisaddin-class"></a>ThisAddIn クラスの設計を理解します。  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]を対象とするプロジェクトでは、 <xref:Microsoft.Office.Tools.AddIn> はインターフェイスです。 `ThisAddIn` クラスは <xref:Microsoft.Office.Tools.AddInBase> クラスから派生します。 この基本クラスは [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] でそのメンバーのすべての呼び出しを <xref:Microsoft.Office.Tools.AddIn> インターフェイスの内部実装にリダイレクトします。  
  
 Outlook の VSTO アドイン プロジェクトで、`ThisAddIn` クラスは .NET Framework 3.5 を対象とするプロジェクトの `Microsoft.Office.Tools.Outlook.OutlookAddIn` クラスと [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] を対象とするプロジェクトの <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> から誘導されます。 これらの基本クラスは、フォーム領域をサポートするための追加の機能をいくつか提供します。 フォーム領域の詳細については、次を参照してください。[作成の Outlook フォーム領域](../vsto/creating-outlook-form-regions.md)します。  
  
## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Microsoft Office アプリケーションのユーザー インターフェイスをカスタマイズします。  
 VSTO アドインを使用すれば、Microsoft Office アプリケーションの UI をプログラミングでカスタマイズできます。 たとえば、Outlook でリボンをカスタマイズしたり、カスタム作業ウィンドウを表示したり、カスタム フォーム領域を作成したりできます。 詳細については、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)します。  
  
 Visual Studio は、カスタム作業ウィンドウの作成、リボンのカスタマイズ、Outlook フォーム領域の作成に使用できるデザイナーとクラスを提供します。 これらのデザイナーやクラスはこれらの機能のカスタマイズ プロセスの簡素化に役立ちます。 詳細については、次を参照してください。[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)、[リボン デザイナー](../vsto/ribbon-designer.md)、および[作成の Outlook フォーム領域](../vsto/creating-outlook-form-regions.md)します。  
  
 クラスとデザイナーでサポートされない方法でこれらの機能をカスタマイズする場合、VSTO アドインに *拡張機能インターフェイス* を実装する方法でカスタマイズすることもできます。 詳細については、次を参照してください。[機能拡張インターフェイスによる UI のカスタマイズ機能](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)します。  
  
 さらに、文書やブックの動作を拡張するホスト項目を生成する方法で Word 文書や Excel ブックを変更できます。 この方法で、管理されているコントロールを文書とワークシートに追加できます。 詳細については、次を参照してください。[拡張 Word 文書や Excel ブックを実行時に VSTO アドインで](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)します。  
  
## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>他のソリューションから VSTO アドイン内のコードを呼び出す  
 VSTO アドインのオブジェクトを、他の Microsoft Office ソリューションを含む、他のソリューションに公開できます。 このことは、VSTO アドインが他のソリューションで使用可能なサービスを含む場合に便利です。 たとえば、この場合は、web サービスから受け取る財務データについて計算を実行する Microsoft Office Excel の VSTO アドインである場合は、その他のソリューションは実行時に Excel VSTO アドインを呼び出すことによってこれらの計算を実行できます。  
  
 詳細については、次を参照してください。[他の Office ソリューションから VSTO アドイン内のコードを呼び出す](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションを開発します。](../vsto/developing-office-solutions.md)   
 [Word 文書と Excel ブックを実行時に VSTO アドインで拡張します。](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [他の Office ソリューションから VSTO アドイン内のコードを呼び出す](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [チュートリアル: VBA から VSTO アドイン内のコードを呼び出す](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [機能拡張インターフェイスによる UI 機能をカスタマイズします。](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)   
 [方法: Visual Studio での Office プロジェクトを作成します。](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Office ソリューションでコードを記述します。](../vsto/writing-code-in-office-solutions.md)  
