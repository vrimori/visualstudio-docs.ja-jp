---
title: "方法: Word 文書または Excel ブックに操作ウィンドウを追加する"
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
ms.assetid: cea3c2b6-9364-4134-b812-50888ad8bd76
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# 方法: Word 文書または Excel ブックに操作ウィンドウを追加する
  Microsoft Office Word文書またはMicrosoft Excelブックに操作ウィンドウを追加するには、最初にWindowsフォーム ユーザー コントロールを作成します。  次に、`ThisDocument.ActionsPane` のフィールド \(Word\) またはプロジェクトの `ThisWorkbook.ActionsPane` のフィールド \(Excel\) の <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> のプロパティにユーザー コントロールを追加します。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## ユーザー コントロールの作成  
 次の手順では、WordまたはExcelプロジェクトのユーザー コントロールを作成する方法を示します。  さらに、ユーザー コントロールをクリックしたときに、文書またはブックにテキストが書き込まれるボタンを追加します。  
  
#### ユーザー コントロールを作成するには  
  
1.  Visual StudioでWordまたはExcelのドキュメント レベルのプロジェクトを開きます。  
  
2.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
3.  **\[新しい項目の追加\]** ダイアログ ボックスの **\[操作ウィンドウ コントロール\]** をクリックし、コントロールに **HelloControl** という名前を付けて **\[追加\]** をクリックします。  
  
    > [!NOTE]  
    >  プロジェクトに**ユーザー コントロール** アイテムを追加する方法もあります。  **操作ウィンドウ コントロール** アイテムおよび**ユーザー コントロール** アイテムによって生成されるクラスは、機能的には同じです。  
  
4.  **\[ツールボックス\]** の **\[Windows フォーム\]** タブから、**ボタン** コントロールをコントロールにドラッグします。  
  
    > [!NOTE]  
    >  **ソリューション エクスプローラー**でコントロールが非表示になっている場合は、デザイナーで **\[HelloControl\]** をダブルクリックします。  
  
5.  ボタンの <xref:System.Windows.Forms.Control.Click> のイベント ハンドラーにコードを追加します。  次の例では、Microsoft Office Wordのドキュメントのコードを次に示します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/HelloControl.vb#12)]  
  
6.  C\# では、ボタン クリックのイベント ハンドラーを追加する必要があります。  このコードは、`IntializeComponent` の呼び出しの後の `HelloControl` コンストラクターに追加できます。  
  
     イベント ハンドラーの作成方法については、「[方法: Office プロジェクトでイベント ハンドラーを作成する](../vsto/how-to-create-event-handlers-in-office-projects.md)」を参照してください。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#13)]  
  
## 操作ウィンドウへのユーザー コントロールの追加  
 操作ウィンドウを表示するには、`ThisDocument.ActionsPane` のフィールド \(Word\) または \(Excel `ThisWorkbook.ActionsPane` のフィールド\) の <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> のプロパティにユーザー コントロールを追加します。  
  
#### 操作ウィンドウにユーザー コントロールを追加するには  
  
1.  クラス レベルの宣言として `ThisDocument` または `ThisWorkbook` のクラスに次のコードを追加します \(このコードをメソッドに追加しないでください\)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#14)]  
  
2.  `ThisDocument` クラスの `ThisDocument_Startup` のイベント ハンドラーまたは `ThisWorkbook` クラスの `ThisWorkbook_Startup` のイベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#15)]  
  
## 参照  
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [チュートリアル : 操作ウィンドウから文書へのテキストの挿入](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [方法 : アクション ペイン上のコントロールのレイアウトを管理する](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [チュートリアル : 操作ウィンドウから文書へのテキストの挿入](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  