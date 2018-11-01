---
title: 'チュートリアル: 操作ウィンドウから文書にテキストを挿入します。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c858cfbd2fb48aa850e395d74d7f03386ec8bc2f
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671860"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>チュートリアル: 操作ウィンドウから文書にテキストを挿入します。
  このチュートリアルでは、Microsoft Office Word ドキュメントで、[操作] ウィンドウを作成する方法を示します。 [操作] ウィンドウには、入力を収集し、文書にテキストを送信する 2 つのコントロールが含まれています。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   操作ウィンドウ コントロールでの Windows フォーム コントロールを使用してインターフェイスを設計します。  
  
-   アプリケーションを開いたときに、操作ウィンドウを表示します。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## <a name="create-the-project"></a>プロジェクトの作成  
 最初に、Word 文書のプロジェクトを作成します。  
  
### <a name="to-create-a-new-project"></a>新しいプロジェクトを作成するには  
  
1.  名前の Word 文書プロジェクトを作成**マイ基本的な操作 ウィンドウ**します。 ウィザードで、次のように選択します。**新しい文書を作成**です。 詳細については、次の[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)を参照してください。  
  
     デザイナーで新しい Word 文書を開き、**マイ基本的な操作 ウィンドウ**プロジェクトを**ソリューション エクスプ ローラー**します。  
  
## <a name="add-text-and-bookmarks-to-the-document"></a>文書にテキストとブックマークを追加します。  
 [操作] ウィンドウでは、文書内のブックマークにテキストを送信します。 ドキュメントをデザインするには、基本的なフォームを作成するには、いくつかテキストを入力します。  
  
### <a name="to-add-text-to-your-document"></a>文書にテキストを追加するには  
  
1. Word ドキュメントには、次のテキストを入力します。  
  
    **2008 年 3 月 21 日**  
  
    **Name**  
  
    **アドレス**  
  
    **これは、Word の基本的な操作ウィンドウの例です。**  
  
   追加することができます、<xref:Microsoft.Office.Tools.Word.Bookmark>コントロールをドラッグしてから、ドキュメント、**ツールボックス**Visual Studio でまたはを使用して、**ブックマーク**Word のダイアログ ボックス。  
  
### <a name="to-add-a-bookmark-control-to-your-document"></a>ドキュメントにブックマーク コントロールを追加するには  
  
1.  **Word コントロール**のタブ、**ツールボックス**、ドラッグ、<xref:Microsoft.Office.Tools.Word.Bookmark>コントロールをドキュメント。  
  
     **ブックマーク コントロールの追加** ダイアログ ボックスが表示されます。  
  
2.  単語を選択する**名前**、せず、段落記号を選択し、をクリックして**OK**。  
  
    > [!NOTE]  
    >  外部ブックマーク、段落記号があります。 段落記号がドキュメントに表示されていない場合は、クリックして、**ツール**メニューで、 **Microsoft Office Word Tools**順にクリックします**オプション**します。 をクリックして、**ビュー**タブをクリックし、選択、**段落記号** チェック ボックス、**記号**のセクション、**オプション** ダイアログ ボックス。  
  
3.  **プロパティ**ウィンドウで、変更、**名前**プロパティの**Bookmark1**に**次に、この**します。  
  
4.  単語を選択する**アドレス**、段落記号を選択することがなく。  
  
5.  **挿入**リボンのタブで、**リンク**グループで、**ブックマーク**します。  
  
6.  **ブックマーク**ダイアログ ボックスに「 **showAddress**で、**ブックマーク名**ボックスし、[] をクリックして**追加**します。  
  
## <a name="add-controls-to-the-actions-pane"></a>[操作] ウィンドウにコントロールを追加します。  
 操作ウィンドウのインターフェイスを設計するには、操作ウィンドウ コントロールをプロジェクトに追加し、操作ウィンドウ コントロールを Windows フォーム コントロールを追加します。  
  
### <a name="to-add-an-actions-pane-control"></a>操作ウィンドウ コントロールを追加するには  
  
1.  選択、**マイ基本的な操作 ウィンドウ**プロジェクト**ソリューション エクスプ ローラー**します。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
3.  **新しい項目の追加**ダイアログ ボックスで、をクリックして**操作ウィンドウ コントロール**、コントロールに名前を**InsertTextControl、**  をクリック**追加**します。  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>操作ウィンドウ コントロールに Windows フォーム コントロールを追加するには  
  
