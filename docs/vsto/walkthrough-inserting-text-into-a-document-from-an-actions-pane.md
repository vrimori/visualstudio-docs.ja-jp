---
title: "チュートリアル : 操作ウィンドウから文書へのテキストの挿入"
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
  - "操作ウィンドウ [Visual Studio での Office 開発], 追加 (コントロールを)"
  - "操作ウィンドウ [Visual Studio での Office 開発], 作成 (Word で)"
  - "スマート ドキュメント [Visual Studio での Office 開発], 追加 (コントロールを)"
  - "スマート ドキュメント [Visual Studio での Office 開発], 作成 (Word で)"
ms.assetid: fd14c896-5737-4a20-94f7-6064b67112c5
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# チュートリアル : 操作ウィンドウから文書へのテキストの挿入
  このチュートリアルでは、Microsoft Office Word 文書で操作ウィンドウを作成する方法について説明します。  操作ウィンドウには、入力を収集するコントロールと、そのテキストを文書に送信するコントロールがあります。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   操作ウィンドウ コントロール上で Windows フォーム コントロールを使用してユーザー インターフェイスをデザインします。  
  
-   アプリケーションが開かれたときに操作ウィンドウを表示します。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## プロジェクトの作成  
 まず、Word 文書プロジェクトを作成します。  
  
#### 新しいプロジェクトを作成するには  
  
1.  My Basic Actions Pane という名前の Word 文書プロジェクトを作成します。  ウィザードで、**\[新規ドキュメントの作成\]** をクリックします。  詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     Visual Studio により、デザイナーで新しい Word 文書が開き、**My Basic Actions Pane** プロジェクトが**ソリューション エクスプローラー**に追加されます。  
  
## 文書へのテキストとブックマークの追加  
 操作ウィンドウは、文書内のブックマークにテキストを送信します。  文書をデザインするには、いくつかのテキストを入力して基本となるフォームを作成します。  
  
#### 文書にテキストを追加するには  
  
1.  次のテキストを Word 文書に入力します。  
  
     March 21, 2008  
  
     名前  
  
     Address  
  
     This is an example of a basic actions pane in Word.  
  
 文書に <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを追加するには、Visual Studio で**ツールボックス**からコントロールをドラッグするか、Word で **\[ブックマーク\]** ダイアログ ボックスを使用します。  
  
#### 文書に Bookmark コントロールを追加するには  
  
1.  **ツールボックス**の **\[Word コントロール\]** タブから <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールを文書にドラッグします。  
  
     **\[ブックマーク コントロールの追加\]** ダイアログ ボックスが表示されます。  
  
2.  文書内の "**Name**" という語を、段落記号は除いて選択し、**\[OK\]** をクリックします。  
  
    > [!NOTE]  
    >  段落記号はブックマークに含めないようにします。  文書に段落記号が表示されていない場合は、**\[ツール\]** メニューをクリックし、**\[Microsoft Office Word ツール\]** をポイントして、**\[オプション\]** をクリックします。  **\[表示\]** タブをクリックし、**\[オプション\]** ダイアログ ボックスの **\[編集記号の表示\]** セクションの **\[段落記号\]** チェック ボックスをオンにします。  
  
3.  **\[プロパティ\]** ウィンドウで **\[Name\]** プロパティを **Bookmark1** から **showName** に変更します。  
  
4.  "**Address**" という語を、段落記号は除いて選択します。  
  
5.  リボンの **\[挿入\]** タブの **\[リンク\]** で **\[ブックマーク\]** をクリックします。  
  
6.  **\[ブックマーク\]** ダイアログ ボックスで、**\[ブックマーク名\]** ボックスに「**showAddress**」と入力し、**\[追加\]** をクリックします。  
  
## 操作ウィンドウへのコントロールの追加  
 操作ウィンドウのインターフェイスをデザインするには、プロジェクトに操作ウィンドウ コントロールを追加し、追加した操作ウィンドウ コントロールに Windows フォーム コントロールを追加します。  
  
#### 操作ウィンドウ コントロールを追加するには  
  
