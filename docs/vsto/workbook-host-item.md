---
title: Workbook ホスト項目
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel workbooks
- Workbook host items
- host items [Office development in Visual Studio], Workbook
- workbooks, Excel
- Workbook host items, events
- workbooks
- Excel [Office development in Visual Studio], workbooks
- workbooks, events
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f15d93818c2db553d22d9639e6460f6637d33c80
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952888"
---
# <a name="workbook-host-item"></a>Workbook ホスト項目
  <xref:Microsoft.Office.Tools.Excel.Workbook> ホスト項目は、Excel のプライマリ相互運用機能アセンブリの <xref:Microsoft.Office.Interop.Excel.Workbook> 型を拡張する型です。 <xref:Microsoft.Office.Tools.Excel.Workbook> ホスト項目は <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトと同じプロパティ、メソッド、イベントがすべて用意されているだけなく、追加の機能も用意されています。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ドキュメント レベルのプロジェクトには、プロジェクト内のブックを表す既定の <xref:Microsoft.Office.Tools.Excel.Workbook> ホスト項目があります。 VSTO アドイン プロジェクトで生成できる<xref:Microsoft.Office.Tools.Excel.Workbook>実行時に項目をホストします。  
  
## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>ドキュメント レベルのプロジェクトでの workbook ホスト項目を理解します。  
 プロジェクトのブックにアクセスするには、 `ThisWorkbook` クラスを使用します。 `ThisWorkbook` クラスによって、 <xref:Microsoft.Office.Tools.Excel.Workbook> ホスト項目のメンバーにアクセスし、ブックが開かれたり閉じられたりしたときにコードを実行するなど、カスタマイズの基本的なタスクを実行できます。 詳細については、次を参照してください。[ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)します。  
  
 `ThisWorkbook` クラスには、プロジェクトでコードの記述を開始できる場所が用意されています。 このクラスには、Excel のプライマリ相互運用機能アセンブリの <xref:Microsoft.Office.Interop.Excel.Workbook> オブジェクトと同じプロパティ、メソッド、イベントがすべて用意されているため、 `ThisWorkbook` を使用して Excel のオブジェクト モデルにアクセスすることもできます。 詳細については、次の [Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)を参照してください。  
  
 **[ソリューション エクスプローラー]** で **ThisWorkbook** プロジェクト項目をダブルクリックすると、ブックのデザイナーが表示され、 **[プロパティ]** ウィンドウにブックのプロパティとイベントが表示されます。  
  
### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>ドキュメント レベルのプロジェクトでの workbook ホスト項目の制限事項  
 ドキュメント レベルのプロジェクトには、1 つの <xref:Microsoft.Office.Tools.Excel.Workbook> ホスト項目のみ (つまり `ThisWorkbook` クラス) を含めることができます。 新規に追加することはできません<xref:Microsoft.Office.Tools.Excel.Workbook>、デザイン時に項目をプロジェクトにホストし、新規に作成することはできません<xref:Microsoft.Office.Tools.Excel.Workbook>時にドキュメント レベルのカスタマイズから項目をホストします。  
  
 実行時に、新しい Excel ブックを作成する場合、型のことが<xref:Microsoft.Office.Interop.Excel.Workbook>します。 これはホスト項目ではないため、ホスト コントロールや Windows フォーム コントロールを含めることはできません。 実行時にブックを作成する方法の詳細については、次を参照してください。[方法。新しいブックをプログラムで作成](../vsto/how-to-programmatically-create-new-workbooks.md)です。  
  
 <xref:Microsoft.Office.Tools.Excel.Workbook> ホスト項目は、ホスト コントロールのコンテナーとしては機能しません。 そのため、表示されるコントロールをブックに追加することはできませんが、 <xref:System.Data.DataSet>などのコンポーネントを追加すると、すべてのワークシートでそのコンポーネントを共有できます。 ドキュメント レベルのプロジェクトでは、ブックで使用できるコンポーネントは、 **[ツールボックス]** の **[コンポーネント]** タブ、 **[データ]** タブ、 **[すべての Windows フォーム]** タブに表示されます。  
  
> [!NOTE]  
>  Visual Studio の Office 開発ツールでは、共有ブックはサポートされません。  
  
## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>VSTO アドイン プロジェクトでのブック ホスト項目を理解します。  
 VSTO アドイン プロジェクトで生成することができます、<xref:Microsoft.Office.Tools.Excel.Workbook>は Excel で開いているすべてのブックの実行時にホスト項目。 <xref:Microsoft.Office.Tools.Excel.Workbook> ホスト項目を生成するには、`GetVstoObject` メソッドを使用します。 詳細については、次を参照してください。[拡張 Word 文書や Excel ブックを実行時に VSTO アドインで](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [Word 文書と Excel ブックを実行時に VSTO アドインで拡張します。](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [拡張オブジェクトを使用して Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
