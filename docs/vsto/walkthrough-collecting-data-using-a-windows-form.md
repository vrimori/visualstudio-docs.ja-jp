---
title: "チュートリアル : Windows フォームを使用してデータを収集する方法"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "データ [Visual Studio での Office 開発]、Windows フォーム"
  - "Windows フォーム [Visual Studio での Office 開発]、収集 (データを)"
  - "フォーム [Visual Studio での Office 開発]、チュートリアル"
  - "ワークシート [Visual Studio での Office 開発]、収集 (データを)"
ms.assetid: 40e87f7f-cfbb-4761-bf1b-d042f45f4f09
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# チュートリアル : Windows フォームを使用してデータを収集する方法
  このチュートリアルでは、Microsoft Office Excel のドキュメント レベルのカスタマイズから Windows フォームを開き、ユーザーから情報を収集し、その情報をワークシートのセルに書き込む方法について説明します。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 このチュートリアルでは具体的には Excel のドキュメントレベルのプロジェクトを使用していますが、チュートリアルで示される概念は他の Office プロジェクトに適用できます。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 新規プロジェクトの作成  
 まず、Excel ブック プロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  **WinFormInput** という名前で Excel ブック プロジェクトを作成し、ウィザードで **\[新しいドキュメントの作成\]** を選択します。 詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     Visual Studio により新しい Excel ブックがデザイナーで開き、**WinFormInput** プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## ワークシートへの NamedRange コントロールの追加  
  
#### Sheet1 に名前付き範囲を追加するには  
  
1.  `Sheet1` でセル **A1** を選択します。  
  
2.  **\[名前\]** ボックスに **formInput** と入力します。  
  
     **\[名前\]** ボックスは数式バーの左側、ワークシートの列 **A** の真上にあります。  
  
3.  ENTER キーを押します。  
  
     <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールがセル **A1** に追加されます。 ワークシート上には表示されませんが、セル **A1** を選択すると、**\[名前\]** ボックス \(左側のワークシートの真上\) および **\[プロパティ\]** ウィンドウに **formInput** と表示されます。  
  
## プロジェクトへの Windows フォームの追加  
 ユーザーに情報を要求するための Windows フォームを作成します。  
  
#### Windows フォームを追加するには  
  
1.  **ソリューション エクスプローラー**でプロジェクト **WinFormInput** を選択します。  
  
2.  **\[プロジェクト\]** メニューの **\[Windows フォームの追加\]** をクリックします。  
  
3.  フォームに **GetInputString.vb** または **GetInputString.cs** という名前を付けてから、**\[追加\]** をクリックします。  
  
     デザイナーで新しいフォームが開きます。  
  
4.  フォームに <xref:System.Windows.Forms.TextBox> および <xref:System.Windows.Forms.Button> を追加します。  
  
5.  ボタンを選択し、**\[プロパティ\]** ウィンドウでプロパティ **\[テキスト\]** を見つけ出し、テキストを **OK** に変更します。  
  
 次に、ユーザーの情報を収集するためのコードを `ThisWorkbook.vb` または `ThisWorkbook.cs` に追加します。  
  
## Windows フォームの表示および情報の収集  
 `GetInputString` Windows フォームのインスタンスを作成しそれを表示してから、ワークシート内のセルにユーザーの情報を書き込みます。  
  
#### フォームを表示し、情報を収集するには  
  
1.  **ソリューション エクスプローラー**で **ThisWorkbook.vb** または **ThisWorkbook.cs** を右クリックしてから、**\[コードの表示\]** をクリックします。  
  
2.  `ThisWorkbook` の <xref:Microsoft.Office.Tools.Excel.Workbook.Open> イベント ハンドラーで、次のコードを追加して、フォーム `GetInputString` の変数を宣言してから、フォームを表示します。  
  
    > [!NOTE]  
    >  C\# では、次のようにイベント ハンドラーを <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> イベントに追加する必要があります。 イベント ハンドラーの作成方法の詳細については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」を参照してください。  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/CS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/VB/ThisWorkbook.vb#1)]  
  
3.  テキストを名前付き範囲に書き込む `WriteStringToCell` という名前のメソッドを作成します。 このメソッドはフォームから呼び出され、ユーザーの入力は <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールである `formInput` のセル **A1** に渡されます。  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/CS/ThisWorkbook.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/VB/ThisWorkbook.vb#2)]  
  
 次に、ボタンのクリック イベントを処理するためのコードをフォームに追加します。  
  
## ワークシートへの情報の送信  
  
#### ワークシートに情報を送信するには  
  
1.  **ソリューション エクスプローラー**で **GetInputString** を右クリックし、**\[デザイナーの表示\]** をクリックします。  
  
2.  ボタンを右クリックして、ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーが追加されたコード ファイルを開きます。  
  
3.  テキスト ボックスから入力を受け取り、関数 `WriteStringToCell` に送信してから、フォームを閉じるコードをイベント ハンドラーに追加します。  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/CS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/VB/GetInputString.vb#3)]  
  
## テスト中  
 これで、プロジェクトを実行できます。 Windows フォームが表示され、ワークシートに入力が表示されます。  
  
#### ブックをテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  Windows フォームが表示されることを確認します。  
  
3.  テキスト ボックスに **Hello World** と入力し、**\[OK\]** をクリックします。  
  
4.  ワークシートのセル **A1** に **Hello World** と表示されることを確認します。  
  
## 次の手順  
 このチュートリアルでは、Windows フォームを表示しワークシートにデータを渡すための基本操作を説明しました。 これ以外にも、次の操作が可能です。  
  
-   Excel ブックまたは Word 文書で Windows フォーム コントロールを使用する。 詳細については、「[Office ドキュメントでの Windows フォーム コントロールの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)」を参照してください。  
  
-   ドキュメント レベルのカスタマイズまたは VSTO アドインから Microsoft Office アプリケーションのユーザー インターフェイスを変更する。 詳細については、「[Office UI のカスタマイズ](../vsto/office-ui-customization.md)」を参照してください。  
  
## 参照  
 [Office ソリューションの開発](../vsto/developing-office-solutions.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)   
 [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)   
 [Word を使用したチュートリアル](../vsto/walkthroughs-using-word.md)   
 [Excel を使用したチュートリアル](../vsto/walkthroughs-using-excel.md)  
  
  