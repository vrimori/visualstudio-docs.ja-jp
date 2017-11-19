---
title: "チュートリアル: アクション ウィンドウから文書にテキストを挿入する |Microsoft ドキュメント"
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
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
ms.assetid: fd14c896-5737-4a20-94f7-6064b67112c5
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5ca062823968153d7c8979cb13c0e3d403237be1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-inserting-text-into-a-document-from-an-actions-pane"></a>チュートリアル : 操作ウィンドウから文書へのテキストの挿入
  このチュートリアルでは、Microsoft Office Word 文書に操作ウィンドウを作成する方法を示します。 [操作] ウィンドウには、入力を収集し、文書にテキストを送信する 2 つのコントロールが含まれています。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   操作ウィンドウ コントロール Windows フォーム コントロールを使用してインターフェイスを設計します。  
  
-   アプリケーションが開かれたときに、[操作] ウィンドウを表示します。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 最初に、Word 文書のプロジェクトを作成します。  
  
#### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Word 文書プロジェクトを作成**マイ基本的な操作 ウィンドウ**します。 ウィザードで、次のように選択します。**新しいドキュメントを作成する**です。 詳細については、「 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
     デザイナーで新しい Word 文書を開き、**マイ基本的な操作 ウィンドウ**プロジェクトを**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-text-and-bookmarks-to-the-document"></a>文書へのテキストとブックマークの追加  
 [操作] ウィンドウでは、ドキュメント内のブックマークにテキストを送信します。 ドキュメントをデザインするには、基本フォームを作成するいくつかのテキストを入力します。  
  
#### <a name="to-add-text-to-your-document"></a>文書にテキストを追加するには  
  
1.  Word 文書に次のテキストを入力します。  
  
     **2008 年 3 月 21 日**  
  
     **名前**  
  
     **アドレス**  
  
     **これは、Word の基本的な操作 ウィンドウの例です。**  
  
 追加することができます、<xref:Microsoft.Office.Tools.Word.Bookmark>をドラッグしてから、ドキュメントにコントロール、**ツールボックス**Visual Studio でまたはを使用して、**ブックマーク**Word のダイアログ ボックス。  
  
#### <a name="to-add-a-bookmark-control-to-your-document"></a>ドキュメントにブックマーク コントロールを追加するには  
  
1.  **Word コントロール**のタブ、**ツールボックス**、ドラッグ、<xref:Microsoft.Office.Tools.Word.Bookmark>をドキュメントにコントロールできます。  
  
     **ブックマーク コントロールの追加** ダイアログ ボックスが表示されます。  
  
2.  単語を選択して**名前**せず、段落記号を選択しをクリックして**OK**です。  
  
    > [!NOTE]  
    >  段落記号は、ブックマークの外部にする必要があります。 段落記号がドキュメントに表示されていない場合をクリックして、**ツール** メニューのをポイント**Microsoft Office Word Tools**  をクリックし、**オプション**です。 クリックして、**ビュー**タブをクリックし、選択、**段落記号** チェック ボックス、**記号**のセクション、**オプション** ダイアログ ボックス。  
  
3.  **プロパティ**ウィンドウで、変更、**名前**プロパティ**Bookmark1**に**次に、この**です。  
  
4.  単語を選択して**アドレス**、段落記号を選択しない場合。  
  
5.  **挿入**リボンのタブで、**リンク**グループで、**ブックマーク**です。  
  
6.  **ブックマーク** ダイアログ ボックスで、「 **showAddress**で、**ブックマーク名**ボックスし、 をクリックして**追加**です。  
  
## <a name="adding-controls-to-the-actions-pane"></a>[操作] ウィンドウにコントロールを追加します。  
 操作ウィンドウのインターフェイスを設計するには、操作ウィンドウ コントロールをプロジェクトに追加し、操作ウィンドウ コントロールに Windows フォーム コントロールを追加します。  
  
#### <a name="to-add-an-actions-pane-control"></a>操作ウィンドウ コントロールを追加するには  
  
