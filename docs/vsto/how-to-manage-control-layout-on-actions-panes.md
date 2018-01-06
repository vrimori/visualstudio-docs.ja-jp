---
title: "方法: アクション ペイン上のコントロールのレイアウトの管理 |Microsoft ドキュメント"
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
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
ms.assetid: 857550d0-b9c0-4d2f-a947-dd955bcf2823
caps.latest.revision: "59"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 06a2488606b93040cf897ac510455b8a9ef74ce2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>方法 : アクション ペイン上のコントロールのレイアウトを管理する
  既定では、[操作] ウィンドウが文書またはワークシートの右側にドッキングされています。ただし、左、上、または下部にドッキングできます。 複数のユーザー コントロールを使用している場合は、[操作] ウィンドウにユーザー コントロールを正しく積み重ねるコードを記述できます。 詳細については、「 [Actions Pane Overview](../vsto/actions-pane-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 コントロールの積み重ね順は、[操作] ウィンドウがドッキングされている垂直または水平方向にするかどうかによって異なります。  
  
> [!NOTE]  
>  ユーザーは、実行時に、[操作] ウィンドウをサイズ変更する場合、は、[操作] ウィンドウのサイズを変更するためにコントロールを設定できます。 Windows フォーム コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティを使用すると、コントロールを操作ウィンドウに固定できます。 詳細については、次を参照してください。[する方法: Windows フォームでコントロールをアンカー](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)です。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
### <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>操作ウィンドウ コントロールの積み重ね順を設定するには  
  
1.  複数のユーザー コントロールまたは入れ子になった操作ウィンドウ コントロールを使用して、操作ウィンドウを含む Microsoft Office Word のドキュメント レベルのプロジェクトを開きます。 詳細については、次を参照してください。[する方法: Word 文書や Excel ブックに操作ウィンドウを追加](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)です。  
  
2.  右クリック**ThisDocument.cs**または**ThisDocument.vb**で**ソリューション エクスプ ローラー**  をクリックし、**コードの表示**です。  
  
3.  <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged>イベント ハンドラーの操作ウィンドウで、[操作] ウィンドウの向きは横方向かどうか確認します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]  
  
4.  方向が水平方向の場合は、スタック操作ウィンドウ コントロールを左からそれ以外の場合、それらを上から積み重ねます。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]  
  
5.  C# でのイベント ハンドラーを追加する必要があります、`ActionsPane`を<xref:Microsoft.Office.Tools.Word.Document.Startup>イベント ハンドラー。 イベント ハンドラーの作成方法の詳細については、次を参照してください。[する方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)です。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]  
  
6.  プロジェクトを実行し、ドキュメントの上部にある [操作] ウィンドウがドッキングされているし、コントロールは、ドキュメントの右側にある [操作] ウィンドウがドッキングされているときに、上から下に積み上げられたときに、操作ウィンドウ コントロールは左から右へを積み上げことを確認してください。  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   Word ドキュメント レベルのプロジェクトで複数のユーザー コントロールが含まれる操作ウィンドウまたは入れ子になった [操作] ウィンドウを制御します。  
  
## <a name="see-also"></a>参照  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [方法: Word 文書や Excel ブックに操作ウィンドウを追加](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [方法: Word 文書や Excel ブックに操作ウィンドウを追加](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [チュートリアル: アクション ウィンドウから文書にテキストを挿入します。](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [チュートリアル: 操作ウィンドウから文書へのテキストの挿入](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  