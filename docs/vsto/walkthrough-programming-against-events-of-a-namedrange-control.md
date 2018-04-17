---
title: 'チュートリアル: NamedRange コントロールのイベントのプログラミング |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 623177120d58b7abd29b57d55db22b8490057bab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-programming-against-events-of-a-namedrange-control"></a>チュートリアル : NamedRange コントロールのイベントのプログラミング
  このチュートリアルは、追加する方法を示します、 <xref:Microsoft.Office.Tools.Excel.NamedRange> Microsoft Office Excel ワークシートと Visual Studio での Office 開発ツールを使用して、そのイベントに対してプログラミングを制御します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   追加、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールをワークシートにします。  
  
-   に対するプログラミング<xref:Microsoft.Office.Tools.Excel.NamedRange>イベントを制御します。  
  
-   プロジェクトをテストします。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 このステップでは、Visual Studio を使用して Excel ブック プロジェクトを作成します。  
  
#### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Excel ブック プロジェクトを作成**マイという名前の範囲イベント**です。 確認して**新しいドキュメントを作成する**が選択されています。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     デザイナーで新しい Excel ブックを開き、**マイという名前の範囲イベント**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-text-and-named-ranges-to-the-worksheet"></a>テキストを追加して、名前付きのワークシートに範囲  
 ホスト コントロールは、Office オブジェクトを拡張は、追加する同じ方法で、文書は、ネイティブ オブジェクトを追加します。 たとえば、Excel を追加することができます<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールをワークシートに開くことによって、**挿入** メニューのをポイント**名前**を選択して**定義**です。 追加することも、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールからドラッグすることで、**ツールボックス**ワークシートにします。  
  
 この手順を使用してワークシートに 2 つの名前付き範囲コントロールを追加、**ツールボックス**、し、ワークシートにテキストを追加します。  
  
#### <a name="to-add-a-range-to-your-worksheet"></a>範囲のワークシートに追加するには  
  
1.  いることを確認、**マイ名前付き範囲 Events.xlsx** 、Visual Studio デザイナーで開いているブックで`Sheet1`が表示されます。  
  
2.  **Excel コントロール**ドラッグ、ツールボックスのタブ、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールをセル**A1**で`Sheet1`です。  
  
     **NamedRange コントロールの追加** ダイアログ ボックスが表示されます。  
  
3.  いることを確認**$A$ 1**の編集可能なテキスト ボックス、およびそのセルが表示されます**A1**が選択されています。 そうでない場合は、セルをクリックして**A1**をオンにします。  
  
4.  **[OK]**をクリックします。  
  
     セル**A1**という名前の範囲になります`namedRange1`です。 ワークシートに示されませんが、`namedRange1`に表示されます、**名前**(左側にあるワークシートのすぐ上にある) ボックス セル**A1**が選択されています。  
  
5.  もう 1 つ追加<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールをセル**B3**です。  
  
6.  いることを確認**$B$ 3**の編集可能なテキスト ボックス、およびそのセルが表示されます**B3**が選択されています。 そうでない場合は、セルをクリックして**B3**をオンにします。  
  
7.  **[OK]**をクリックします。  
  
     セル**B3**という名前の範囲になります`namedRange2`です。  
  
#### <a name="to-add-text-to-your-worksheet"></a>ワークシートにテキストを追加するには  
  
1.  セルに**A1**、次のテキストを入力します。  
  
     **これは、NamedRange コントロールの例です。**  
  
2.  セルに**A3** (の左側に`namedRange2`)、次のテキストを入力します。  
  
     **イベント:**  
  
 次のセクションにテキストを挿入するコードを記述します`namedRange2`のプロパティを変更し、`namedRange2`コントロールへの応答、 <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>、 <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>、および<xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>のイベント`namedRange1`です。  
  
## <a name="adding-code-to-respond-to-the-beforedoubleclick-event"></a>BeforeDoubleClick イベントに応答するコードを追加します。  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>BeforeDoubleClick イベントに基づいて NamedRange2 にテキストを挿入するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**Sheet1.vb**または**Sheet1.cs**選択**コードの表示**です。  
  
2.  コードを追加するため、`namedRange1_BeforeDoubleClick`イベント ハンドラーは、次のようになります。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  ように、C# の場合は、名前付き範囲のイベント ハンドラーを追加する必要があります、<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>以下のイベントです。 イベント ハンドラーを作成する方法については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## <a name="adding-code-to-respond-to-the-change-event"></a>変更イベントに応答するコードを追加します。  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>変更イベントに基づく namedRange2 にテキストを挿入するには  
  
1.  コードを追加するため、`NamedRange1_Change`イベント ハンドラーは、次のようになります。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  編集モードに入ると、Excel 範囲内でセルをダブルクリックするので、<xref:Microsoft.Office.Tools.Excel.NamedRange.Change>イベント テキストの変更が発生していない場合でも、選択範囲が、範囲外に移動するときに発生します。  
  
## <a name="adding-code-to-respond-to-the-selectionchange-event"></a>SelectionChange イベントに応答するコードを追加します。  
  
#### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>SelectionChange イベントに基づいて namedRange2 にテキストを挿入するには  
  
1.  コードを追加するため、 **NamedRange1_SelectionChange**イベント ハンドラーは、次のようになります。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  原因 Excel の範囲内のセルをダブルクリックすると、選択範囲に移動する、<xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>イベントが発生する前に、<xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>イベントが発生します。  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 これで、そのテキストのイベントを表すことを確認するブックをテストすることができます、<xref:Microsoft.Office.Tools.Excel.NamedRange>イベントが発生したときにコントロールが別の名前付き範囲に挿入します。  
  
#### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  カーソルを置く`namedRange1`、いることを確認し、テキストに関する、<xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>イベントが挿入され、ワークシートにコメントを挿入します。  
  
3.  内をダブルクリック`namedRange1`、いることを確認し、テキストに関する<xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>に赤い斜体のテキストを含むイベントを挿入`namedRange2`です。  
  
4.  外側をクリックして`namedRange1`と変更イベントが終了するときに発生する編集モードの場合でも、テキストに変更されませんでした。  
  
5.  内のテキストを変更する`namedRange1`です。  
  
6.  外側をクリックして`namedRange1`、ことを確認し、テキストに関する<xref:Microsoft.Office.Tools.Excel.NamedRange.Change>に青のテキストを含むイベントを挿入`namedRange2`です。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでのイベントに対するプログラミングの基礎、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロール。 次のタスクを次に示します。  
  
-   プロジェクトを配置します。 詳細については、次を参照してください。 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [方法: NamedRange コントロールのサイズを変更します。](../vsto/how-to-resize-namedrange-controls.md)   
 [方法: ワークシートに NamedRange コントロールを追加します。](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  