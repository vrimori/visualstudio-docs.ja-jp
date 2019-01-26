---
title: 'チュートリアル: CheckBox コントロールを使用してワークシートの書式設定を変更します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 30e89adf2d93e67a63071f79ded213a3dcff6385
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871027"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>チュートリアル: CheckBox コントロールを使用してワークシートの書式設定を変更します。
  このチュートリアルでは、Microsoft Office Excel ワークシートの書式を変更するチェック ボックスの使用の基本を説明します。 Visual Studio での Office 開発ツールを使用して作成し、プロジェクトにコードを追加するは。 完成したサンプルとして結果を参照してくださいにある Excel コントロールのサンプルを参照してください。 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   テキストとコントロールをワークシートに追加します。  
  
-   オプションを選択すると、テキストの書式を設定します。  
  
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
  
1.  名前の Excel ブック プロジェクトを作成する**マイ Excel の書式**します。 必ず**新しい文書を作成**が選択されています。 詳細については、「[方法 :Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
     デザイナーで新しい Excel ブックを開き、**マイ Excel の書式**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
## <a name="add-text-and-controls-to-the-worksheet"></a>テキストとコントロールをワークシートに追加します。  
 このチュートリアルでは、必要があります。 3 つ<xref:Microsoft.Office.Tools.Excel.Controls.CheckBox>コントロールと任意のテキストを、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロール。  
  
### <a name="to-add-three-check-boxes"></a>次の 3 つのチェック ボックスを追加するには  
  
1.  ブックが、Visual Studio デザイナーで開いていることを確認`Sheet1`が開いています。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**、ドラッグ、<xref:Microsoft.Office.Tools.Excel.Controls.CheckBox>コントロールまたはセルの近くに**B2**で**Sheet1**します。  
  
3.  **ビュー**メニューの **プロパティ**ウィンドウ。  
  
4.  確認します**Checkbox1**のオブジェクト名のリスト ボックスに表示されて、**プロパティ**ウィンドウで、次のプロパティを変更。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**Text**|**太字**|  
  
5.  上またはセルの近くに 2 つ目のチェック ボックスをドラッグして**B4**し、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**Text**|**斜体**|  
  
6.  上またはセルの近くに 3 つ目のチェック ボックスをドラッグして**B6**し、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**Text**|**下線**|  
  
7.  保留中のすべての 3 つのチェック ボックス コントロールを選択して、 **Ctrl**キー。  
  
8.  Excel で 書式 タブの 配置グループの  **Align**、 をクリックし、**左揃え**します。  
  
     次の 3 つのチェック ボックス コントロールは、左側にある、選択した最初のコントロールの位置に配置されます。  
  
     次に、ドラッグするが、<xref:Microsoft.Office.Tools.Excel.NamedRange>ワークシートにコントロール。  
  
    > [!NOTE]  
    >  追加することも、 <xref:Microsoft.Office.Tools.Excel.NamedRange> 」と入力してコントロール**ボックス**に、**名前**ボックス。  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>NamedRange コントロールにテキストを追加するには  
  
1. **Excel コントロール**、ツールボックスのタブ、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールをセル**B9**します。  
  
2. いることを確認 **$B 9 ドル**編集可能なテキスト ボックスに、そのセルに表示される**B9**が選択されています。 そうでない場合は、セルをクリックします。 **B9**をオンにします。  
  
3. **[OK]** をクリックします。  
  
4. セル**B9**という名前の範囲になります`NamedRange1`します。  
  
    ワークシートの表示を示す値はありませんが、`NamedRange1`に表示されます、**名 ボックスに**(ワークシートの真上左側にある) セル**B9**が選択されています。  
  
5. 確認します**NamedRange1**のオブジェクト名のリスト ボックスに表示されて、**プロパティ**ウィンドウで、次のプロパティを変更。  
  
   |プロパティ|[値]|  
   |--------------|-----------|  
   |**Name**|**textFont**|  
   |**Value2**|**このテキストの書式を変更する チェック ボックスをクリックします。**|  
  
   次に、オプションを選択すると、テキストの書式設定コードを記述します。  
  
## <a name="format-the-text-when-an-option-is-selected"></a>オプションを選択すると、テキストの書式設定します。  
 このセクションでは、ユーザーは、書式設定オプションを選択すると、ワークシート内のテキストの形式が変更できるようにコードを記述します。  
  
### <a name="to-change-formatting-when-a-check-box-is-selected"></a>チェック ボックスの書式を変更するには、が選択されています。  
  
1.  右クリック**Sheet1**、] をクリックし、**コードの表示**ショートカット メニューの [します。  
  
2.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、 `applyBoldFont`  チェック ボックス。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、 `applyItalicFont`  チェック ボックス。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、 `applyUnderlineFont`  チェック ボックス。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  C# でにあるチェック ボックスのイベント ハンドラーを追加する必要があります、<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>次に示すようにイベント。 イベント ハンドラーの作成方法の詳細については、次を参照してください。[方法。Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="test-the-application"></a>アプリケーションをテストする  
 選択またはチェック ボックスをオフにするときに、テキストの書式が正しく設定するかどうかを確認するブックをテストできます。  
  
### <a name="to-test-your-workbook"></a>ブックをテストするには  
  
1.  キーを押して**F5**プロジェクトを実行します。  
  
2.  選択するか、チェック ボックスをオフにします。  
  
3.  テキストの形式が正しいことを確認します。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、チェック ボックスを使用して、Excel ワークシート上でテキストの書式設定の基本を説明します。 ここでは、次のタスクを行います。  
  
-   プロジェクトを配置します。 詳細については、次を参照してください。 [ClickOnce を使用して Office ソリューションを配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)します。  
-   ボタンを使用してテキスト ボックスへデータを挿入する。 詳細については、「[チュートリアル:ボタンを使用してワークシート内のテキスト ボックスにテキストを表示](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Excel を使用したチュートリアル](../vsto/walkthroughs-using-excel.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [Office ドキュメントに Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
