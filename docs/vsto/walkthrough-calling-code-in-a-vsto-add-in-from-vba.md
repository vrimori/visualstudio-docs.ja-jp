---
title: "チュートリアル: は、VSTO アドインのコードを VBA から呼び出す |Microsoft ドキュメント"
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
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- Video How tos, Office development in Visual Studio
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
ms.assetid: 9c04d1df-0d93-473c-85fd-02dc2e956c9e
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 66b9c93c9a1c4bcf55b4efc5e95d5b6353f9bd68
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-calling-code-in-a-vsto-add-in-from-vba"></a>チュートリアル : VSTO アドインのコードを VBA から呼び出す
  このチュートリアルでは、VSTO アドインのオブジェクトを Visual Basic for Applications (VBA) アドインや COM VSTO アドインなど、他の Microsoft Office ソリューションに公開する方法について説明します。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 このチュートリアルでは具体的に Excel を使用しますが、ここで説明する概念は Visual Studio で提供されるすべての VSTO アドイン プロジェクト テンプレートに当てはまります。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   他の Office ソリューションに公開できるクラスを定義する。  
  
-   他の Office ソリューションにクラスを公開する。  
  
-   クラスのメソッドを VBA コードから呼び出す。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="creating-the-vsto-add-in-project"></a>VSTO アドイン プロジェクトの作成  
 まず、Excel 用の VSTO アドイン プロジェクトを作成します。  
  
#### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  Excel VSTO アドイン プロジェクト テンプレートを使用して、 **ExcelImportData**という名前の Excel VSTO アドイン プロジェクトを作成します。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって、 **ThisAddIn.cs** コード ファイルまたは **ThisAddIn.vb** コード ファイルが開かれ、 **ソリューション エクスプローラー** に **ExcelImportData**プロジェクトが追加されます。  
  
## <a name="defining-a-class-that-you-can-expose-to-other-office-solutions"></a>他の Office ソリューションに公開できるクラスを定義する  
 このチュートリアルの目的は、VSTO アドインの `ImportData` というクラスの `AddInUtilities` メソッドを VBA コードから呼び出すことです。 このメソッドは、アクティブなワークシートのセル A1 に文字列を書き込みます。  
  
 `AddInUtilities` クラスを他の Office ソリューションに公開するには、このクラスをパブリックにし、COM から参照できるようにする必要があります。 このクラスの [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) インターフェイスも公開する必要があります。 次の手順で示すコードでは、これらの要件を満たす方法の 1 つを示します。 詳細については、「 [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)」を参照してください。  
  
#### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>他の Office ソリューションに公開できるクラスを定義するには  
  
1.  **[プロジェクト]** メニューの **[クラスの追加]**をクリックします。  
  
2.  **[新しい項目の追加]** ダイアログ ボックスで、新しいクラスの名前を **AddInUtilities**に変更し、 **[追加]**をクリックします。  
  
     コード エディターで **AddInUtilities.cs** ファイルまたは **AddInUtilities.vb** ファイルが開きます。  
  
3.  ファイルの先頭に次のステートメントを追加します。  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#2)]  
  
4.  `AddInUtilities` クラスを次のコードで置き換えます。  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
     このコードは、 `AddInUtilities` クラスを COM から参照できるようにし、このクラスに `ImportData` メソッドを追加します。 また、 [クラスは](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) IDispatch `AddInUtilities` インターフェイスを公開するために <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 属性を持ち、COM から参照できるインターフェイスを実装します。  
  
## <a name="exposing-the-class-to-other-office-solutions"></a>他の Office ソリューションにクラスを公開する  
 `AddInUtilities` クラスを他の Office ソリューションに公開するには、 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> クラスの `ThisAddIn` メソッドをオーバーライドします。 オーバーライドでは、 `AddInUtilities` クラスのインスタンスを返します。  
  
#### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>他の Office ソリューションに AddInUtilities クラスを公開するには  
  
1.  **ソリューション エクスプローラー**で、 **[Excel]**を展開します。  
  
2.  **ThisAddIn.cs** または **ThisAddIn.vb**を右クリックしてから、 **[コードの表示]**をクリックします。  
  
3.  `ThisAddIn` クラスに次のコードを追加します。  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
4.  **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。  
  
     ソリューションがエラーなしでビルドされることを確認します。  
  
## <a name="testing-the-vsto-add-in"></a>VSTO アドインのテスト  
 `AddInUtilities` クラスをさまざまな種類の Office ソリューションから呼び出すことができます。 このチュートリアルでは、Excel ブック内の VBA コードを使用します。 使用できる他の種類の Office ソリューションの詳細については、「 [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)」を参照してください。  
  
#### <a name="to-test-your-vsto-add-in"></a>VSTO アドインをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  Excel で、アクティブ ブックを Excel マクロ有効ブック (*.xlsm) として保存します。 このブックは、デスクトップなどの便利な場所に保存します。  
  
3.  リボンの **[開発]** タブをクリックします。  
  
    > [!NOTE]  
    >  **[開発]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「 [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)」を参照してください。  
  
4.  **[コード]** グループの **[Visual Basic]**をクリックします。  
  
     Visual Basic エディターが開きます。  
  
5.  **[プロジェクト]** ウィンドウで、 **[ThisWorkbook]**をダブルクリックします。  
  
     `ThisWorkbook` オブジェクトのコード ファイルが開きます。  
  
6.  コード ファイルに次の VBA コードを追加します。 このコードは最初を表す COMAddIn オブジェクトを取得、 **ExcelImportData** VSTO アドイン。 次に、コードが COMAddIn オブジェクトのオブジェクトのプロパティを使用して呼び出す、、`ImportData`メソッドです。  
  
    ```  
    Sub CallVSTOMethod()  
        Dim addIn As COMAddIn  
        Dim automationObject As Object  
        Set addIn = Application.COMAddIns("ExcelImportData")  
        Set automationObject = addIn.Object  
        automationObject.ImportData  
    End Sub  
    ```  
  
7.  F5 キーを押します。  
  
8.  新しい **Imported Data** シートがブックに追加されていることを確認します。 セル A1 に文字列 **This is my data**があることも確認してください。  
  
9. Excel を終了します。  
  
## <a name="next-steps"></a>次の手順  
 VSTO アドインのプログラミングの詳細については、次の各トピックを参照してください。  
  
-   `ThisAddIn` クラスを使用して、ホスト アプリケーションを自動化し、VSTO アドイン プロジェクトの他のタスクを実行する。 詳細については、「 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)」を参照してください。  
  
-   VSTO アドインにカスタム作業ウィンドウを作成する。 詳細については、次を参照してください。[カスタム作業ウィンドウの](../vsto/custom-task-panes.md)と[する方法: カスタム作業ウィンドウをアプリケーションに追加](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)です。  
  
-   VSTO アドインでリボンをカスタマイズする。 詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)と[する方法: リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)です。  
  
## <a name="see-also"></a>参照  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [他の Office ソリューションから VSTO アドインのコードを呼び出す](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Office ソリューションの開発](../vsto/developing-office-solutions.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [機能拡張インターフェイスによる UI 機能のカスタマイズ](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  