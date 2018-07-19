---
title: '方法: プログラムによって自動的に増分するデータ範囲を入力'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a4fff7eb59ff2fe5e17ddf500bf546502492634d
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256404"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>方法: プログラムによって自動的に増分するデータ範囲を入力
  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>のメソッド、<xref:Microsoft.Office.Interop.Excel.Range>オブジェクトでは、値を含むワークシートで範囲を自動的に入力することができます。 ほとんどの場合、<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>メソッドは、段階的増加または減少する範囲の値の格納に使用されます。 任意の定数を指定して、動作を指定することができます、<xref:Microsoft.Office.Interop.Excel.XlAutoFillType>列挙体。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 使用する場合は、2 つの範囲を指定する必要があります<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:  
  
-   呼び出す範囲、<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>メソッドでは、塗りつぶしの開始位置を指定し、初期値が含まれています。  
  
-   パラメーターとして渡される範囲を入力する、<xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>メソッド。 この変換先の範囲は、初期値を含む範囲を含める必要があります。  
  
    > [!NOTE]  
    >  渡すことはできません、<xref:Microsoft.Office.Tools.Excel.NamedRange>制御の代わりに、<xref:Microsoft.Office.Interop.Excel.Range>します。 詳細については、次を参照してください。[ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)します。  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]  
  
## <a name="compile-the-code"></a>コードをコンパイルします  
 格納する範囲の最初のセルには、初期値を含める必要があります。  
  
 この例では、3 つのリージョンを入力することが必要です。  
  
-   列 B には 5 つまでの平日を含めます。 初期値に「**月曜日**セル B1 にします。  
  
-   列 C には 5 か月が含まれます。 初期値に「**年 1 月**セル C1 にします。  
  
-   列 D では、一連の数字、行ごとに 2 つずつインクリメントされます。 初期値として、入力**4** D1 のセルと**6**セル D2 にします。  
  
## <a name="see-also"></a>関連項目  
 [範囲を操作します。](../vsto/working-with-ranges.md)   
 [方法: プログラムによってコード内でワークシートの範囲を参照](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [方法: プログラムによってブック内の範囲にスタイルを適用](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [方法: プログラムによって Excel の計算を実行](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  