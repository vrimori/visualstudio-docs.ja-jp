---
title: "方法 : カスタム作業ウィンドウをアプリケーションに追加する"
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
  - "カスタム作業ウィンドウ [Visual Studio での Office 開発], 追加 (アプリケーションに)"
  - "作業ウィンドウ [Visual Studio での Office 開発], 追加 (アプリケーションに)"
ms.assetid: 67b4ed5b-d77e-4630-b851-34bb25bdc9b3
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 方法 : カスタム作業ウィンドウをアプリケーションに追加する
  VSTO アドインを使用して、上記にリストしたアプリケーションにカスタム作業ウィンドウを追加できます。  詳細については、「[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)」を参照してください。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## カスタム作業ウィンドウをアプリケーションに追加する  
  
#### カスタム作業ウィンドウをアプリケーションに追加するには  
  
1.  上記のアプリケーションのいずれかの VSTO アドイン プロジェクトを開くか、作成します。  詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
2.  **\[プロジェクト\]** メニューの **\[ユーザー コントロールの追加\]** をクリックします。  
  
3.  **\[新しい項目の追加\]** ダイアログ ボックスで新しいユーザー コントロールの名前を **MyUserControl** に変更し、**\[追加\]** をクリックします。  
  
     ユーザー コントロールがデザイナーで開きます。  
  
4.  **\[ツールボックス\]** の 1 つまたは複数の Windows フォーム コントロールをユーザー コントロールに追加します。  
  
5.  **ThisAddIn.cs** または **ThisAddIn.vb** コード ファイルを開きます。  
  
6.  `ThisAddIn` クラスに次のコードを追加します。  このコードは `MyUserControl` と <xref:Microsoft.Office.Tools.CustomTaskPane> のインスタンスを `ThisAddIn` クラスのメンバーとして宣言します。  
  
     [!code-csharp[Trin_TaskPaneBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#1)]  
  
7.  `ThisAddIn_Startup` イベント ハンドラーに次のコードを追加します。  このコードは `MyUserControl` オブジェクトを `CustomTaskPanes` コレクションに追加することにより、新しい <xref:Microsoft.Office.Tools.CustomTaskPane> を作成します。  コードでは、作業ウィンドウも表示されます。  
  
     [!code-csharp[Trin_TaskPaneBasic#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneBasic#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#2)]  
  
    > [!NOTE]  
    >  このコードは、カスタム作業ウィンドウをアプリケーションのアクティブ ウィンドウに関連付けます。  一部のアプリケーションでは、他のドキュメントやアプリケーションのアイテムで作業ウィンドウが表示されるように、このコードを変更する場合があります。  詳細については、「[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)」を参照してください。  
  
## 参照  
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [カスタム作業ウィンドウ](../vsto/custom-task-panes.md)   
 [チュートリアル : カスタム作業ウィンドウからのアプリケーションの自動化](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
  
  