---
title: 'チュートリアル: ボタンを使用して文書内のテキスト ボックスにテキストを表示'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 188fc5d954bb41ced952e48874816bdfd503765b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910140"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>チュートリアル: ボタンを使用して文書内のテキスト ボックスにテキストを表示
  このチュートリアルでは、Microsoft Office Word のドキュメント レベルのカスタマイズでボタンやテキスト ボックスを使用する方法を示します。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
- デザイン時にドキュメント レベルのプロジェクトで Word 文書にコントロールを追加する。  
  
- ボタンがクリックされたときにテキスト ボックスにデータを読み込む。  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>プロジェクトの作成  
 最初に、Word 文書のプロジェクトを作成します。  
  
### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Word 文書プロジェクトを作成**My Word Button**します。 ウィザードで、次のように選択します。**新しい文書を作成**です。  
  
     詳細については、「[方法 :Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
     デザイナーで新しい Word 文書を開き、 **My Word Button**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
## <a name="add-controls-to-the-word-document"></a>Word 文書にコントロールを追加します。  
 ユーザー インターフェイス コントロールは、Word 文書上のボタンとテキスト ボックスで構成されます。  
  
### <a name="to-add-a-button-and-a-text-box"></a>ボタンとテキスト ボックスを追加するには  
  
1. Visual Studio デザイナーで文書が開いていることを確認します。  
  
2. **コモン コントロール**のタブ、**ツールボックス**、ドラッグ、<xref:Microsoft.Office.Tools.Word.Controls.TextBox>コントロールをドキュメント。  
  
   > [!NOTE]  
   >  Word の既定では、コントロールはテキスト中にインラインでドロップされます。 制御する方法を変更して、図形オブジェクトの挿入の既定値を変更することで、**編集**のタブ、**オプション**Word のダイアログ ボックス。  
  
3. **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックします。  
  
4. 検索**TextBox1**で、**プロパティ**ウィンドウのドロップダウン リスト ボックスと変更、**名前**にテキスト ボックスのプロパティ**displayText**します。  
  
5. ドラッグ、**ボタン**ドキュメントに制御し、次のプロパティを変更します。  
  
   |プロパティ|[値]|  
   |--------------|-----------|  
   |**Name**|**insertText**|  
   |**[テキスト]**|**テキストを挿入します。**|  
  
   これで、ボタンがクリックされたときに実行されるコードを記述できるようになりました。  
  
## <a name="populate-the-text-box-when-the-button-is-clicked"></a>ボタンがクリックされたときに、テキスト ボックスを設定します。  
 ユーザーが、ボタンをクリックするたびに**Hello World!** テキスト ボックスに追加されます。  
  
### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>ボタンがクリックされたときにテキスト ボックスに書き込むには  
  
1.  **ソリューション エクスプ ローラー**、右クリックして**ThisDocument**、順にクリックします**コードの表示**ショートカット メニューの します。  
  
2.  ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]  
  
3.  C# では、ボタンのイベント ハンドラーを <xref:Microsoft.Office.Tools.Word.Document.Startup> イベントに追加する必要があります。 イベント ハンドラーの作成方法の詳細については、次を参照してください。[方法。Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)します。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]  
  
## <a name="test-the-application"></a>アプリケーションをテストする  
 確認する、文書をテストするメッセージ**Hello World!** ボタンをクリックすると、テキスト ボックスに表示されます。  
  
### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  キーを押して**F5**プロジェクトを実行します。  
  
2.  ボタンをクリックします。  
  
3.  確認します**Hello World!** テキスト ボックスに表示されます。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、Word 文書でボタンとテキスト ボックスを使用する際の基本事項について説明しました。 ここでは、次のタスクを行います。  
  
-   コンボ ボックスを使用して書式設定を変更する。 詳細については、「[チュートリアル:CheckBox コントロールを使用して書式設定の変更ドキュメント](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)します。  
  
-   オプション ボタンを使用してグラフのスタイルを選択する。 詳細については、「[チュートリアル:ラジオ ボタンを使用してドキュメントのグラフを更新](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Office ドキュメントの概要での Windows フォーム コントロール](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Word を使用したチュートリアル](../vsto/walkthroughs-using-word.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [方法: Office ドキュメントへの Windows フォーム コントロールを追加します。](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
