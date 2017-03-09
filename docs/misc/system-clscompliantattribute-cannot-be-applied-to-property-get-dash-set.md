---
title: "System.CLSCompliantAttribute はプロパティ &#39;Get&#39; または &#39;Set&#39; に適用できません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40043"
  - "BC40043"
helpviewer_keywords: 
  - "BC40043"
ms.assetid: 2ff45c09-32be-4ca9-b42a-63ce2536db7d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.CLSCompliantAttribute はプロパティ &#39;Get&#39; または &#39;Set&#39; に適用できません
プロパティ定義は、<xref:System.CLSCompliantAttribute> 属性を `Get` ステートメントまたは `Set` ステートメントに適用します。  
  
 プロパティが [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) に準拠するためには、プロパティ全体が `<CLSCompliant(True)>` としてマークされる必要があります。<xref:System.CLSCompliantAttribute> は、`Get` ステートメントや `Set` ステートメントではなく、[Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement) ステートメントに適用する必要があります。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40043  
  
### このエラーを解決するには  
  
-   `Get` ステートメントまたは `Set` ステートメントから <xref:System.CLSCompliantAttribute> を削除します。  
  
-   このプロパティが CLS に準拠している必要がある場合は、`Property` ステートメントを `<CLSCompliant(True)>` としてマークします。  
  
## 参照  
 [\<PAVE OVER\> CLS 準拠コードの記述](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)