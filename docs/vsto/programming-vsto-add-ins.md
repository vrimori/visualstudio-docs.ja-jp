---
title: VSTO アドインをプログラミングします。
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 52297a90f562ac534d0087c273cde05f021711af
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692874"
---
# <a name="program-vsto-add-ins"></a>VSTO アドインをプログラミングします。
  VSTO アドインを作成して Microsoft Office アプリケーションを拡張するときは、プロジェクトの `ThisAddIn` クラスに対して直接コードを記述します。 このクラスを使用し、Microsoft Office ホスト アプリケーションのオブジェクト モデルにアクセスする、アプリケーションのユーザー インターフェイス (UI) をカスタマイズする、その他の Office ソリューションに VSTO アドインのオブジェクトを公開するなどの作業を実行できます。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 VSTO アドイン プロジェクトのコードの記述には、Visual Studio の他のプロジェクトの種類とは異なる点があります。 相違点の多くは、Office オブジェクト モデルがマネージ コードに公開される方法に起因しています。 詳細については、次を参照してください。 [Office ソリューションでコードを記述](../vsto/writing-code-in-office-solutions.md)です。  
  
 Visual Studio での Office 開発ツールを使用して作成できる VSTO アドインと他の種類のソリューションに関する全般については、次を参照してください。 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)です。  
  
