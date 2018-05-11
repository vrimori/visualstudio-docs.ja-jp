---
title: 'チュートリアル: 実行時における VSTO ワークシートにコントロールを追加するアドインのプロジェクト |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47c647e2b3af6941f7b4a4d6f28eccfac2b31e2d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>チュートリアル : 実行時における VSTO アドイン プロジェクトのワークシートへのコントロールの追加
  Excel VSTO アドインを使用して、任意の開いているワークシートにコントロールを追加できます。 このチュートリアルでは、リボンを使用してユーザーがワークシートに <xref:Microsoft.Office.Tools.Excel.Controls.Button>、<xref:Microsoft.Office.Tools.Excel.NamedRange>、および <xref:Microsoft.Office.Tools.Excel.ListObject> を追加できるようにする方法を説明します。 詳細については、次を参照してください。[を実行時に Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)です。  
  
 **適用されます:**このトピックの情報は、Excel の VSTO アドイン プロジェクトに適用されます。 詳細については、「[Office アプリケーションおよびプロジェクトの種類別の使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   ワークシートにコントロールを追加するためのユーザー インターフェイス (UI) を提供する。  
  
-   ワークシートにコントロールを追加する。  
  
-   ワークシートからコントロールを削除する。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## <a name="creating-a-new-excel-vsto-add-in-project"></a>新しい Excel VSTO アドイン プロジェクトの作成  
 まず、Excel VSTO アドイン プロジェクトを作成します。  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project"></a>新しい Excel VSTO アドイン プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、名前の Excel VSTO アドイン プロジェクトを作成**ExcelDynamicControls**です。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
2.  参照を追加、 **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll**アセンブリ。 この参照は、このチュートリアルの後半で Windows フォーム コントロールをワークシートにプログラムを使用して追加するのに必要です。  
  
## <a name="providing-a-ui-to-add-controls-to-a-worksheet"></a>ワークシートにコントロールを追加するための UI の提供  
 Excel のリボンにカスタム タブを追加します。 ユーザーはタブにあるチェック ボックスをオンにして、ワークシートにコントロールを追加できます。  
  
#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>ワークシートにコントロールを追加するための UI を提供するには  
  
1.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、**リボン (ビジュアル デザイナー)**、クリックして**追加**です。  
  
     という名前のファイル**Ribbon1.cs**または**Ribbon1.vb**リボン デザイナーで開き、既定のタブとグループが表示されます。  
  
3.  **Office リボン コントロール**のタブ、**ツールボックス**、CheckBox コントロールをドラッグして**group1**です。  
  
4.  **[CheckBox1]** をクリックしてオンにします。  
  
5.  **[プロパティ]** ウィンドウで、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**Button**|  
    |**Label**|**Button**|  
  
6.  **group1**に 2 つ目のチェック ボックスを追加し、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**NamedRange**|  
    |**Label**|**NamedRange**|  
  
7.  3 番目のチェック ボックスを追加**group1**、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**ListObject**|  
    |**Label**|**ListObject**|  
  
## <a name="adding-controls-to-the-worksheet"></a>ワークシートへのコントロールの追加  
 マネージ コントロールは、ホスト項目に対してのみ追加できます。これは、コンテナーとして機能します。 VSTO アドイン プロジェクトは任意の開いているブックを操作するため、VSTO アドインはワークシートをホスト項目に変換するか、または既存のホスト項目を取得してから、コントロールを追加します。 開いているワークシートに基づく <xref:Microsoft.Office.Tools.Excel.Worksheet> ホスト項目を生成するように、各コントロールのクリック イベント ハンドラーにコードを追加します。 次に、ワークシートの現在選択されている位置に <xref:Microsoft.Office.Tools.Excel.Controls.Button>、<xref:Microsoft.Office.Tools.Excel.NamedRange>、および <xref:Microsoft.Office.Tools.Excel.ListObject> を追加します。  
  
#### <a name="to-add-controls-to-a-worksheet"></a>ワークシートにコントロールを追加するには  
  
1.  リボン デザイナーで、ダブルクリック**ボタン**です。  
  
     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>のイベント ハンドラー、**ボタン** チェック ボックスは、コード エディターでを開きます。  
  
2.  `Button_Click` イベント ハンドラーを次のコードで置き換えます。  
  
     このコードでは、`GetVstoObject` メソッドを使用してブックの最初のワークシートを表すホスト項目を取得し、現在選択されているセルに <xref:Microsoft.Office.Tools.Excel.Controls.Button> コントロールを追加します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]  
  
