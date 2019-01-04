---
title: '方法: Word 文書または Excel ブックに操作ウィンドウを追加します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4630834f1673e1c96ca67b90a8bb329951f53de1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827021"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>方法: Word 文書または Excel ブックに操作ウィンドウを追加する
  に Microsoft Office Word ドキュメントまたは Microsoft Excel ブックを操作ウィンドウを追加するには、Windows フォーム ユーザー コントロールをまず作成します。 次に、ユーザー コントロールを追加、<xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>のプロパティ、`ThisDocument.ActionsPane`フィールド (Word) または`ThisWorkbook.ActionsPane`project のフィールド (Excel)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="creating-the-user-control"></a>ユーザー コントロールの作成  
 次の手順では、Excel プロジェクトまたは Word ユーザー コントロールを作成する方法を示します。 また、ボタンは、ユーザー コントロールがクリックされたときに、ドキュメントまたはブックにテキストを書き込むも追加されます。  
  
#### <a name="to-create-the-user-control"></a>ユーザー コントロールを作成するには  
  
1.  Visual Studio で Word または Excel ドキュメント レベルのプロジェクトを開きます。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
3.  **新しい項目の追加**ダイアログ ボックスで、**操作ウィンドウ コントロール**、名前を付けます**HelloControl**、 をクリック**追加**します。  
  
    > [!NOTE]  
    >  別の方法として追加することができます、**ユーザー コントロール**をプロジェクトに項目。 によって生成されたクラス、**操作ウィンドウ コントロール**と**ユーザー コントロール**項目は、機能的に同等です。  
  
4.  **Windows フォーム**のタブ、**ツールボックス**ドラッグ、**ボタン**コントロールをコントロールにします。  
  
    > [!NOTE]  
    >  コントロールがデザイナーで表示されていない場合をダブルクリックします**HelloControl**で**ソリューション エクスプ ローラー**します。  
  
5.  コードを追加して、<xref:System.Windows.Forms.Control.Click>ボタンのイベント ハンドラー。 次の例では、Microsoft Office Word ドキュメントのコードを示します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  C# では、ボタン クリックのイベント ハンドラーを追加する必要があります。 このコードを配置することができます、`HelloControl`コンス トラクターの呼び出し後`InitializeComponent`します。  
  
     イベント ハンドラーを作成する方法については、次を参照してください。[方法。Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="add-the-user-control-to-the-actions-pane"></a>[操作] ウィンドウにユーザー コントロールを追加します。  
 [操作] ウィンドウを表示するには、ユーザー コントロールを追加、<xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>のプロパティ、`ThisDocument.ActionsPane`フィールド (Word) または`ThisWorkbook.ActionsPane`フィールド (Excel)。  
  
### <a name="to-add-the-user-control-to-the-actions-pane"></a>[操作] ウィンドウにユーザー コントロールを追加するには  
  
1.  次のコードを追加、`ThisDocument`または`ThisWorkbook`クラスレベル宣言としてクラス (は、メソッドに次のコードが追加されることはありません)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  次のコードを追加、`ThisDocument_Startup`のイベント ハンドラー、`ThisDocument`クラスまたは`ThisWorkbook_Startup`のイベント ハンドラー、`ThisWorkbook`クラス。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>関連項目  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [チュートリアル: 操作ウィンドウから文書にテキストを挿入します。](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [方法: アクション ペイン上のコントロールのレイアウトを管理します。](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [チュートリアル: 操作ウィンドウから文書にテキストを挿入します。](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
