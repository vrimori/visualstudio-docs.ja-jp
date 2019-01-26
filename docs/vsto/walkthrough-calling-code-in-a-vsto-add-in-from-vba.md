---
title: 'チュートリアル: VBA から VSTO アドイン内のコードを呼び出す'
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: faa71d4cefabbb59e7b9b5255cfebf3677e257a5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865750"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>チュートリアル: VBA から VSTO アドイン内のコードを呼び出す
  このチュートリアルでは、VSTO アドインのオブジェクトを Visual Basic for Applications (VBA) アドインや COM VSTO アドインなど、他の Microsoft Office ソリューションに公開する方法について説明します。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 このチュートリアルでは具体的に Excel を使用しますが、ここで説明する概念は Visual Studio で提供されるすべての VSTO アドイン プロジェクト テンプレートに当てはまります。  
  
 このチュートリアルでは、次の作業について説明します。  
  
- 他の Office ソリューションに公開できるクラスを定義する。  
  
- 他の Office ソリューションにクラスを公開する。  
  
- クラスのメソッドを VBA コードから呼び出す。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="create-the-vsto-add-in-project"></a>VSTO アドイン プロジェクトを作成します。  
 まず、Excel 用の VSTO アドイン プロジェクトを作成します。  
  
### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  Excel VSTO アドイン プロジェクト テンプレートを使用して、 **ExcelImportData**という名前の Excel VSTO アドイン プロジェクトを作成します。 詳細については、「[方法 :Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって、 **ThisAddIn.cs** コード ファイルまたは **ThisAddIn.vb** コード ファイルが開かれ、 **ソリューション エクスプローラー** に **ExcelImportData**プロジェクトが追加されます。  
  
## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>他の Office ソリューションに公開できるクラスを定義します。  
 このチュートリアルの目的は、VSTO アドインの `ImportData` というクラスの `AddInUtilities` メソッドを VBA コードから呼び出すことです。 このメソッドは、アクティブなワークシートのセル A1 に文字列を書き込みます。  
  
 `AddInUtilities` クラスを他の Office ソリューションに公開するには、このクラスをパブリックにし、COM から参照できるようにする必要があります。 このクラスの [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) インターフェイスも公開する必要があります。 次の手順で示すコードでは、これらの要件を満たす方法の 1 つを示します。 詳細については、「 [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)」を参照してください。  
  
### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>他の Office ソリューションに公開できるクラスを定義するには  
  
1.  **[プロジェクト]** メニューの **[クラスの追加]** をクリックします。  
  
2.  **[新しい項目の追加]** ダイアログ ボックスで、新しいクラスの名前を **AddInUtilities**に変更し、 **[追加]** をクリックします。  
  
     コード エディターで **AddInUtilities.cs** ファイルまたは **AddInUtilities.vb** ファイルが開きます。  
  
3.  ファイルの先頭に次のステートメントを追加します。  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#2)]  
  
4.  `AddInUtilities` クラスを次のコードで置き換えます。  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
     このコードは、 `AddInUtilities` クラスを COM から参照できるようにし、このクラスに `ImportData` メソッドを追加します。 また、 [クラスは](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) IDispatch `AddInUtilities` インターフェイスを公開するために <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 属性を持ち、COM から参照できるインターフェイスを実装します。  
  
## <a name="expose-the-class-to-other-office-solutions"></a>クラスの他の Office ソリューションを公開します  
 `AddInUtilities` クラスを他の Office ソリューションに公開するには、 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> クラスの `ThisAddIn` メソッドをオーバーライドします。 オーバーライドでは、 `AddInUtilities` クラスのインスタンスを返します。  
  
### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>他の Office ソリューションに AddInUtilities クラスを公開するには  
  
1.  **ソリューション エクスプローラー**で、 **[Excel]** を展開します。  
  
2.  **ThisAddIn.cs** または **ThisAddIn.vb**を右クリックしてから、 **[コードの表示]** をクリックします。  
  
3.  `ThisAddIn` クラスに次のコードを追加します。  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
4.  **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。  
  
     ソリューションがエラーなしでビルドされることを確認します。  
  
## <a name="test-the-vsto-add-in"></a>VSTO アドインのテストします。  
 `AddInUtilities` クラスをさまざまな種類の Office ソリューションから呼び出すことができます。 このチュートリアルでは、Excel ブック内の VBA コードを使用します。 使用することも、Office ソリューションの他の種類の詳細については、次を参照してください。[他の Office ソリューションから VSTO アドイン内のコードを呼び出す](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)します。  
  
### <a name="to-test-your-vsto-add-in"></a>VSTO アドインをテストするには  
  
1.  キーを押して**F5**プロジェクトを実行します。  
  
2.  Excel で、アクティブ ブックを Excel マクロ有効ブック (*.xlsm) として保存します。 このブックは、デスクトップなどの便利な場所に保存します。  
  
3.  リボンの **[開発]** タブをクリックします。  
  
    > [!NOTE]  
    >  **[開発]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「[方法 :リボンの [開発] タブを表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)します。  
  
4.  **[コード]** グループの **[Visual Basic]** をクリックします。  
  
     Visual Basic エディターが開きます。  
  
5.  **[プロジェクト]** ウィンドウで、 **[ThisWorkbook]** をダブルクリックします。  
  
     `ThisWorkbook` オブジェクトのコード ファイルが開きます。  
  
6.  コード ファイルに次の VBA コードを追加します。 このコードは、まずを表す COMAddIn オブジェクトを取得します。、 **ExcelImportData** VSTO アドイン。 次に、コードが COMAddIn オブジェクトのオブジェクトのプロパティを使用して呼び出し、`ImportData`メソッド。  
  
    ```vb  
    Sub CallVSTOMethod()  
        Dim addIn As COMAddIn  
        Dim automationObject As Object  
        Set addIn = Application.COMAddIns("ExcelImportData")  
        Set automationObject = addIn.Object  
        automationObject.ImportData  
    End Sub  
    ```  
  
7.  **F5**キーを押します。  
  
8.  新しい **Imported Data** シートがブックに追加されていることを確認します。 セル A1 に文字列 **This is my data**があることも確認してください。  
  
9. Excel を終了します。  
  
## <a name="next-steps"></a>次の手順  
 VSTO アドインのプログラミングの詳細については、次の各トピックを参照してください。  
  
-   `ThisAddIn` クラスを使用して、ホスト アプリケーションを自動化し、VSTO アドイン プロジェクトの他のタスクを実行する。 詳細については、次を参照してください。[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)します。  
  
-   VSTO アドインにカスタム作業ウィンドウを作成する。 詳細については、次を参照してください。[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)と[方法。カスタム作業ウィンドウをアプリケーションに追加](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)します。  
  
-   VSTO アドインでリボンをカスタマイズします。 詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)と[方法。リボンのカスタマイズの概要](../vsto/how-to-get-started-customizing-the-ribbon.md)します。  
  
## <a name="see-also"></a>関連項目  
 [VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)   
 [他の Office ソリューションから VSTO アドイン内のコードを呼び出す](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Office ソリューションを開発します。](../vsto/developing-office-solutions.md)   
 [方法: Visual Studio での Office プロジェクトを作成します。](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [機能拡張インターフェイスによる UI 機能をカスタマイズします。](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