1.  操作ウィンドウ コントロールがデザイナーで表示されない場合はダブルクリック**InsertTextControl**します。  
  
2.  **コモン コントロール**のタブ、**ツールボックス**、ドラッグ、**ラベル**操作ウィンドウ コントロールを制御します。  
  
3.  変更、**テキスト**ラベル コントロールのプロパティ**名前**します。  
  
4.  追加、 **Textbox**操作ウィンドウ コントロールを制御し、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**GetName**|  
    |**Size**|**130, 20**|  
  
5.  1 秒あたりの追加**ラベル**操作ウィンドウ コントロールを制御し、変更、**テキスト**プロパティを**アドレス**します。  
  
6.  1 秒あたりの追加**Textbox**操作ウィンドウ コントロールを制御し、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**GetAddress**|  
    |**戻り値を受け入れます**|**True**|  
    |**Multiline**|**True**|  
    |**Size**|**130, 40**|  
  
7.  追加、**ボタン**操作ウィンドウ コントロールを制御し、次のプロパティを変更します。  
  
    |プロパティ|[値]|  
    |--------------|-----------|  
    |**Name**|**addText**|  
    |**[テキスト]**|**[挿入]**|  
  
## <a name="add-code-to-insert-text-into-the-document"></a>文書にテキストを挿入するコードを追加します。  
 操作ウィンドウで、適切なにテキスト ボックスからテキストを挿入するコードを記述<xref:Microsoft.Office.Tools.Word.Bookmark>ドキュメント内のコントロール。 使用することができます、`Globals`操作ウィンドウ上のコントロールから、ドキュメント上のコントロールにアクセスするクラス。 詳細については、次を参照してください。 [Office プロジェクト内のオブジェクトへのアクセスをグローバル](../vsto/global-access-to-objects-in-office-projects.md)します。  
  
### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>ドキュメント内のブックマークの [操作] ウィンドウからテキストを挿入するには  
  
1.  次のコードを追加、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、 **addText**ボタンをクリックします。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  C# では、ボタン クリックのイベント ハンドラーを追加する必要があります。 このコードを配置することができます、`InsertTextControl`コンス トラクターの呼び出し後`IntializeComponent`します。 イベント ハンドラーの作成方法の詳細については、次を参照してください。[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="add-code-to-show-the-actions-pane"></a>操作ウィンドウを表示するコードを追加します。  
 [操作] ウィンドウを表示するには、コントロールのコレクションを作成したコントロールを追加します。  
  
### <a name="to-show-the-actions-pane"></a>[操作] ウィンドウを表示するには  
  
1.  操作ウィンドウ コントロールでの新しいインスタンスを作成、`ThisDocument`クラス。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  次のコードを追加、<xref:Microsoft.Office.Tools.Word.Document.Startup>イベント ハンドラーの`ThisDocument`します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="test-the-application"></a>アプリケーションをテストする  
 ドキュメントをテストして、ドキュメントが開かれ、ボタンがクリックされたときにテキスト ボックスに入力したテキストがブックマークに挿入がときに、[操作] ウィンドウを開き、ことを確認します。  
  
### <a name="to-test-your-document"></a>文書をテストするには  
  
1.  キーを押して**F5**プロジェクトを実行します。  
  
2.  [操作] ウィンドウが表示されていることを確認します。  
  
3.  操作ウィンドウ上のテキスト ボックスに、名前とアドレスを入力し、をクリックして**挿入**します。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、次のタスクを行います。  
  
-   Excel で操作ウィンドウを作成します。 詳細については、次を参照してください。[方法: Excel ブックに操作ウィンドウを追加する](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))します。  
  
-   データを操作ウィンドウ上のコントロールにバインドします。 詳細については、次を参照してください。[チュートリアル: Word の操作ウィンドウ上のコントロールにデータをバインド](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)します。  
  
## <a name="see-also"></a>関連項目  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [方法: Word 文書に操作ウィンドウを追加したり、Excel ブック](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [方法: Excel ブックに操作ウィンドウを追加します。](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))   
 [方法: アクション ペイン上のコントロールのレイアウトの管理](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Bookmark コントロール](../vsto/bookmark-control.md)  
  
  