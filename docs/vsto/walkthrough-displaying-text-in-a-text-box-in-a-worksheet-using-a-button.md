---
title: 'チュートリアル: ボタンを使用してワークシート内のテキスト ボックスにテキストを表示する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e141618fb5b647f0cdb5341627356588df932fed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button"></a>チュートリアル : ボタンを使用してワークシート内テキスト ボックスにテキストを表示する方法
  このチュートリアルでは、ボタンやテキスト ボックスを使用して、Microsoft Office Excel ワークシート、および Visual Studio での Office 開発ツールを使用する Excel プロジェクトを作成する方法についての基本を使用します。 完成したサンプルの結果を参照してくださいで Excel コントロールのサンプルを参照してください。 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)です。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   コントロールをワークシートに追加します。  
  
-   テキスト ボックスは、ボタンがクリックされたときに入力します。  
  
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
  
1.  名前の Excel ブック プロジェクトを作成**マイ Excel ボタン**です。 確認して**新しいドキュメントを作成する**が選択されています。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     デザイナーで新しい Excel ブックを開き、**マイ Excel ボタン**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-controls-to-the-worksheet"></a>ワークシートへのコントロールの追加  
 このチュートリアルでは、ボタンと最初のワークシートにテキスト ボックスを必要があります。  
  
#### <a name="to-add-a-button-and-a-text-box"></a>ボタンとテキスト ボックスを追加するには  
  
1.  いることを確認、**マイ Excel Button.xlsx** 、Visual Studio デザイナーで開いているブックで`Sheet1`が表示されます。  
  
2.  **コモン コントロール**ドラッグ、ツールボックスのタブ、<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>に`Sheet1`です。  
  
3.  **ビュー**メニューの [**プロパティ] ウィンドウ**します。  
  
4.  あることを確認**TextBox1**に表示されて、**プロパティ**ウィンドウのドロップダウン ボックスと変更、**名前**にテキスト ボックスのプロパティ**displayText**.  
  
5.  ドラッグ、**ボタン**コントロールを`Sheet1`し、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**insertText**|  
    |**[テキスト]**|**テキストを挿入します。**|  
  
 ボタンがクリックされたときに実行するコードを記述します。  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>ボタンがクリックされたときに、テキスト ボックスの設定  
 ユーザーは、ボタンをクリックするたびに**Hello World!** テキスト ボックスに追加されます。  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>ボタンがクリックされたときにテキスト ボックスに書き込むには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**Sheet1**、クリックして**コードの表示**ショートカット メニューの します。  
  
2.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>ボタンのイベント ハンドラー。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  C# の場合は、イベント ハンドラーを追加する必要があります、<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>イベント次のようにします。 イベント ハンドラーを作成する方法については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 確認するブックをテストして、メッセージ**Hello World!** ボタンをクリックしたときに、テキスト ボックスに表示されます。  
  
#### <a name="to-test-your-workbook"></a>ブックをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  ボタンをクリックします。  
  
3.  いることを確認**Hello World!** テキスト ボックスに表示されます。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、Excel ワークシートでボタンやテキスト ボックスの基本的な使い方を示します。 ここでは、次のタスクを行います。  
  
-   プロジェクトを配置します。 詳細については、次を参照してください。 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)です。  
  
-   書式を変更するのにには、チェック ボックスを使用します。 詳細については、次を参照してください。[チュートリアル: 変更ワークシートの書式設定 チェック ボックス コントロールを使用した](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: Windows フォーム コントロールの Office ドキュメントへの追加](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [使用して Excel のチュートリアル](../vsto/walkthroughs-using-excel.md)   
 [Office ドキュメントでの Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  