1.  **ソリューション エクスプローラー**で **My Basic Actions Pane** プロジェクトを選択します。  
  
2.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
3.  **\[新しい項目の追加\]** ダイアログ ボックスで **\[操作ウィンドウ コントロール\]** をクリックし、コントロールに **InsertTextControl** という名前を指定して、**\[追加\]** をクリックします。  
  
#### 操作ウィンドウ コントロールに Windows フォーム コントロールを追加するには  
  
1.  デザイナーで操作ウィンドウ コントロールが非表示になっている場合は、**InsertTextControl** をダブルクリックします。  
  
2.  **ツールボックス**の **\[コモン コントロール\]** タブから **Label** コントロールを操作ウィンドウ コントロールにドラッグします。  
  
3.  Label コントロールの **Text** プロパティを **Name** に変更します。  
  
4.  操作ウィンドウ コントロールに **Textbox** コントロールを追加し、以下のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**getName**|  
    |**サイズ**|**130, 20**|  
  
5.  操作ウィンドウ コントロールに 2 番目の **Label** コントロールを追加し、**Text** プロパティを **Address** に変更します。  
  
6.  操作ウィンドウ コントロールに 2 番目の **Textbox** コントロールを追加し、以下のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**getAddress**|  
    |**AcceptsReturn**|**True**|  
    |**Multiline**|**True**|  
    |**サイズ**|**130, 40**|  
  
7.  操作ウィンドウ コントロールに **Button** コントロールを追加し、以下のプロパティを変更します。  
  
    |プロパティ|価値|  
    |-----------|--------|  
    |**名前**|**addText**|  
    |**テキスト**|**\[挿入\]**|  
  
## 文書にテキストを挿入するコードの追加  
 操作ウィンドウで、テキスト ボックスのテキストを文書内の対応する <xref:Microsoft.Office.Tools.Word.Bookmark> コントロールに挿入するコードを記述します。  `Globals` クラスを使用して、操作ウィンドウ上のコントロールから文書上のコントロールにアクセスできます。  詳細については、「[Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)」を参照してください。  
  
#### 操作ウィンドウから文書内のブックマークにテキストを挿入するには  
  
1.  **addText** ボタンの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/InsertTextControl.vb#8)]  
  
2.  C\# では、ボタン クリックのイベント ハンドラーを追加する必要があります。  このコードは、`IntializeComponent` の呼び出しの後の `InsertTextControl` コンストラクターに追加できます。  イベンド ハンドラーの作成方法の詳細については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」を参照してください。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/InsertTextControl.cs#9)]  
  
## 操作ウィンドウを表示するコードの追加  
 操作ウィンドウを表示するには、作成したコントロールをコントロール コレクションに追加します。  
  
#### 操作ウィンドウを表示するには  
  
1.  `ThisDocument` クラスで、操作ウィンドウ コントロールの新しいインスタンスを作成します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#10)]  
  
2.  `ThisDocument` の <xref:Microsoft.Office.Tools.Word.Document.Startup> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#11)]  
  
## アプリケーションのテスト  
 文書をテストして、文書を開いたときに操作ウィンドウが開くこと、およびボタンをクリックしたときにテキスト ボックスに入力したテキストがブックマークに挿入されることを確認します。  
  
#### 文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  操作ウィンドウが表示されていることを確認します。  
  
3.  操作ウィンドウ上のテキスト ボックスに自分の名前と住所を入力し、**\[Insert\]** をクリックします。  
  
## 次の手順  
 次に行う作業は以下のとおりです。  
  
-   Excel の操作ウィンドウの作成。  詳細については、「[How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/ja-jp/62abfce6-e44f-419d-85d8-26bf59f33872)」を参照してください。  
  
-   操作ウィンドウ上のコントロールへのデータのバインド。  詳細については、「[チュートリアル : Word の操作ウィンドウ上のコントロールへのデータ バインド](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)」を参照してください。  
  
## 参照  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [方法: Word 文書または Excel ブックに操作ウィンドウを追加する](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/ja-jp/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [方法 : アクション ペイン上のコントロールのレイアウトを管理する](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Bookmark コントロール](../vsto/bookmark-control.md)  
  
  