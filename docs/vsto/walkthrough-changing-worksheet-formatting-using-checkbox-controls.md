---
title: "チュートリアル: CheckBox コントロールを使用してワークシートの書式設定の変更 |Microsoft ドキュメント"
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
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f10b0ed77dc9d5f97b6fc2fc4f218c86dafee41
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-changing-worksheet-formatting-using-checkbox-controls"></a>チュートリアル : CheckBox コントロールを使用したワークシート書式の変更
  このチュートリアルでは、Microsoft Office Excel ワークシートの書式を変更する チェック ボックスを使用する基礎を説明します。 Visual Studio での Office 開発ツールを使用して、作成し、プロジェクトにコードが追加されます。 完成したサンプルの結果を参照してくださいで Excel コントロールのサンプルを参照してください。 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)です。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   テキストとコントロールをワークシートに追加します。  
  
-   オプションを選択するとテキストの書式を設定します。  
  
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
  
1.  名前の Excel ブック プロジェクトを作成**個人用の Excel の書式**です。 確認して**新しいドキュメントを作成する**が選択されています。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     デザイナーで新しい Excel ブックを開き、**個人用の Excel の書式**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-text-and-controls-to-the-worksheet"></a>テキストとコントロールをワークシートに追加します。  
 このチュートリアルでは、必要があります 3<xref:Microsoft.Office.Tools.Excel.Controls.CheckBox>コントロールとテキストを<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロール。  
  
#### <a name="to-add-three-check-boxes"></a>次の 3 つのチェック ボックスを追加するには  
  
1.  ブックが、Visual Studio デザイナーで開かれていることを確認`Sheet1`が開かれています。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**、ドラッグ、<xref:Microsoft.Office.Tools.Excel.Controls.CheckBox>コントロールまたはセルの近くに**B2**で**Sheet1**です。  
  
3.  **ビュー**メニューの **プロパティ**ウィンドウです。  
  
4.  あることを確認**Checkbox1**のオブジェクト名 ボックスの一覧ボックスが表示されて、**プロパティ**ウィンドウで、次のプロパティを変更。  
  
    |プロパティ|値|  
    |--------------|-----------|  
    |**名前**|**applyBoldFont**|  
    |**[テキスト]**|**太字**|  
  
5.  2 番目のチェック ボックスを上または近くのセルにドラッグ**B4**し、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |--------------|-----------|  
    |**名前**|**applyItalicFont**|  
    |**[テキスト]**|**斜体**|  
  
6.  3 番目のチェック ボックスを上または近くのセルにドラッグ**B6**し、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |--------------|-----------|  
    |**名前**|**applyUnderlineFont**|  
    |**[テキスト]**|**下線**|  
  
7.  CTRL キーを押しながら、すべての 3 つのチェック ボックス コントロールを選択します。  
  
8.  Excel で 書式 タブの配置 をクリックして**Align**、クリックして**左揃え**です。  
  
     次の 3 つのチェック ボックス コントロールは、左側にある、選択した最初のコントロールの位置にアラインします。  
  
     次に、ドラッグするが、<xref:Microsoft.Office.Tools.Excel.NamedRange>ワークシートにコントロールです。  
  
    > [!NOTE]  
    >  追加することも、 <xref:Microsoft.Office.Tools.Excel.NamedRange> 」と入力してコントロール**ボックス**に、**名前**ボックス。  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>NamedRange コントロールにテキストを追加するには  
  
1.  **Excel コントロール**ドラッグ、ツールボックスのタブ、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールをセル**B9**です。  
  
2.  いることを確認**$B 9 ドル**の編集可能なテキスト ボックス、およびそのセルが表示されます**B9**が選択されています。 そうでない場合は、セルをクリックして**B9**をオンにします。  
  
3.  **[OK]** をクリックします。  
  
4.  セル**B9**という名前の範囲になります`NamedRange1`です。  
  
     ワークシートに示されませんが、`NamedRange1`に表示されます、**名 ボックス**(ワークシートの真上左側に) セル**B9**が選択されています。  
  
5.  あることを確認**NamedRange1**のオブジェクト名 ボックスの一覧ボックスが表示されて、**プロパティ**ウィンドウで、次のプロパティを変更。  
  
    |プロパティ|値|  
    |--------------|-----------|  
    |**名前**|**ボックス**|  
    |**Value2**|**このテキストの書式を変更する チェック ボックスをクリックします。**|  
  
 次に、オプションを選択するとテキストの書式を設定するコードを記述します。  
  
## <a name="formatting-the-text-when-an-option-is-selected"></a>書式設定テキストと、オプションが選択されています。  
 このセクションでは、ユーザーは、書式設定オプションを選択すると、ワークシート内のテキストの形式が変更できるようにコードを記述します。  
  
#### <a name="to-change-formatting-when-a-check-box-is-selected"></a>チェック ボックスを書式設定を変更するのには、選択されています。  
  
1.  右クリック**Sheet1**、クリックして**コードの表示**ショートカット メニューの します。  
  
2.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、 `applyBoldFont`  チェック ボックス。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、 `applyItalicFont`  チェック ボックス。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、 `applyUnderlineFont`  チェック ボックス。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  C# の場合は、チェック ボックスのイベント ハンドラーを追加する必要があります、<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>イベント次のようにします。 イベント ハンドラーを作成する方法については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 選択またはチェック ボックスをオフにするときに、テキストの書式が正しく設定するかどうかを確認するブックをテストできます。  
  
#### <a name="to-test-your-workbook"></a>ブックをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  選択またはチェック ボックスをオフにします。  
  
3.  テキストの形式が正しいことを確認します。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、チェック ボックスを使用して、Excel ワークシート上のテキストを書式設定の基本を使用します。 ここでは、次の作業を行います。  
  
-   プロジェクトを配置します。 詳細については、次を参照してください。 [ClickOnce を使用して Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)です。  
  
-   ボタンを使用してテキスト ボックスへデータを挿入する。 詳細については、次を参照してください。[チュートリアル: ボタンを使用してワークシート内のテキスト ボックスに表示するテキスト](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)です。  
  
## <a name="see-also"></a>関連項目  
 [使用して Excel のチュートリアル](../vsto/walkthroughs-using-excel.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [Office ドキュメントでの Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  