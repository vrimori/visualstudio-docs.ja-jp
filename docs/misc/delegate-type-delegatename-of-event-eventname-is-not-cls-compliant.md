---
title: "イベント &#39;&lt;eventname&gt;&#39; のデリゲート型 &#39;&lt;delegatename&gt;&#39; は CLS 準拠ではありません | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40050"
  - "vbc40050"
helpviewer_keywords: 
  - "BC40050"
ms.assetid: 92f5be26-9a82-46d4-bf97-005f2c7ca424
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# イベント &#39;&lt;eventname&gt;&#39; のデリゲート型 &#39;&lt;delegatename&gt;&#39; は CLS 準拠ではありません
[Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement) はデリゲートを使用してその署名を指定しますが、[Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement) は `<CLSCompliant(False)>` としてマークされているか、またはマークされていません。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> 属性を適用するときは、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40050  
  
### このエラーを解決するには  
  
-   CLS 準拠が必要で、デリゲートの定義を制御できる場合は、<xref:System.CLSCompliantAttribute> をその宣言に適用して、`<CLSCompliant(True)>` としてマークします。  
  
-   デリゲートの定義を制御できない場合、または準拠としてマークできない場合は、<xref:System.CLSCompliantAttribute> を `Event` ステートメントから削除するか、または `<CLSCompliant(False)>` としてマークします。  
  
## 参照  
 [\<PAVE OVER\> CLS 準拠コードの記述](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)