---
title: '方法: アクション ペイン上のコントロールのレイアウトを管理します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: ee790707a5c1c74f3227f74874c66bb4438e7ab0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991176"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>方法: アクション ペイン上のコントロールのレイアウトを管理します。
  操作ウィンドウが既定では、ドキュメントまたはワークシートの右側にドッキングされています。ただし、左、上、または下部にドッキングできます。 複数のユーザー コントロールを使用している場合は、[操作] ウィンドウにユーザー コントロールを正しくスタックするコードを記述できます。 詳細については、次を参照してください。[操作ウィンドウの概要](../vsto/actions-pane-overview.md)します。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 コントロールの積み重ね順は、[操作] ウィンドウを垂直方向または水平方向にドッキングするかどうかによって異なります。  
  
> [!NOTE]  
>  ユーザーには、実行時に操作ウィンドウがサイズ変更、操作ウィンドウのサイズを変更するためにコントロールを設定できます。 Windows フォーム コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティを使用すると、コントロールを操作ウィンドウに固定できます。 詳細については、「[方法 :Windows フォーム上のコントロールを固定](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)します。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>操作ウィンドウ コントロールの積み重ね順を設定するには  
  
1.  複数のユーザー コントロールまたは入れ子になった操作ウィンドウ コントロールを使用して、操作ウィンドウを含む Microsoft Office Word のドキュメント レベルのプロジェクトを開きます。 詳細については、「[方法 :Word 文書に操作ウィンドウを追加したり、Excel ブック](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)します。  
  
2.  右クリック**ThisDocument.cs**または**ThisDocument.vb**で**ソリューション エクスプ ローラー**  をクリックし、**コードの表示**します。  
  
3.  <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged>操作ウィンドウ、[操作] ウィンドウの向きが水平方向があるかどうかのイベント ハンドラー。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]  
  
4.  印刷の向きが水平方向の場合は、操作ウィンドウ コントロールを左からのスタックします。それ以外の場合、それらを上から積み重ねます。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]  
  
5.  C# でのイベント ハンドラーを追加する必要があります、`ActionsPane`を<xref:Microsoft.Office.Tools.Word.Document.Startup>イベント ハンドラー。 イベント ハンドラーの作成方法の詳細については、次を参照してください。[方法。Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]  
  
6.  プロジェクトを実行し、ドキュメントの上部にある [操作] ウィンドウがドッキングされているし、ドキュメントの右側にある [操作] ウィンドウがドッキングされているときに、コントロールを上から下に積み上げられたときに、操作ウィンドウ コントロールを左右からを積み重ねることを確認します。  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   複数のユーザー コントロールを含む操作ウィンドウまたは入れ子になったアクション ウィンドウで Word ドキュメント レベルのプロジェクトを制御します。  
  
## <a name="see-also"></a>関連項目  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [方法: Word 文書または Excel ブックに操作ウィンドウを追加します。](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [方法: Word 文書や Excel ブックに、アクション ペインを追加します。](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [チュートリアル: 操作ウィンドウから文書にテキストを挿入します。](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [チュートリアル: 操作ウィンドウから文書にテキストを挿入します。](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
