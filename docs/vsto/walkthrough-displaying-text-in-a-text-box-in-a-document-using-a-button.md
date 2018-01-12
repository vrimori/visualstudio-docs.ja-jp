---
title: "チュートリアル: ボタンを使用してドキュメント内のテキスト ボックスにテキストを表示する |Microsoft ドキュメント"
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
helpviewer_keywords: text boxes, displaying text in documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 803dcbe27eedc4b93443a6389b4acf7ee2dc08cf
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button"></a>チュートリアル : ボタンを使用して文書内のテキスト ボックスにテキストを表示する方法
  このチュートリアルでは、Microsoft Office Word のドキュメント レベルのカスタマイズでボタンやテキスト ボックスを使用する方法を示します。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   デザイン時にドキュメント レベルのプロジェクトで Word 文書にコントロールを追加する。  
  
-   ボタンがクリックされたときにテキスト ボックスにデータを読み込む。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初に、Word 文書のプロジェクトを作成します。  
  
#### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Word 文書プロジェクトを作成**My Word Button**です。 ウィザードで、次のように選択します。**新しいドキュメントを作成する**です。  
  
     詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     デザイナーで新しい Word 文書を開き、 **My Word Button**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-controls-to-the-word-document"></a>Word 文書へのコントロールの追加  
 ユーザー インターフェイス コントロールは、Word 文書上のボタンとテキスト ボックスで構成されます。  
  
#### <a name="to-add-a-button-and-a-text-box"></a>ボタンとテキスト ボックスを追加するには  
  
1.  Visual Studio デザイナーで文書が開いていることを確認します。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**、ドラッグ、<xref:Microsoft.Office.Tools.Word.Controls.TextBox>コントロールをドキュメント。  
  
    > [!NOTE]  
    >  Word の既定では、コントロールはテキスト中にインラインでドロップされます。 制御する方法を変更して、図形オブジェクトは、既定値を変更することで挿入、**編集**のタブ、**オプション**Word のダイアログ ボックス。  
  
3.  **[表示]** メニューの **[プロパティ ウィンドウ]**をクリックします。  
  
4.  検索**TextBox1**で、**プロパティ**ウィンドウのドロップダウン ボックスと変更、**名前**にテキスト ボックスのプロパティ**displayText**です。  
  
5.  ドラッグ、**ボタン**コントロールを文書と、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**insertText**|  
    |**[テキスト]**|**テキストを挿入します。**|  
  
 これで、ボタンがクリックされたときに実行されるコードを記述できるようになりました。  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>ボタンがクリックされたときにテキスト ボックスにデータを読み込む  
 ユーザーが、ボタンをクリックするたびに**Hello World!** テキスト ボックスに追加されます。  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>ボタンがクリックされたときにテキスト ボックスに書き込むには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**ThisDocument**、クリックして**コードの表示**ショートカット メニューの します。  
  
2.  ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]  
  
3.  C# では、ボタンのイベント ハンドラーを <xref:Microsoft.Office.Tools.Word.Document.Startup> イベントに追加する必要があります。 イベント ハンドラーの作成方法の詳細については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 確認して、文書をテストすることができます、メッセージ**Hello World!** ボタンをクリックしたときに、テキスト ボックスに表示されます。  
  
#### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  ボタンをクリックします。  
  
3.  いることを確認**Hello World!** テキスト ボックスに表示されます。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルでは、Word 文書でボタンとテキスト ボックスを使用する際の基本事項について説明しました。 ここでは、次のタスクを行います。  
  
-   コンボ ボックスを使用して書式設定を変更する。 詳細については、次を参照してください。[チュートリアル: を変更するドキュメントの書式設定 チェック ボックス コントロールを使用した](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)です。  
  
-   オプション ボタンを使用してグラフのスタイルを選択する。 詳細については、次を参照してください。[チュートリアル: グラフを更新するラジオ ボタンを使用してドキュメントで](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)です。  
  
## <a name="see-also"></a>参照  
 [Windows フォームでコントロールの Office ドキュメントの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [チュートリアルを使用して Word](../vsto/walkthroughs-using-word.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [方法: Windows フォーム コントロールの Office ドキュメントへの追加](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)  
  
  