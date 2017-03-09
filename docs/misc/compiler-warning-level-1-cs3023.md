---
title: "コンパイラの警告 (レベル 1) CS3023 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3023"
ms.assetid: fd7782f9-f18a-4ce8-843b-95bf19b54317
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS3023
CLSCompliant 属性は、戻り値の型に適用しても意味がありません。  代わりに、メソッドに適用してください。  
  
 CLS 準拠の規則はメソッドと型の宣言に適用されるので、関数の戻り値の型に対して CLS 準拠はチェックされません。  
  
## 使用例  
 次のコード例では、警告 CS3023 が生成されます。  
  
```  
// C3023.cs [assembly:System.CLSCompliant(true)] public class Test { [return:System.CLSCompliant(true)]  // CS3023 // Try this instead: // [method:System.CLSCompliant(true)] public static int Main() { return 0; } }  
```