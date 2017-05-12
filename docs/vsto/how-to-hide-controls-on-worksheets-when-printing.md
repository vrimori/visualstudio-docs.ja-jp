---
title: "方法 : 印刷時にワークシートのコントロールを非表示にする"
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
  - "コントロール [Visual Studio での Office 開発], 非表示 (出力中は)"
  - "印刷 [Visual Studio での Office 開発], 非表示 (コントロールを)"
  - "印刷 [Visual Studio での Office 開発], ワークシート"
  - "ワークシート, 非表示 (出力時コントロールを)"
ms.assetid: a637fe9a-9de1-4162-8ff6-fe28ccd62389
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# 方法 : 印刷時にワークシートのコントロールを非表示にする
  Windows フォーム コントロールが含まれる Microsoft Office Excel ドキュメントを印刷すると、コントロールが表示されたワークシートが印刷されます。  ワークシートの印刷時にコントロールを非表示にすることができます。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> など、データを表示するコントロールを非表示にすると、印刷されたワークシートではそのコントロール内のデータが表示されなくなります。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### ワークシートの印刷時にコントロールを非表示にするには  
  
1.  Visual Studio で Excel プロジェクトを作成するか開いて、デザイナーに **\[Sheet1\]** が表示されることを確認します。  プロジェクトの作成の詳細については、「[方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)」を参照してください。  
  
2.  **\[ツールボックス\]** の **\[コモン コントロール\]** タブから <xref:Microsoft.Office.Tools.Excel.Controls.Button> コントロールを `Sheet1` のセルへドラッグします。  
  
3.  **\[プロパティ\]** ウィンドウで、<xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> プロパティを **False** に設定します。  
  
## 参照  
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [Office ドキュメントでの Windows フォーム コントロールの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [方法 : Office ドキュメントに Windows フォーム コントロールを追加する](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [方法 : ワークシートのセル内のコントロールをサイズ変更する](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  