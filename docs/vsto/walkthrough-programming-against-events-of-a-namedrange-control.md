---
title: 'チュートリアル: NamedRange コントロールのイベントのプログラム'
ms.date: 02/02/2017
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
ms.openlocfilehash: 020d10aec83cd9249378c326f02ba37c3721b126
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910819"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>チュートリアル: NamedRange コントロールのイベントのプログラム
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
  
## <a name="create-the-project"></a>プロジェクトの作成  
 この手順では、Visual Studio を使用して Excel ブック プロジェクトを作成します。  
  
### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Excel ブック プロジェクトを作成する**マイという名前の範囲イベント**します。 必ず**新しい文書を作成**が選択されています。 詳細については、「[方法 :Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
     デザイナーで新しい Excel ブックを開き、**マイという名前の範囲イベント**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
## <a name="add-text-and-named-ranges-to-the-worksheet"></a>テキストを追加し、名前付き範囲をワークシート  
 ホスト コントロールでは、Office オブジェクトに拡張するため、追加すると同じように、ドキュメントには、ネイティブ オブジェクトを追加します。 たとえば、Excel を追加することができます<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールをワークシートに開くことで、**挿入** メニューのをポイント**名前**を選択して**定義**します。 追加することも、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールからドラッグすることで、**ツールボックス**ワークシートにします。  
  
 この手順を使用してワークシートに 2 つの名前付き範囲コントロールを追加します、**ツールボックス**、し、ワークシートにテキストを追加します。  
  
### <a name="to-add-a-range-to-your-worksheet"></a>ワークシートに範囲を追加するには  
  
1.  いることを確認、*マイ名前付き範囲 Events.xlsx* 、Visual Studio デザイナーで開いているブックで`Sheet1`が表示されます。  
  
2.  **Excel コントロール**、ツールボックスのタブ、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールをセル**A1**で`Sheet1`します。  
  
     **NamedRange コントロールの追加** ダイアログ ボックスが表示されます。  
  
3.  いることを確認 **$A$ 1**編集可能なテキスト ボックスに、そのセルに表示される**A1**が選択されています。 そうでない場合は、セルをクリックします。 **A1**をオンにします。  
  
4.  **[OK]** をクリックします。  
  
     セル**A1**という名前の範囲になります`namedRange1`します。 ワークシートの表示を示す値はありませんが、`namedRange1`に表示されます、**名前**ボックス (左側にあるワークシートの真上にあります) セル**A1**が選択されています。  
  
5.  もう 1 つ追加<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールをセル**B3**します。  
  
6.  いることを確認 **$B$ 3**編集可能なテキスト ボックスに、そのセルに表示される**B3**が選択されています。 そうでない場合は、セルをクリックします。 **B3**をオンにします。  
  
7.  **[OK]** をクリックします。  
  
     セル**B3**という名前の範囲になります`namedRange2`します。  
  
### <a name="to-add-text-to-your-worksheet"></a>ワークシートにテキストを追加するには  
  
1. セルに**A1**、次のテキストを入力します。  
  
    **これは、NamedRange コントロールの例です。**  
  
2. セルに**A3** (の左側に`namedRange2`)、次のテキストを入力します。  
  
    **イベント:**  
  
   テキストを挿入するコードを記述する次のセクションで`namedRange2`のプロパティを変更し、`namedRange2`コントロールへの応答、 <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>、 <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>、および<xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>のイベント`namedRange1`します。  
  
## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>BeforeDoubleClick イベントに応答するコードを追加します。  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>BeforeDoubleClick イベントに基づいて NamedRange2 にテキストを挿入するには  
  
1.  **ソリューション エクスプ ローラー**、右クリック**Sheet1.vb**または**Sheet1.cs**選択と**コードの表示**します。  
  
2.  コードを追加するため、`namedRange1_BeforeDoubleClick`イベント ハンドラーは、次のようにします。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  C# でのように、名前付き範囲のイベント ハンドラーを追加する必要があります、<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>イベント。 イベント ハンドラーの作成方法の詳細については、次を参照してください。[方法。Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## <a name="add-code-to-respond-to-the-change-event"></a>変更イベントに応答するコードを追加します。  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>変更イベントに基づく namedRange2 にテキストを挿入するには  
  
1.  コードを追加するため、`NamedRange1_Change`イベント ハンドラーは、次のようにします。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  編集モードでは、Excel の範囲内のセルをダブルクリックすると入力したため、<xref:Microsoft.Office.Tools.Excel.NamedRange.Change>イベント テキストに変更が発生していない場合でも、選択範囲が範囲外で移動するときに発生します。  
  
## <a name="add-code-to-respond-to-the-selectionchange-event"></a>SelectionChange イベントに応答するコードを追加します。  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>SelectionChange イベントに基づいて namedRange2 にテキストを挿入するには  
  
1.  コードを追加するため、 **NamedRange1_SelectionChange**イベント ハンドラーは、次のようにします。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Excel の範囲内のセルをダブルクリックすると、範囲に移動が発生するため、<xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>イベントが発生する前に、<xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>イベントが発生します。  
  
## <a name="test-the-application"></a>アプリケーションをテストする  
 イベントを表すテキストを確認するブックをテストして、<xref:Microsoft.Office.Tools.Excel.NamedRange>イベントが発生したときに、コントロールが別の名前付き範囲に挿入されます。  
  
### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  キーを押して**F5**プロジェクトを実行します。  
  
2.  カーソルを置く`namedRange1`、いることを確認し、テキストに関する、<xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>イベントが挿入されると、ワークシートにコメントを挿入します。  
  
3.  内でダブルクリック`namedRange1`、ことを確認しますテキストに関する<xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>の赤色の斜体テキストと共にイベントが挿入されます`namedRange2`します。  
  
4.  外側をクリックして`namedRange1`テキストに変更が加えられなかった場合でも、編集モードの変更イベントが終了するときに発生する注意してください。  
  
5.  内のテキストを変更する`namedRange1`します。  
  
6.  外側をクリックして`namedRange1`、いることを確認し、テキストに関する<xref:Microsoft.Office.Tools.Excel.NamedRange.Change>に青色のテキストと共にイベントが挿入されます`namedRange2`します。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでのイベントのプログラミングの基礎を<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロール。 次のタスクを次に示します。  
  
-   プロジェクトを配置します。 詳細については、次を参照してください。 [Office ソリューションを配置](../vsto/deploying-an-office-solution.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [拡張オブジェクトを使用して Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [方法: NamedRange コントロールをサイズ変更します。](../vsto/how-to-resize-namedrange-controls.md)   
 [方法: ワークシートに NamedRange コントロールを追加します。](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [方法: Office プロジェクトでのイベント ハンドラーを作成します。](../vsto/how-to-create-event-handlers-in-office-projects.md)  
