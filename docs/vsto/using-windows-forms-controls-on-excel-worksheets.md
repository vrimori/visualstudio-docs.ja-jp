---
title: Excel ワークシート上の Windows フォーム コントロールを使用します。
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd367087f48ababb390ddd87e289ec22258b4921
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767924"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Excel ワークシート上の Windows フォーム コントロールを使用します。
  Windows フォームにコントロールを追加することと同様に、Microsoft Office Excel ブックに Windows フォーム コントロールを追加できます。 ドキュメントのコントロールを使用した作業の概要については、次を参照してください。 [Office ドキュメントの概要 Windows フォームのコントロール](../vsto/windows-forms-controls-on-office-documents-overview.md)です。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Excel 用の管理の考慮事項  
 Excel に固有のいくつかの考慮事項があります。  
  
### <a name="match-control-size-to-cell-size"></a>セルのサイズに一致するコントロールのサイズ  
 親のセルのサイズが変更されたときに、自動的にサイズ変更されるようにコントロールを設定することができます。 詳細については、次を参照してください。[する方法: ワークシートのセル内のコントロールのサイズ変更](../vsto/how-to-resize-controls-within-worksheet-cells.md)です。  
  
### <a name="add-components-that-are-shared-by-all-worksheets"></a>すべてのワークシートで共有されるコンポーネントを追加します。  
 <xref:System.Data.DataSet>などすべてのワークシート間で共有するコンポーネントを、ワークシートではなくブックのデザイナーに追加することができます。 このコンポーネントは、コンポーネント トレイに表示されます。  
  
### <a name="formula-for-embedding-controls"></a>コントロールを埋め込むための数式  
 Excel 内でコントロールを選択すると、 **数式バー** に  " **=EMBED("WinForms.Control.Host","")**" と表示されます。 このテキストは必要なので、削除しないでください。  
  
## <a name="see-also"></a>関連項目  
 [方法: ワークシートのセル内のコントロールのサイズを変更します。](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [方法: 印刷時にワークシートのコントロールを非表示にします。](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [チュートリアル: CheckBox コントロールを使用してワークシートの書式を変更します。](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [チュートリアル: ボタンを使用してワークシート内のテキスト ボックスにテキストを表示します。](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [チュートリアル: オプション ボタンを使用してワークシートのグラフを更新します。](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  