---
title: "方法: プログラムによって Word の組み込みダイアログ ボックスを使用する"
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
  - "Word [Visual Studio での Office 開発]、ダイアログ ボックス"
  - "ダイアログ ボックス、Word"
ms.assetid: 0c7e4338-dead-4444-868b-3b0212368455
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 方法: プログラムによって Word の組み込みダイアログ ボックスを使用する
  Microsoft Office Word の使用時に、ユーザー入力用のダイアログ ボックスを表示する必要があることがあります。  独自のダイアログ ボックスを作成することもできますが、Word の組み込みダイアログ ボックスを使用することもできます。Word の組み込みダイアログ ボックスは、<xref:Microsoft.Office.Interop.Word.Application> オブジェクトの <xref:Microsoft.Office.Interop.Word.Dialogs> コレクションで公開されています。  この方法を利用すると、列挙体で表される 200 以上の組み込みダイアログ ボックスにアクセスできます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## ダイアログ ボックスの表示  
 ダイアログ ボックスを表示するには、<xref:Microsoft.Office.Interop.Word.WdWordDialog> 列挙体の値のいずれかを使用して、表示するダイアログ ボックスを表す <xref:Microsoft.Office.Interop.Word.Dialog> オブジェクトを作成します。  次に、<xref:Microsoft.Office.Interop.Word.Dialog> オブジェクトの <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> メソッドを呼び出します。  
  
 **\[ファイルを開く\]** ダイアログ ボックスの表示方法を次のコード例に示します。  このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスから実行します。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#100](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreWordAutomation#100](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#100)]  
  
### 遅延バインディングを介して使用できるダイアログ ボックス メンバーへのアクセス  
 Word のダイアログ ボックスの一部のプロパティとメソッドは、遅延バインディングを介してのみ使用できます。  Visual Basic では **Option Strict** がどこにあるか、リフレクションをこれらのメンバーにアクセスする必要があります。  詳細については、「[Office ソリューションの遅延バインディング](../vsto/late-binding-in-office-solutions.md)」を参照してください。  
  
 次のコード例では、がオフ **Option Strict** がいるか、または [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)][!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]を対象とする Visual C\# での Visual Basic プロジェクトで **\[ファイルを開く\]** のダイアログ ボックスの **Name** のプロパティを使用する方法を示します。  このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスから実行します。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 次のコード例に **Option Strict** がオンの Visual Basic プロジェクトの **\[ファイルを開く\]** のダイアログ ボックスの **Name** のプロパティにアクセスするにはリフレクションを使用する方法を示します。  このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスから実行します。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## 参照  
 [方法: プログラムによって Word のダイアログ ボックスを非表示モードで使用する](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [リフレクション &#40;C&#35; および Visual Basic&#41;](../Topic/Reflection%20(C%23%20and%20Visual%20Basic).md)  
  
  