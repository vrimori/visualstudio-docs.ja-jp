---
title: "Office ソリューションの遅延バインディング"
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
  - "オブジェクト [Visual Studio での Office 開発]、キャスト"
  - "型 [Visual Studio での Office 開発]、キャスト"
  - "オートメーション [Visual Studio での Office 開発]、オブジェクトのキャスト"
  - "キャスト、オブジェクトを特定の型に"
ms.assetid: 80b0d23e-df68-4ea9-a02b-238aee8ca9c0
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Office ソリューションの遅延バインディング
  Office アプリケーションのオブジェクト モデルの一部の型には、遅延バインディング機能を通じて使用できる機能があります。  たとえば、一部のメソッドおよびプロパティは、Office アプリケーションのコンテキストに応じて異なるオブジェクトの型を返すことができ、一部の型は異なるコンテキストで異なるメソッドまたはプロパティを公開できます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual Basic は **Option Strict** が消え、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] を対象としている場合、または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] がこれらの遅延バインディング機能を持つ型を直接使用できる Visual C\# プロジェクトまたはプロジェクトが。  
  
## オブジェクト戻り値の暗黙的および明示的なキャスト  
 Microsoft Office プライマリ相互運用機能アセンブリ \(PIA: Primary Interop Assembly\) の多くのメソッドとプロパティは、いくつかの異なる型のオブジェクトを返すことができるため、<xref:System.Object> 値を返します。  たとえば、<xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> プロパティは、作業中のシートが何であるかに応じて戻り値が <xref:Microsoft.Office.Interop.Excel.Worksheet> オブジェクトまたは <xref:Microsoft.Office.Interop.Excel.Chart> オブジェクトになるため、<xref:System.Object> を返します。  
  
 メソッドまたはプロパティが <xref:System.Object>を返すと、入力します **Option Strict** がオンの Visual Basic プロジェクトを明示的に \(Visual Basic では\) を適切なにオブジェクトを変換する必要があります。  **Option Strict** がオフの Visual Basic プロジェクトの <xref:System.Object> の戻り値を明示的にキャストする必要はありません。  
  
 ほとんどの場合、<xref:System.Object> を返すメンバーの戻り値として使用できる型の一覧は、リファレンス ドキュメントに記載されています。  オブジェクトを変換またはキャストすると、コード エディターでオブジェクトに対する IntelliSense が有効になります。  
  
 Visual Basic での変換については、「[Implicit and Explicit Conversions &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)」および「[CType 関数 &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function)」を参照してください。  
  
### 例  
 次のコード例では、特定のオブジェクトをキャストする方法も示します **Option Strict** がオンの Visual Basic プロジェクトを示します。  この種類のプロジェクトでは、<xref:Microsoft.Office.Interop.Excel.Range>に明示的に <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> のプロパティをキャストする必要があります。  この例では、`Sheet1` という名前のワークシート クラスを持つドキュメント レベルの Excel プロジェクトが必要です。  
  
 [!code-vb[Trin_VstcoreProgramming#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#9)]  
  
 次のコード例では、**Option Strict** がオフの Visual Basic プロジェクトまたは [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] を対象とする Visual C\# プロジェクトで、オブジェクトを特定の型に暗黙的にキャストする方法を示します。  これらのプロジェクトの種類では、<xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> プロパティが <xref:Microsoft.Office.Interop.Excel.Range> に暗黙にキャストされます。  この例では、`Sheet1` という名前のワークシート クラスを持つドキュメント レベルの Excel プロジェクトが必要です。  
  
 [!code-csharp[Trin_VstcoreProgramming#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#10)]
 [!code-vb[Trin_VstcoreProgramming#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#10)]  
  
## 遅延バインディングを介してのみ使用できるメンバーへのアクセス  
 Office PIA の一部のプロパティおよびメソッドは、遅延バインディングを介してのみ使用できます。  Visual Basic で遅延バインディング メンバーにアクセスするには **Option Strict** がどこからからこれらの言語で [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] いるか、または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]を対象とする Visual C\# で、遅延バインディング機能を使用できるプロジェクトまたはプロジェクト。  Visual Basic では **Option Strict** がどこにあるか、リフレクションをこれらのメンバーにアクセスする必要があります。  
  
### 例  
 次のコード例では、**Option Strict** がオフの Visual Basic プロジェクトまたは [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] を対象とする Visual C\# プロジェクトで、遅延バインディングされたメンバーにアクセスする方法を示します。  この例では、Word の **\[ファイルを開く\]** ダイアログ ボックスの遅延バインディングされた **Name** プロパティにアクセスします。  このコード例を使用するには、Word プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスから実行します。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 次のコード例に **Option Strict** がオンの Visual Basic プロジェクトで同じタスクを実行するためにリフレクションを使用する方法を示します。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## 参照  
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [dynamic 型の使用 &#40;C&#35; プログラミング ガイド&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [リフレクション &#40;C&#35; および Visual Basic&#41;](../Topic/Reflection%20(C%23%20and%20Visual%20Basic).md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)  
  
  