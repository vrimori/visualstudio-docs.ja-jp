---
title: "方法: プログラムによってワークシートの範囲内のテキストを検索する"
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
  - "テキスト [Visual Studio での Office 開発], 検索 (ワークシートで)"
  - "テキスト検索, ワークシート"
  - "ワークシート, 検索"
ms.assetid: a6902711-fefb-450a-a76b-b1446d11c423
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# 方法: プログラムによってワークシートの範囲内のテキストを検索する
  <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトの <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> メソッドを使用すると、範囲内のテキストを検索できます。  このテキストは、ワークシートのセルに表示できるエラー文字列にすることもできます \(`#NULL!` や `#VALUE!`\)。  エラー文字列の詳細については、「[Cell Error Values](HV10038459)」を参照してください。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 以下の例では、"`Fruits`" という名前の範囲を検索し、単語 "apples" が含まれているセルのフォントを変更します。  このプロシージャでは、<xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> メソッドも使用して、以前に設定された検索設定を利用して検索を繰り返します。  検索対象の後にあるセルを指定して、<xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> メソッドで残りのセルを処理します。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> メソッドによる検索は、検索処理が検索範囲の末尾に達すると、検索範囲の先頭に戻ります。  コードでは、検索処理が無限ループにならないようにする必要があります。  サンプル プロシージャでは、その方法の 1 つとして、<xref:Microsoft.Office.Interop.Excel.Range.Address%2A> プロパティを使用する方法を示します。  
  
 ![ビデオへのリンク](~/data-tools/media/playvideo.gif "ビデオへのリンク") 関連のビデオ デモについては、「[How Do I: Use the Find Method in an Excel Add\-in? \(操作方法: Excel アドインで Find メソッドを使用する\)](http://go.microsoft.com/fwlink/?LinkID=130294)」を参照してください。  
  
### ワークシートの範囲内のテキストを検索するには  
  
1.  範囲全体、最初に一致した検索範囲、および現在一致している検索範囲を追跡する変数を宣言します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#58)]  
  
2.  検索対象の直前のセル以外のすべてのパラメーターを指定して、最初の一致を検索します  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#59)]  
  
3.  すべての一致が見つかるまで、検索を継続します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#60)]  
  
4.  最初に見つかった範囲 \(`firstFind`\) と **Nothing** を比較します。  `firstFind` に値が含まれていない場合、コードは、見つかった範囲 \(`currentFind`\) を格納します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#61)]  
  
5.  見つかった範囲のアドレスが最初に見つかった範囲のアドレスと一致すると、ループを終了します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#62)]  
  
6.  見つかった範囲の表示書式を設定します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#63)]  
  
7.  次の検索を実行します。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#64)]  
  
 このメソッドの完全なコードは次のようになります。  
  
## 使用例  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#57)]  
  
## 参照  
 [範囲の使用](../vsto/working-with-ranges.md)   
 [方法: プログラムによってブック内の範囲にスタイルを適用する](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [方法: プログラムによってコード内でワークシートの範囲を参照する](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  