3.  **ソリューション エクスプ ローラー**、Ribbon1.cs または Ribbon1.vb を選択します。  
  
4.  **ビュー**  メニューのをクリックして**デザイナー**です。  
  
5.  リボン デザイナーで、ダブルクリック**NamedRange**です。  
  
6.  `NamedRange_Click` イベント ハンドラーを次のコードで置き換えます。  
  
     このコードでは、`GetVstoObject` メソッドを使用してブックの最初のワークシートを表すホスト項目を取得し、現在選択されている (1 つまたは複数の) セルの <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを定義します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]  
  
7.  リボン デザイナーで、ダブルクリック**ListObject**です。  
  
8.  `ListObject_Click` イベント ハンドラーを次のコードで置き換えます。  
  
     このコードでは、`GetVstoObject` メソッドを使用してブックの最初のワークシートを表すホスト項目を取得し、現在選択されている (1 つまたは複数の) セルの <xref:Microsoft.Office.Tools.Excel.ListObject> を定義します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]  
  
9. リボン コード ファイルの先頭に次のステートメントを追加します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]  
  
## <a name="removing-controls-from-the-worksheet"></a>ワークシートからコントロールを削除する。  
 ワークシートが保存されて閉じられるとき、コントロールは保持されません。 ワークシートを保存する前に、生成されたすべての Windows フォーム コントロールをプログラムを使用して削除する必要があります。そうしないと、ワークシートを再び開いたときに、コントロールのアウトラインのみが表示されます。 生成されたホスト項目のコントロール コレクションから Windows フォーム コントロールを削除するコードを <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> イベントに追加します。 詳細については、「 [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md)」を参照してください。  
  
#### <a name="to-remove-controls-from-the-worksheet"></a>ワークシートからコントロールを削除するには  
  
1.  **ソリューション エクスプ ローラー**、ThisAddIn.cs または ThisAddIn.vb を選択します。  
  
2.  **ビュー**  メニューのをクリックして**コード**です。  
  
3.  次のメソッドを ThisAddIn クラスに追加します。 このコードはブックの最初のワークシートを取得し、`HasVstoObject` メソッドを使用して、ワークシートにワークシート オブジェクトが生成されているかどうかを確認します。 生成されたワークシート オブジェクトにコントロールがある場合、コードはそのワークシート オブジェクトを取得し、コントロール コレクションを反復処理してコントロールを削除します。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]  
  
4.  C# では、<xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> イベントのイベント ハンドラーを作成する必要があります。 このコードを `ThisAddIn_Startup` メソッドに配置できます。 イベント ハンドラーの作成の詳細については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。 `ThisAddIn_Startup` メソッドを次のコードに置き換えます。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]  
  
## <a name="testing-the-solution"></a>ソリューションのテスト  
 リボンのカスタム タブからコントロールを選択し、ワークシートに追加します。 ワークシートを保存すると、これらのコントロールは削除されます。  
  
#### <a name="to-test-the-solution"></a>ソリューションをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  Sheet1 で任意のセルを選択します。  
  
3.  **[アドイン]** タブをクリックします。  
  
4.  **Group1**グループで、**ボタン**です。  
  
     選択したセルにボタンが表示されます。  
  
5.  Sheet1 で別のセルを選択します。  
  
6.  **Group1**グループで、 **NamedRange**です。  
  
     選択したセルに名前付き範囲が定義されます。  
  
7.  Sheet1 で一連のセルを選択します。  
  
8.  **Group1**グループで、 **ListObject**です。  
  
     選択したセルにリスト オブジェクトが追加されます。  
  
9. ワークシートを保存します。  
  
     Sheet1 に追加したコントロールは表示されなくなります。  
  
## <a name="next-steps"></a>次の手順  
 Excel VSTO アドイン プロジェクトのコントロールの詳細については、以下のトピックをご覧ください。  
  
-   コントロールをワークシートに保存する方法については、Excel VSTO アドイン ダイナミック コントロール サンプルでを参照してください。 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Excel ソリューション](../vsto/excel-solutions.md)   
 [Windows フォームでコントロールの Office ドキュメントの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [ListObject コントロール](../vsto/listobject-control.md)  
  
  