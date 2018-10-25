---
title: 'チュートリアル: ボタンを使用してワークシート内のテキスト ボックスでテキストを表示します。'
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
ms.openlocfilehash: 25294e9cb8f57036603ec4817fcbd59976a358a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840286"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>チュートリアル: ボタンを使用してワークシート内のテキスト ボックスでテキストを表示します。
  このチュートリアルでは、ボタンやテキスト ボックスを使用して、Microsoft Office Excel ワークシート、および Visual Studio での Office 開発ツールを使用して Excel プロジェクトを作成する方法の基本を説明します。 完成したサンプルとして結果を参照してくださいにある Excel コントロールのサンプルを参照してください。 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)します。  
  
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
  
## <a name="create-the-project"></a>プロジェクトの作成  
 この手順では、Visual Studio を使用して Excel ブック プロジェクトを作成します。  
  
### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Excel ブック プロジェクトを作成する**マイ Excel ボタン**します。 必ず**新しい文書を作成**が選択されています。 詳細については、次の[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)を参照してください。  
  
     デザイナーで新しい Excel ブックを開き、**マイ Excel ボタン**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
## <a name="add-controls-to-the-worksheet"></a>ワークシートにコントロールを追加します。  
 このチュートリアルでは、ボタンと最初のワークシートにテキスト ボックスを必要があります。  
  
### <a name="to-add-a-button-and-a-text-box"></a>ボタンとテキスト ボックスを追加するには  
  
1. いることを確認、**マイ Excel Button.xlsx** 、Visual Studio デザイナーで開いているブックで`Sheet1`が表示されます。  
  
2. **コモン コントロール**、ツールボックスのタブ、<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>に`Sheet1`します。  
  
3. **ビュー**メニューの [**プロパティ] ウィンドウ**します。  
  
4. 確認します**TextBox1**に表示されて、**プロパティ**ウィンドウのドロップダウン リスト ボックスと変更、**名前**にテキスト ボックスのプロパティ**displayText**.  
  
5. ドラッグ、**ボタン**コントロールを`Sheet1`し、次のプロパティを変更します。  
  
   |プロパティ|[値]|  
   |--------------|-----------|  
   |**Name**|**insertText**|  
   |**[テキスト]**|**テキストを挿入します。**|  
  
   ボタンがクリックされたときに実行するコードを記述するようになりました。  
  
## <a name="populate-the-text-box-when-the-button-is-clicked"></a>ボタンがクリックされたときに、テキスト ボックスを設定します。  
 ユーザーが、ボタンをクリックするたびに**Hello World!** テキスト ボックスに追加されます。  
  
### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>ボタンがクリックされたときにテキスト ボックスに書き込むには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**Sheet1**、] をクリックし、**コードの表示**ショートカット メニューの [します。  
  
2.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>ボタンのイベント ハンドラー。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  C# でイベント ハンドラーを追加する必要があります、<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>次に示すようにイベント。 イベント ハンドラーの作成方法の詳細については、次を参照してください。[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="test-the-application"></a>アプリケーションをテストする  
 確認するブックをテスト メッセージ**Hello World!** ボタンをクリックすると、テキスト ボックスに表示されます。  
  
### <a name="to-test-your-workbook"></a>ブックをテストするには  
  
1.  キーを押して**F5**プロジェクトを実行します。  
  
2.  ボタンをクリックします。  
  
3.  確認します**Hello World!** テキスト ボックスに表示されます。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、Excel ワークシートでボタンやテキスト ボックスを使用するの基本を説明します。 ここでは、次のタスクを行います。  
  
-   プロジェクトを配置します。 詳細については、次を参照してください。 [Office ソリューションを配置](../vsto/deploying-an-office-solution.md)します。  
  
-   書式を変更するのにには、チェック ボックスを使用します。 詳細については、次を参照してください。[チュートリアル: CheckBox コントロールを使用して書式設定の変更ワークシート](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)します。  
  
## <a name="see-also"></a>関連項目  
 [方法: Windows フォーム コントロールを Office ドキュメントに追加します。](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Excel を使用したチュートリアル](../vsto/walkthroughs-using-excel.md)   
 [Office ドキュメントに Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  