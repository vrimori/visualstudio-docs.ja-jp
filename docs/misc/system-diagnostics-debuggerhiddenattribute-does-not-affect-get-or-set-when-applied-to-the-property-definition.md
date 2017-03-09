---
title: "System.Diagnostics.DebuggerHiddenAttribute は、プロパティ定義に適用するときに &#39;Get&#39; または &#39;Set&#39; に影響しません | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40051"
  - "vbc40051"
helpviewer_keywords: 
  - "BC40051"
ms.assetid: 623d5e48-7fb2-48a9-bbbb-92914b08c01c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.Diagnostics.DebuggerHiddenAttribute は、プロパティ定義に適用するときに &#39;Get&#39; または &#39;Set&#39; に影響しません
System.Diagnostics.DebuggerHiddenAttribute は、プロパティ定義に適用するときに 'Get' または 'Set' に影響しません。 必要に応じて、'Get' プロシージャと 'Set' プロシージャに直接属性を適用します。  
  
 <xref:System.Diagnostics.DebuggerHiddenAttribute> は、プロパティの宣言に適用されます。  
  
 ソース コードでは、<xref:System.Diagnostics.DebuggerHiddenAttribute> をプロシージャに適用できます。 これにより、Visual Studio デバッガーは、このプロシージャ内で停止したり、ブレークポイントをプロシージャ内に設定したりしないように指示されます。  
  
 <xref:System.Diagnostics.DebuggerHiddenAttribute> をプロパティに適用することはできますが、効果はありません。 プロパティの `Get` または `Set` プロシージャに適用する場合にのみ、必要な効果が得られます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」をご覧ください。  
  
 **エラー ID:** BC40051  
  
### このエラーを解決するには  
  
-   <xref:System.Diagnostics.DebuggerHiddenAttribute> をプロパティの宣言から削除するか、必要に応じてプロパティの `Get` または `Set` プロシージャに適用します。  
  
## 参照  
 <xref:System.Diagnostics.DebuggerHiddenAttribute>   
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)