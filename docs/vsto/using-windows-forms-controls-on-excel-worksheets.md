---
title: Excel ワークシート上で Windows フォーム コントロールを使用します。
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 144bcf1d9b0b96944e1493471106fe8aa6c8031b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871534"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Excel ワークシート上で Windows フォーム コントロールを使用します。
  Windows フォームにコントロールを追加することと同じ方法で、Microsoft Office Excel ブックへの Windows フォーム コントロールを追加できます。 概要ドキュメントのコントロールの操作については、次を参照してください。 [Windows フォーム コントロールの Office ドキュメントの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)します。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Excel 用の管理の考慮事項  
 Excel に固有のいくつかの考慮事項があります。  
  
### <a name="match-control-size-to-cell-size"></a>セルのサイズに一致するコントロールのサイズ  
 親のセルのサイズが変更されたときに、自動的にサイズ変更されるようにコントロールを設定することができます。 詳細については、「[方法 :ワークシートのセル内のコントロールをサイズ変更](../vsto/how-to-resize-controls-within-worksheet-cells.md)します。  
  
### <a name="add-components-that-are-shared-by-all-worksheets"></a>すべてのワークシートによって共有されるコンポーネントを追加します。  
 <xref:System.Data.DataSet>などすべてのワークシート間で共有するコンポーネントを、ワークシートではなくブックのデザイナーに追加することができます。 このコンポーネントは、コンポーネント トレイに表示されます。  
  
### <a name="formula-for-embedding-controls"></a>コントロールを埋め込むための数式  
 Excel 内でコントロールを選択すると、 **数式バー** に  " **=EMBED("WinForms.Control.Host","")**" と表示されます。 このテキストは必要なので、削除しないでください。  
  
## <a name="see-also"></a>関連項目  
 [方法: ワークシートのセル内のコントロールをサイズ変更します。](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [方法: 印刷時にワークシートのコントロールを非表示にします。](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [チュートリアル: CheckBox コントロールを使用してワークシートの書式設定を変更します。](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [チュートリアル: ボタンを使用してワークシート内のテキスト ボックスにテキストを表示](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [チュートリアル: ラジオ ボタンを使用してワークシートのグラフを更新します。](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
