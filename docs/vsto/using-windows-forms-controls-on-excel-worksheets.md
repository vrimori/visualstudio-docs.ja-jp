---
title: "Excel ワークシート上での Windows フォーム コントロールの使用"
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
  - "コントロール [Visual Studio での Office 開発], Windows フォーム コントロール"
  - "Excel [Visual Studio での Office 開発], Windows フォーム コントロール"
  - "Windows フォーム コントロール [Visual Studio での Office 開発], Excel"
ms.assetid: bbda7461-0d69-4b56-8ba3-418d63ba49db
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Excel ワークシート上での Windows フォーム コントロールの使用
  Windows フォーム コントロールは、Windows フォームにコントロールを追加するのと同じように、Microsoft Office Excel ブックに追加できます。  文書上でのコントロールの操作の詳細については、「[Office ドキュメントでの Windows フォーム コントロールの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)」を参照してください。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Excel のコントロールに関する考慮事項  
 Excel を使用する場合に考慮する必要のある事項を次に示します。  
  
### コントロール サイズとセル サイズの一致  
 親セルのサイズが変更されたときにコントロールのサイズが自動的に変更されるように設定できます。  詳細については、「[方法 : ワークシートのセル内のコントロールをサイズ変更する](../vsto/how-to-resize-controls-within-worksheet-cells.md)」を参照してください。  
  
### すべてのワークシートで共有するコンポーネントの追加  
 <xref:System.Data.DataSet> など、すべてのワークシートで共有するコンポーネントをワークシートではなくブックのデザイナーに追加できます。  追加したコンポーネントはコンポーネント トレイに表示されます。  
  
### コントロールを埋め込むための数式  
 Excel 内でコントロールを選択すると、数式バーに "\=EMBED\("WinForms.Control.Host",""\)" と表示されます。  このテキストは必要なので、削除しないでください。  
  
## 参照  
 [方法 : ワークシートのセル内のコントロールをサイズ変更する](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [方法 : 印刷時にワークシートのコントロールを非表示にする](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [チュートリアル : CheckBox コントロールを使用したワークシート書式の変更](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [チュートリアル : ボタンを使用してワークシート内テキスト ボックスにテキストを表示する方法](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [チュートリアル : オプション ボタンを使用してワークシートのグラフを更新する方法](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  