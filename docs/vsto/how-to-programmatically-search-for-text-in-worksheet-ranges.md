---
title: '方法: プログラムによってワークシートの範囲内のテキストを検索します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 37f59f2888fc5a572029f4c21116281df008706e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868590"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>方法: プログラムによってワークシートの範囲内のテキストを検索します。
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>のメソッド、<xref:Microsoft.Office.Interop.Excel.Range>オブジェクトでは、範囲内でテキストを検索することができます。 このテキストのエラー文字列など、ワークシートのセルに表示されることができますを指定できますも`#NULL!`または`#VALUE!`します。 エラー文字列の詳細については、次を参照してください。[エラー値をセル](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values)します。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 次の例では、名前付き範囲を検索する`Fruits`"apples"という単語を含むセルのフォントを変更します。 このプロシージャで、<xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>メソッドは、事前に設定を使用して検索を繰り返すの設定を検索します。 検索するセルを指定して、<xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>メソッドがすべて引き受けてくれます。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>範囲の末尾に達した後、検索範囲の先頭に戻ってメソッドの検索をラップします。 コードは必要があります、検索が無限ループに入るをラップしないことを確認します。 サンプル プロシージャを使用してこれを処理する 1 つの方法を示しています、<xref:Microsoft.Office.Interop.Excel.Range.Address%2A>プロパティ。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください[How do i:。Excel アドインでは、Find メソッドを使用しますか。](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
## <a name="to-search-for-text-in-a-worksheet-range"></a>ワークシートの範囲内のテキストを検索するには  
  
1. 全体の範囲、最初に見つかった範囲、および現在の検索範囲を追跡するための変数を宣言します。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2. 検索した後にあるセルを除くすべてのパラメーターを指定する、最初の一致を検索します。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3. 一致がある限りの検索を続行します。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4. 最初に見つかった範囲を比較 (`firstFind`) に**Nothing**します。 場合`firstFind`検索範囲には値なし。 すぐにコード ストアが含まれています (`currentFind`)。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5. 検索範囲のアドレスが最初に見つかった範囲のアドレスと一致する場合は、ループを終了します。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6. 検索範囲の外観を設定します。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7. 別の検索を実行します。  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
   このメソッドを使ったサンプル コード全体を次に示します。  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>関連項目  
 [範囲を操作します。](../vsto/working-with-ranges.md)   
 [方法: プログラムによってブック内の範囲にスタイルを適用します。](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [方法: コード内でワークシートの範囲をプログラムで参照してください。](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
