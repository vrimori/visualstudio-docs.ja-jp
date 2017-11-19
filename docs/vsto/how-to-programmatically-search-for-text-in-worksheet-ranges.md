---
title: "方法: プログラムによってワークシートの範囲内のテキストの検索 |Microsoft ドキュメント"
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
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
ms.assetid: a6902711-fefb-450a-a76b-b1446d11c423
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 031894a3307a40af981ad974898ae819ba68d24a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>方法: プログラムによってワークシートの範囲内のテキストを検索する
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>のメソッド、<xref:Microsoft.Office.Interop.Excel.Range>オブジェクトでは、範囲内でテキストを検索することができます。 このテキストがなど、ワークシートのセルに表示される可能性がエラー文字列のいずれかに指定することできますも`#NULL!`または`#VALUE!`です。 エラー文字列の詳細については、次を参照してください。[セルのエラー値](http://msdn.microsoft.com/library/office/ff839168.aspx)です。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 次の例は、名前付き範囲を検索`Fruits`"apples"を含むセルのフォントを変更します。 このプロシージャで、<xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>メソッドで、事前に設定を使用して、検索の繰り返しを検索します。 検索するセルを指定して、<xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>メソッドは、残りの部分を処理します。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>範囲の末尾に達した後に、メソッドの検索が検索範囲の先頭に戻るラップします。 コードでは、ある検索周りで折り返されない無限ループを確認してください。 サンプル プロシージャを使用してこれを処理する方法を示しています、<xref:Microsoft.Office.Interop.Excel.Range.Address%2A>プロパティです。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。[操作方法: 使用 Find メソッド、Excel アドインで?](http://go.microsoft.com/fwlink/?LinkID=130294)です。  
  
### <a name="to-search-for-text-in-a-worksheet-range"></a>ワークシートの範囲内のテキストを検索するには  
  
1.  全体の範囲、最初に見つかった範囲、および現在の検索範囲を追跡するための変数を宣言します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2.  検索した後にあるセルを除くすべてのパラメーターを指定する、最初の一致を検索します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3.  検索の一致がある限り、続行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4.  最初に見つかった範囲を比較 (`firstFind`) に**Nothing**です。 場合`firstFind`見つかった範囲には値なし、休暇からコード ストアが含まれています (`currentFind`)。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5.  検索範囲のアドレスには、最初に見つかった範囲のアドレスが一致する場合は、ループを終了します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6.  検索範囲の外観を設定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7.  別の検索を実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
 このメソッドを使ったサンプル コード全体を次に示します。  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>関連項目  
 [範囲の使用](../vsto/working-with-ranges.md)   
 [方法: プログラムによってブック内の範囲にスタイルを適用](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [方法: プログラムによってワークシートの範囲をコード内を参照してください](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  