1.  選択、**マイ基本的な操作 ウィンドウ**プロジェクト**ソリューション エクスプ ローラー**です。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
3.  **新しい項目の追加**ダイアログ ボックスで、をクリックして**操作ウィンドウ コントロール**、コントロールの名前を付けます**InsertTextControl、**  をクリック**追加**です。  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Windows フォーム コントロールを操作ウィンドウ コントロールに追加するには  
  
1.  操作ウィンドウ コントロールがデザイナーに表示されない場合は、ダブルクリック**InsertTextControl**です。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**、ドラッグ、**ラベル**操作ウィンドウ コントロールにコントロールできます。  
  
3.  変更、**テキスト**するラベル コントロールのプロパティ**名前**です。  
  
4.  追加、 **Textbox**操作ウィンドウ コントロールに制御し、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |--------------|-----------|  
    |**名前**|**getName**|  
    |**Size**|**130, 20**|  
  
5.  1 秒あたりの追加**ラベル**操作ウィンドウ コントロールに制御し、変更、**テキスト**プロパティを**アドレス**です。  
  
6.  1 秒あたりの追加**Textbox**操作ウィンドウ コントロールに制御し、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |--------------|-----------|  
    |**名前**|**getAddress**|  
    |**戻り値を受け入れます**|**True**|  
    |**Multiline**|**True**|  
    |**Size**|**130, 40**|  
  
7.  追加、**ボタン**操作ウィンドウ コントロールに制御し、次のプロパティを変更します。  
  
    |プロパティ|値|  
    |--------------|-----------|  
    |**名前**|**addText**|  
    |**[テキスト]**|**挿入します。**|  
  
## <a name="adding-code-to-insert-text-into-the-document"></a>文書にテキストを挿入するコードを追加します。  
 [操作] ウィンドウのテキスト ボックスに、適切なテキストを挿入するコードを記述<xref:Microsoft.Office.Tools.Word.Bookmark>ドキュメント内のコントロールです。 使用することができます、`Globals`操作ウィンドウ上のコントロールから、文書のコントロールにアクセスするクラス。 詳細については、次を参照してください。 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)です。  
  
#### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>ドキュメント内のブックマークの操作ウィンドウからテキストを挿入するには  
  
1.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、 **addText**ボタンをクリックします。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  C# の場合は、ボタンをクリックし、イベント ハンドラーを追加する必要があります。 このコードを配置することができます、`InsertTextControl`コンス トラクターへの呼び出し後`IntializeComponent`です。 イベント ハンドラーの作成方法の詳細については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="adding-code-to-show-the-actions-pane"></a>[操作] ウィンドウを表示するコードを追加します。  
 [操作] ウィンドウを表示するには、コントロール コレクションを作成したコントロールを追加します。  
  
#### <a name="to-show-the-actions-pane"></a>[操作] ウィンドウを表示するには  
  
1.  操作ウィンドウ コントロールでの新しいインスタンスを作成、`ThisDocument`クラスです。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  次のコードを追加、<xref:Microsoft.Office.Tools.Word.Document.Startup>のイベント ハンドラー`ThisDocument`です。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 文書をテストして、ドキュメントが開かれ、ボタンがクリックされたときに、テキスト ボックスに入力したテキストがブックマークに挿入がときに、[操作] ウィンドウを開き、ことを確認します。  
  
#### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  [操作] ウィンドウが表示されていることを確認します。  
  
3.  [操作] ウィンドウでテキスト ボックスに名前とアドレスを入力し、をクリックして**挿入**です。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、次のタスクを行います。  
  
-   Excel で操作ウィンドウを作成します。 詳細については、次を参照してください。[する方法: Excel ブックに操作ウィンドウを追加](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872)です。  
  
-   操作ウィンドウ上のコントロールにデータをバインドします。 詳細については、次を参照してください。[チュートリアル: Word の操作ウィンドウ上のコントロールへのデータ バインディング](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)です。  
  
## <a name="see-also"></a>関連項目  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [方法: Word 文書や Excel ブックに操作ウィンドウを追加](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [方法: Excel ブックに操作ウィンドウを追加](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [方法: アクション ペイン上のコントロールのレイアウトの管理](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Bookmark コントロール](../vsto/bookmark-control.md)  
  
  