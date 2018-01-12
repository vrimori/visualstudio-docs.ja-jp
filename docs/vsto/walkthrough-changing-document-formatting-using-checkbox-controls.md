---
title: "チュートリアル: CheckBox コントロールを使用したドキュメント書式の変更 |Microsoft ドキュメント"
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
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5b99f1a5d05d1eac173c40e7cc0c3b989f7c0cd3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-changing-document-formatting-using-checkbox-controls"></a>チュートリアル : CheckBox コントロールを使用したドキュメント書式の変更
  このチュートリアルでは、Microsoft Office Word のドキュメント レベルのカスタマイズでの Windows フォーム コントロールを使用して、テキストの書式設定を変更する方法を示します。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   デザイン時にドキュメント レベルのプロジェクトの文書にテキストとコントロールを追加します。  
  
-   オプションを選択すると、テキストの書式を設定します。  
  
 完成したサンプルの結果を参照してくださいで Word コントロールのサンプルを参照してください。 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)です。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初に、Word 文書のプロジェクトを作成します。  
  
#### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Word 文書プロジェクトを作成**My Word 書式**です。 ウィザードで、次のように選択します。**新しいドキュメントを作成する**です。  
  
     詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     デザイナーで新しい Word 文書を開き、 **My Word 書式**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-text-and-controls-to-the-word-document"></a>Word 文書にテキストとコントロールの追加  
 このチュートリアルでは、次の 3 つのチェック ボックスとテキストを追加、 <xref:Microsoft.Office.Tools.Word.Bookmark> Word 文書にコントロールできます。 チェック ボックス オプションが表示されます、ユーザーにテキストの書式設定します。  
  
#### <a name="to-add-three-check-boxes"></a>次の 3 つのチェック ボックスを追加するには  
  
1.  Visual Studio デザイナーで文書が開いていることを確認します。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**、最初にドラッグ<xref:Microsoft.Office.Tools.Word.Controls.CheckBox>コントロールをドキュメント。  
  
3.  **[プロパティ]** ウィンドウで、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**[テキスト]**|**太字**|  
  
4.  キーを押して**Enter**最初のチェック ボックスの下にカーソルを移動します。  
  
5.  次のドキュメントに 2 つ目のチェック ボックスを追加、`ApplyBoldFont`チェック ボックスをオンし、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**[テキスト]**|**斜体**|  
  
6.  キーを押して**Enter** 2 番目のチェック ボックスの下にカーソルを移動します。  
  
7.  3 番目のチェック ボックスを次のドキュメントに追加、`ApplyItalicFont`チェック ボックスをオンし、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**[テキスト]**|**下線**|  
  
#### <a name="to-add-text-and-a-bookmark-control"></a>テキストおよびブックマーク コントロールを追加するには  
  
1.  チェック ボックス コントロールの下にカーソルを移動し、次のテキストを入力します。  
  
     **このテキストの書式を変更する チェック ボックスをクリックします。**  
  
2.  **Word コントロール**のタブ、**ツールボックス**、ドラッグ、<xref:Microsoft.Office.Tools.Word.Bookmark>コントロールをドキュメント。  
  
     **ブックマーク コントロールの追加** ダイアログ ボックスが表示されます。  
  
3.  ドキュメントに追加するテキストを選択し、クリックして**OK**です。  
  
     A<xref:Microsoft.Office.Tools.Word.Bookmark>という名前のコントロール**Bookmark1**がドキュメントで選択したテキストに追加します。  
  
4.  **プロパティ** ウィンドウの値を変更、 **(名)**プロパティを**fontText です。**  
  
 次に、チェック ボックスをオンまたはオフのときにテキストの書式を設定するコードを記述します。  
  
## <a name="formatting-the-text-when-a-check-box-is-checked-or-cleared"></a>オンまたはオフには、テキストと、チェック ボックスを書式設定  
 ユーザーが書式設定オプションを選択すると、ドキュメント内のテキストの書式を変更します。  
  
#### <a name="to-change-formatting-when-a-check-box-is-selected"></a>チェック ボックスを書式設定を変更するのには、選択されています。  
  
1.  右クリック`ThisDocument`で**ソリューション エクスプ ローラー**、クリックして**コードの表示**ショートカット メニューの します。  
  
2.  C# の場合のみ、定数の追加、次に、 **ThisDocument**クラスです。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]  
  
3.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、`applyBoldFont`チェック ボックスをオンします。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]  
  
4.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、`applyItalicFont`チェック ボックスをオンします。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]  
  
5.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、`applyUnderlineFont`チェック ボックスをオンします。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]  
  
6.  C# の場合にあるテキスト ボックスのイベント ハンドラーを追加する必要があります、<xref:Microsoft.Office.Tools.Word.Document.Startup>イベント。 イベント ハンドラーを作成する方法については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 選択またはチェック ボックスをオフにするときに、テキストの書式が正しく設定することを確認する文書をテストできます。  
  
#### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  選択またはチェック ボックスをオフにします。  
  
3.  テキストの形式が正しいことを確認します。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、チェック ボックスを使用して、プログラムによって Word 文書で書式設定テキストの変更の基礎を説明します。 ここでは、次のタスクを行います。  
  
-   ボタンを使用して、テキスト ボックスに入力します。 詳細については、次を参照してください。[チュートリアル: ボタンを使用してドキュメント内のテキスト ボックスに表示するテキスト](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)です。  
  
-   オプション ボタンを使用してグラフのスタイルを選択する。 詳細については、次を参照してください。[チュートリアル: グラフを更新するラジオ ボタンを使用してドキュメントで](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)です。  
  
-  
  
## <a name="see-also"></a>参照  
 [チュートリアルを使用して Word](../vsto/walkthroughs-using-word.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [Office ドキュメントでの Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  