---
title: "Windows フォームの使用上の Excel ワークシートのコントロール |Microsoft ドキュメント"
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
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
ms.assetid: bbda7461-0d69-4b56-8ba3-418d63ba49db
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3d80158853ec042b98f7e40feda70520af55ed32
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-windows-forms-controls-on-excel-worksheets"></a>Excel ワークシート上での Windows フォーム コントロールの使用
  Windows フォームにコントロールを追加することと同様に、Microsoft Office Excel ブックに Windows フォーム コントロールを追加できます。 ドキュメントのコントロールを使用した作業の概要については、次を参照してください。 [Office ドキュメントの概要での Windows フォーム コントロール](../vsto/windows-forms-controls-on-office-documents-overview.md)です。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Excel 用の管理の考慮事項  
 Excel に固有のいくつかの考慮事項があります。  
  
### <a name="matching-control-size-to-cell-size"></a>セルのサイズに一致するコントロールのサイズ  
 親のセルのサイズが変更されたときに、自動的にサイズ変更されるようにコントロールを設定することができます。 詳細については、次を参照してください。[する方法: ワークシート セル内でコントロールのサイズを変更する](../vsto/how-to-resize-controls-within-worksheet-cells.md)です。  
  
### <a name="adding-components-that-are-shared-by-all-worksheets"></a>すべてのワークシートによって共有されるコンポーネントの追加  
 <xref:System.Data.DataSet>などすべてのワークシート間で共有するコンポーネントを、ワークシートではなくブックのデザイナーに追加することができます。 このコンポーネントは、コンポーネント トレイに表示されます。  
  
### <a name="formula-for-embedding-controls"></a>コントロールを埋め込むための数式  
 Excel 内でコントロールを選択すると、 **数式バー** に  " **=EMBED("WinForms.Control.Host","")**" と表示されます。 このテキストは必要なので、削除しないでください。  
  
## <a name="see-also"></a>参照  
 [方法: ワークシートのセル内のコントロールのサイズを変更します。](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [方法: 印刷時にワークシートのコントロールを非表示にします。](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [チュートリアル: CheckBox コントロールを使用してワークシートの書式設定の変更](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [チュートリアル: ボタンを使用してワークシート内のテキスト ボックスにテキストを表示します。](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [チュートリアル: オプション ボタンを使用してワークシートのグラフを更新する方法](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  