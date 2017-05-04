---
title: "方法 : アクション ペイン上のコントロールのレイアウトを管理する | Microsoft Docs"
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
  - "操作ウィンドウ [Visual Studio での Office 開発], コントロールのレイアウト"
  - "コントロール [Visual Studio での Office 開発], レイアウト (操作ウィンドウでの)"
  - "スマート ドキュメント [Visual Studio での Office 開発], コントロールのレイアウト"
ms.assetid: 857550d0-b9c0-4d2f-a947-dd955bcf2823
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# 方法 : アクション ペイン上のコントロールのレイアウトを管理する
  既定では、操作ウィンドウはドキュメントまたはワークシートの右側にドッキングされますが、左側、上部、または下部にドッキングすることもできます。  複数のユーザー コントロールを使用する場合、ユーザー コントロールが操作ウィンドウ上で正しくスタックされるようにコードを作成できます。  詳細については、「[操作ウィンドウの概要](../vsto/actions-pane-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 コントロールのスタック順は、操作ウィンドウが垂直方向にドッキングされているか水平方向にドッキングされているかで異なります。  
  
> [!NOTE]  
>  ユーザーが実行時に操作ウィンドウのサイズを変更した場合、操作ウィンドウに合わせてコントロールのサイズも変更するように設定できます。  Windows フォーム コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティを使用すると、コントロールを操作ウィンドウに固定できます。  詳細については、「[方法 : Windows フォームにコントロールを固定する](../Topic/How%20to:%20Anchor%20Controls%20on%20Windows%20Forms.md)」を参照してください。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### 操作ウィンドウ コントロールのスタック順を設定するには  
  
1.  複数のユーザー コントロールまたは入れ子になった操作ウィンドウ コントロールが含まれる操作ウィンドウを使用した、Microsoft Office Word 用のドキュメント レベルのプロジェクトを開きます。  詳細については、「[方法: Word 文書または Excel ブックに操作ウィンドウを追加する](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)」を参照してください。  
  
2.  **ソリューション エクスプローラー**で **ThisDocument.cs** または **ThisDocument.vb** を右クリックし、**\[コードの表示\]** をクリックします。  
  
3.  操作ウィンドウ の <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> イベント ハンドラーで、操作ウィンドウが水平方向に配置されているかどうかをチェックします。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#30)]  
  
4.  水平方向に配置されている場合は、操作ウィンドウ コントロールを左からスタックします。水平方向ではない場合は、上からスタックします。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#31)]  
  
5.  C\# では、`ActionsPane` のイベント ハンドラーを <xref:Microsoft.Office.Tools.Word.Document.Startup> イベント ハンドラーに追加する必要があります。  イベンド ハンドラーの作成方法の詳細については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」を参照してください。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#32)]  
  
6.  プロジェクトを実行して、操作ウィンドウがドキュメントの上部にドッキングされている場合には操作ウィンドウ コントロールが左から右へ、操作ウィンドウがドキュメントの右側にドッキングされている場合にはコントロールが上から下へスタックされることを確認します。  
  
## 使用例  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#29)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   複数のユーザー コントロールまたは入れ子になった操作ウィンドウ コントロールが含まれる操作ウィンドウを使用した Word 用のドキュメント レベルのプロジェクト  
  
## 参照  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [方法: Word 文書または Excel ブックに操作ウィンドウを追加する](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [方法: Word 文書または Excel ブックに操作ウィンドウを追加する](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [チュートリアル : 操作ウィンドウから文書へのテキストの挿入](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [チュートリアル : 操作ウィンドウから文書へのテキストの挿入](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  