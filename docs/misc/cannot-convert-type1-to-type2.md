---
title: "&#39;type1&#39; を &#39;type2&#39; に変換できません | Microsoft Docs"
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
  - "bc31193"
  - "vbc31193"
helpviewer_keywords: 
  - "BC31193"
ms.assetid: f25a9f5b-7741-4cd6-b85a-b19037ed8e49
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;type1&#39; を &#39;type2&#39; に変換できません
'type1' を 'type2' に変換できません。 'parentElement' の最初の要素の文字列値は、'Value' プロパティを使用して取得できます。  
  
 XML リテラルを特定の型を暗黙的にキャストしようとしました。 XML リテラルは、指定した型に暗黙的にキャストできません。  
  
 **エラー ID:** BC31193  
  
### このエラーを解決するには  
  
-   XML リテラルの `Value` プロパティを使用して、その値を `String` として参照します。`CType` 関数、別の型変換関数、または <xref:System.Convert> クラスを使用して、指定した型として値をキャストします。  
  
## 参照  
 <xref:System.Convert>   
 [Accessing XML in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/xml/accessing-xml)   
 [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)