---
title: 'チュートリアル: CheckBox コントロールを使用したドキュメント書式を変更します。'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6e33d7b683e55f570961d9f9f8f77ea1491db3f5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913870"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>チュートリアル: CheckBox コントロールを使用したドキュメント書式を変更します。
  このチュートリアルでは、Microsoft Office Word のドキュメント レベルのカスタマイズでの Windows フォーム コントロールを使用して、テキストの書式設定を変更する方法を示します。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
- デザイン時にドキュメント レベルのプロジェクトの文書にテキストとコントロールを追加します。  
  
- オプションを選択すると、テキストの書式を設定します。  
  
  完成したサンプルとして結果を参照してくださいで Word コントロールのサンプルを参照してください。 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)します。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## <a name="create-the-project"></a>プロジェクトの作成  
 最初に、Word 文書のプロジェクトを作成します。  
  
### <a name="create-a-new-project"></a>新しいプロジェクトを作成する  
  
1.  名前の Word 文書プロジェクトを作成**My Word の書式設定**します。 ウィザードで、次のように選択します。**新しい文書を作成**です。  
  
     詳細については、「[方法 :Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
     デザイナーで新しい Word 文書を開き、 **My Word の書式設定**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
## <a name="add-text-and-controls-to-the-word-document"></a>Word 文書にテキストとコントロールを追加します。  
 このチュートリアルでは、次の 3 つのチェック ボックスと任意のテキストを追加、 <xref:Microsoft.Office.Tools.Word.Bookmark> Word 文書にコントロール。 チェック ボックスは、オプションをテキストの書式設定、ユーザーに表示されます。  
  
### <a name="add-three-check-boxes"></a>次の 3 つのチェック ボックスを追加します。  
  
1.  Visual Studio デザイナーで文書が開いていることを確認します。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**、1 つ目のドラッグ<xref:Microsoft.Office.Tools.Word.Controls.CheckBox>コントロールをドキュメント。  
  
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
  
6.  キーを押して**Enter** 2 つ目のチェック ボックスの下にカーソルを移動します。  
  
7.  以下の説明に 3 つ目のチェック ボックスを追加、`ApplyItalicFont`チェック ボックスをオンし、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**[テキスト]**|**下線**|  
  
### <a name="add-text-and-a-bookmark-control"></a>テキストおよびブックマーク コントロールを追加します。  
  
1. チェック ボックス コントロールの下にカーソルを移動し、次のテキストを入力します。  
  
    **このテキストの書式を変更する チェック ボックスをクリックします。**  
  
2. **Word コントロール**のタブ、**ツールボックス**、ドラッグ、<xref:Microsoft.Office.Tools.Word.Bookmark>コントロールをドキュメント。  
  
    **ブックマーク コントロールの追加** ダイアログ ボックスが表示されます。  
  
3. ドキュメントに追加するテキストを選択し、クリックして**OK**します。  
  
    A<xref:Microsoft.Office.Tools.Word.Bookmark>という名前のコントロール**Bookmark1**ドキュメントで選択したテキストに追加されます。  
  
4. **プロパティ** ウィンドウの値を変更、 **(名)** プロパティを**fontText します。**  
  
   次に、チェック ボックスをオンまたはオフのときに、テキストの書式設定コードを記述します。  
  
## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>チェック ボックスをオンまたはオフのときに、テキストの書式設定します。  
 ユーザーが、書式設定オプションを選択すると、ドキュメント内のテキストの書式を変更します。  
  
### <a name="change-formatting-when-a-check-box-is-selected"></a>チェック ボックスが選択されているときに書式設定を変更します。  
  
1.  右クリック`ThisDocument`で**ソリューション エクスプ ローラー**、] をクリックし、**コードの表示**ショートカット メニューの [します。  
  
2.  C# のみの場合に、次の定数を追加、 **ThisDocument**クラス。  
  
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
  
6.  C# でにあるテキスト ボックスのイベント ハンドラーを追加する必要があります、<xref:Microsoft.Office.Tools.Word.Document.Startup>イベント。 イベント ハンドラーを作成する方法については、次を参照してください。[方法。Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]  
  
## <a name="test-the-application"></a>アプリケーションをテストする  
 選択またはチェック ボックスをオフにするときに、テキストの書式が正しく設定することを確認するドキュメントをテストできます。  
  
### <a name="test-your-document"></a>ドキュメントをテストします。  
  
1.  キーを押して**F5**プロジェクトを実行します。  
  
2.  選択するか、チェック ボックスをオフにします。  
  
3.  テキストの形式が正しいことを確認します。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、チェック ボックスを使用して、プログラムによって Word 文書の書式設定テキストの変更の基礎を説明します。 ここでは、次のタスクを行います。  
  
-   ボタンを使用して、テキスト ボックスに入力します。 詳細については、「[チュートリアル:ボタンを使用して、ドキュメント内のテキスト ボックスにテキストを表示](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)します。  
  
-   オプション ボタンを使用してグラフのスタイルを選択する。 詳細については、「[チュートリアル:ラジオ ボタンを使用してドキュメントのグラフを更新](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)します。  
  

## <a name="see-also"></a>関連項目  
 [Word を使用したチュートリアル](../vsto/walkthroughs-using-word.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange コントロール](../vsto/namedrange-control.md)   
 [Office ドキュメントに Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
