---
title: "方法: ListObject コントロールに新しい行が追加されたときにデータの検証 |Microsoft ドキュメント"
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
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
ms.assetid: 107bce92-e5ef-40be-8c05-cd6861d39d75
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 87ba8bc1d81dbce4609fcc349337c3f86de50f2d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>方法 : ListObject コントロールに新規行が追加された場合にデータを検証する
  ユーザーはデータにバインドされている <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールに新しい行を追加できます。 変更をデータ ソースにコミットする前に、ユーザーのデータを検証できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="data-validation"></a>データの検証  
 データにバインドされている <xref:Microsoft.Office.Tools.Excel.ListObject> に行が追加されるたびに、 <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> イベントが発生します。 このイベントを処理することで、データの検証を実行できます。 たとえば、アプリケーションでデータ ソースに 18 ～ 65 歳の従業員のみを追加できるようにする必要がある場合、行が追加される前に、入力された年齢がその範囲内であることを検証できます。  
  
> [!NOTE]  
>  常に、クライアントだけでなく、サーバー上のユーザー入力も確認する必要があります。 詳細については、次を参照してください。[クライアント アプリケーションのセキュリティで保護された](/dotnet/framework/data/adonet/secure-client-applications)です。  
  
#### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>データ バインドされた ListObject に新規行が追加された場合にデータを検証するには  
  
1.  クラス レベルで ID および <xref:System.Data.DataTable> の変数を作成します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]  
  
2.  新しい <xref:System.Data.DataTable> を作成し、 `Startup` クラス (ドキュメント レベル プロジェクトの場合) または `Sheet1` クラス (VSTO アドイン プロジェクトの場合) の `ThisAddIn` イベント ハンドラーにサンプルの列とデータを追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]  
  
3.  `list1_BeforeAddDataBoundRow` イベント ハンドラーに、入力された年齢が許容範囲内であるかどうかを確認するコードを追加します。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコード例では、このコードがあるワークシートに、 <xref:Microsoft.Office.Tools.Excel.ListObject> という名前の既存の `list1` があることを前提としています。  
  
## <a name="see-also"></a>参照  
 [実行時の Word 文書と VSTO アドイン内の Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject コントロール](../vsto/listobject-control.md)   
 [拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)   
 [方法: データに ListObject 列を割り当てる](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  