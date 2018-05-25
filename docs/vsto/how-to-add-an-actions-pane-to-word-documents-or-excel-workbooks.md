---
title: '方法: Word 文書に操作ウィンドウを追加または Excel ブック'
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
ms.openlocfilehash: ebf4896411a46b2c75edd8216bd61623bc9b728f
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>方法: Word 文書または Excel ブックに操作ウィンドウを追加する
  Microsoft Office Word ドキュメントまたは Microsoft Excel ブックに操作ウィンドウを追加するには、Windows フォーム ユーザー コントロールをまず作成します。 次に、ユーザー コントロールを追加、<xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>のプロパティ、`ThisDocument.ActionsPane`フィールド (Word の場合) または`ThisWorkbook.ActionsPane`project のフィールド (Excel)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="creating-the-user-control"></a>ユーザー コントロールの作成  
 次の手順では、Excel プロジェクトまたは、単語内でユーザー コントロールを作成する方法を示します。 また、ユーザー コントロールがクリックされたときに、文書またはブックにテキストを書き込むにボタンを追加します。  
  
#### <a name="to-create-the-user-control"></a>ユーザー コントロールを作成するには  
  
1.  Visual Studio で Word または Excel のドキュメント レベルのプロジェクトを開きます。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
3.  **新しい項目の追加**ダイアログ ボックスで、**操作ウィンドウ コントロール**、名前を付けます**HelloControl**、 をクリック**追加**です。  
  
    > [!NOTE]  
    >  代わりに追加することができます、**ユーザー コントロール**をプロジェクトに項目。 によって生成されたクラス、**操作ウィンドウ コントロール**と**ユーザー コントロール**項目は機能的に等価です。  
  
4.  **Windows フォーム**のタブ、**ツールボックス**ドラッグ、**ボタン**コントロールをコントロールにします。  
  
    > [!NOTE]  
    >  コントロールがデザイナーで表示されていない場合をダブルクリックして**HelloControl**で**ソリューション エクスプ ローラー**です。  
  
5.  コードを追加して、<xref:System.Windows.Forms.Control.Click>ボタンのイベント ハンドラー。 次の例では、Microsoft Office Word ドキュメントのコードを示します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  C# の場合は、ボタンをクリックし、イベント ハンドラーを追加する必要があります。 このコードを配置することができます、`HelloControl`コンス トラクターへの呼び出し後`IntializeComponent`です。  
  
     イベント ハンドラーを作成する方法については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="add-the-user-control-to-the-actions-pane"></a>[操作] ウィンドウに、ユーザー コントロールを追加します。  
 [操作] ウィンドウを表示するユーザー コントロールを追加、<xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>のプロパティ、`ThisDocument.ActionsPane`フィールド (Word の場合) または`ThisWorkbook.ActionsPane`フィールド (Excel)。  
  
### <a name="to-add-the-user-control-to-the-actions-pane"></a>[操作] ウィンドウにユーザー コントロールを追加するには  
  
1.  次のコードを追加、`ThisDocument`または`ThisWorkbook`クラス レベルの宣言とクラス (は、メソッドに次のコードが追加されることはしません)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  次のコードを追加、`ThisDocument_Startup`のイベント ハンドラー、`ThisDocument`クラスまたは`ThisWorkbook_Startup`のイベント ハンドラー、`ThisWorkbook`クラスです。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>関連項目  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [チュートリアル: アクション ウィンドウから文書にテキストを挿入します。](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [方法: アクション ペイン上のコントロールのレイアウトの管理](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [チュートリアル: アクション ウィンドウから文書にテキストを挿入します。](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  