## <a name="use-the-thisaddin-class"></a>ThisAddIn クラスを使用します。  
 VSTO アドイン コードの記述は `ThisAddIn` クラスから開始することができます。 Visual Studio で、このクラスを自動的に生成する、 *ThisAddIn.vb* (で[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) または*ThisAddIn.cs* (C# の場合) のコードでは、VSTO アドイン プロジェクトのファイルです。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は、Microsoft Office アプリケーションが VSTO アドインを読み込むと、このクラスを自動的にインスタンス化します。  
  
 `ThisAddIn` クラスには既定のイベント ハンドラーが 2 つあります。 VSTO アドインが読み込まれるときにコードを実行するには、 `ThisAddIn_Startup` イベント ハンドラーにコードを追加します。 VSTO アドインが読み込み解除される直前にコードを実行するには、 `ThisAddIn_Shutdown` イベント ハンドラーにコードを追加します。 これらのイベント ハンドラーの詳細については、次を参照してください。 [Office プロジェクトのイベント](../vsto/events-in-office-projects.md)です。  
  
> [!NOTE]  
>  Outlook の場合、既定では、VSTO アドインが読み込み解除されるときに `ThisAddIn_Shutdown` イベント ハンドラーが常に呼び出されるとは限りません。 詳細については、次を参照してください。 [Office プロジェクトのイベント](../vsto/events-in-office-projects.md)です。  
  
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
  
 次のコード例は、 `Application` フィールドを使用して Microsoft Office Excel の VSTO アドインで新しいブックを作成する方法を示しています。 この例は `ThisAddIn` クラスから実行することを意図しています。  
  
```vb  
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 同じ処理を `ThisAddIn` クラスの外から行うには、 `Globals` オブジェクトを使用して `ThisAddIn` クラスにアクセスします。 詳細については、`Globals`オブジェクトを参照してください[Office プロジェクト内のオブジェクトへのアクセスをグローバル](../vsto/global-access-to-objects-in-office-projects.md)です。  
  
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
  
###  <a name="AccessingDocuments"></a> Office アプリケーションの起動時に、ドキュメントへのアクセスします。  
 すべての [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] アプリケーションが起動時にドキュメントを自動的に開くわけではありません。 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] アプリケーションの場合、起動時にドキュメントは開きません。 したがって、内のコードを追加しない、`ThisAdd-In_Startup`コードでは、ドキュメントを開く場合、イベント ハンドラー。 代わりに、ユーザーがドキュメントを作成するとき、または開くときに Office アプリケーションが発生させるイベントにそのコードを追加します。 この方法により、コードがドキュメントに操作を実行する前にドキュメントが確実に開きます。  
  
 次のコード例は、ユーザーがドキュメントを作成した、または既存のドキュメントを開いたときにのみ、Word のドキュメントと連動します。  
  
 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]  
  
### <a name="thisaddin-members-to-use-for-other-tasks"></a>他のタスクを使用する ThisAddIn メンバー  
 次の表は、他の一般的なタスクに関する説明とタスクを実行するために使用できる `ThisAddIn` クラスのメンバーをまとめたものです。  
  
|タスク|使用するメンバー|  
|----------|-------------------|  
|VSTO アドインが読み込まれるときに VSTO アドインを初期化するコードを実行します。|`ThisAddIn_Startup` メソッドにコードを追加します。 これは <xref:Microsoft.Office.Tools.AddInBase.Startup> イベントの既定のイベント ハンドラーです。 詳細については、次を参照してください。 [Office プロジェクトのイベント](../vsto/events-in-office-projects.md)です。|  
|VSTO アドインが読み込み解除される前に VSTO アドインにより使用されるリソースを消去するコードを実行します。|`ThisAddIn_Shutdown` メソッドにコードを追加します。 これは <xref:Microsoft.Office.Tools.AddInBase.Shutdown> イベントの既定のイベント ハンドラーです。 詳細については、次を参照してください。 [Office プロジェクトのイベント](../vsto/events-in-office-projects.md)です。 **注:** Outlook では、既定では、`ThisAddIn_Startup`イベント ハンドラーは、VSTO アドインを読み込むときに常に呼び出されません。 詳細については、次を参照してください。 [Office プロジェクトのイベント](../vsto/events-in-office-projects.md)です。|  
|カスタム作業ウィンドウを表示します。|`CustomTaskPanes` フィールドを使用します。 詳細については、次を参照してください。[カスタム作業ウィンドウの](../vsto/custom-task-panes.md)します。|  
|その他の Microsoft Office ソリューションに VSTO アドインのオブジェクトを公開します。|<xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> メソッドをオーバーライドします。 詳細については、次を参照してください。[他の Office ソリューションから VSTO アドイン内のコードを呼び出す](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)です。|  
|機能拡張インターフェイスを実装することで Microsoft Office システムの機能をカスタマイズします。|<xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> メソッドを上書きし、このインターフェイスを実装するクラスのインスタンスを返します。 詳細については、次を参照してください。[機能拡張インターフェイスによる UI のカスタマイズ機能](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)します。 **注:** リボン UI をカスタマイズするには、オーバーライドの<xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A>メソッドです。|  
  
### <a name="understand-the-design-of-the-thisaddin-class"></a>ThisAddIn クラスの設計を把握します。  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]を対象とするプロジェクトでは、 <xref:Microsoft.Office.Tools.AddIn> はインターフェイスです。 `ThisAddIn` クラスは <xref:Microsoft.Office.Tools.AddInBase> クラスから派生します。 この基本クラスは <xref:Microsoft.Office.Tools.AddIn> でそのメンバーのすべての呼び出しを [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]インターフェイスの内部実装にリダイレクトします。  
  
 Outlook の VSTO アドイン プロジェクトで、`ThisAddIn`クラスから派生、`Microsoft.Office.Tools.Outlook.OutlookAddIn`クラス、.NET Framework 3.5 をターゲットとするプロジェクトと<xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase>対象とするプロジェクトで、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]です。 これらの基本クラスは、フォーム領域をサポートするための追加の機能をいくつか提供します。 フォーム領域の詳細については、次を参照してください。[作成 Outlook フォーム領域の](../vsto/creating-outlook-form-regions.md)します。  
  
## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Microsoft Office アプリケーションのユーザー インターフェイスをカスタマイズします。  
 VSTO アドインを使用すれば、Microsoft Office アプリケーションの UI をプログラミングでカスタマイズできます。 たとえば、Outlook でリボンをカスタマイズしたり、カスタム作業ウィンドウを表示したり、カスタム フォーム領域を作成したりできます。 詳細については、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)です。  
  
 Visual Studio は、カスタム作業ウィンドウの作成、リボンのカスタマイズ、Outlook フォーム領域の作成に使用できるデザイナーとクラスを提供します。 これらのデザイナーやクラスはこれらの機能のカスタマイズ プロセスの簡素化に役立ちます。 詳細については、次を参照してください。[カスタム作業ウィンドウの](../vsto/custom-task-panes.md)、[リボン デザイナー](../vsto/ribbon-designer.md)、および[作成 Outlook フォーム領域の](../vsto/creating-outlook-form-regions.md)します。  
  
 クラスとデザイナーでサポートされない方法でこれらの機能をカスタマイズする場合、VSTO アドインに *拡張機能インターフェイス* を実装する方法でカスタマイズすることもできます。 詳細については、次を参照してください。[機能拡張インターフェイスによる UI のカスタマイズ機能](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)します。  
  
 さらに、文書やブックの動作を拡張するホスト項目を生成する方法で Word 文書や Excel ブックを変更できます。 この方法で、管理されているコントロールを文書とワークシートに追加できます。 詳細については、次を参照してください。[拡張 Word 文書と実行時に VSTO アドイン内の Excel ブック](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)です。  
  
## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>他のソリューションから VSTO アドイン内のコードを呼び出す  
 VSTO アドインのオブジェクトを、他の Microsoft Office ソリューションを含む、他のソリューションに公開できます。 このことは、VSTO アドインが他のソリューションで使用可能なサービスを含む場合に便利です。 たとえば、Web サービスから受け取る財務データについて計算を実行する、Microsoft Office Excel 向けの VSTO アドインがある場合、他のソリューションは、実行時に Excel VSTO アドインを呼び出すことで、これらの計算を実行できます。  
  
 詳細については、次を参照してください。[他の Office ソリューションから VSTO アドイン内のコードを呼び出す](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションを開発します。](../vsto/developing-office-solutions.md)   
 [Word 文書と実行時に VSTO アドイン内の Excel ブックを拡張します。](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [その他の Office ソリューションから VSTO アドイン内のコードを呼び出す](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [チュートリアル: は、VSTO アドインのコードを VBA から呼び出す](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [機能拡張インターフェイスによる UI 機能をカスタマイズします。](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [Office ソリューションでコードを記述します。](../vsto/writing-code-in-office-solutions.md)  
  
  