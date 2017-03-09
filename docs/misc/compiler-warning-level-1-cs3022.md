---
title: "コンパイラの警告 (レベル 1) CS3022 | Microsoft Docs"
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
  - "CS3022"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3022"
ms.assetid: 9340645c-10c3-4e21-a825-3f05fae02ff7
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS3022
CLSCompliant 属性は、パラメーターに適用しても意味がありません 代わりに、メソッドに適用してください。  
  
 CLS 準拠の規則はメソッドと型の宣言に適用されるので、メソッドのパラメーターに対して CLS 準拠はチェックされません。  
  
## 使用例  
 次の例では CS3022 が生成されます。  
  
```  
// CS3022.cs // compile with: /W:1 using System; [assembly: CLSCompliant(true)] [CLSCompliant(true)] public class C { public void F([CLSCompliant(true)] int i) { } public static void Main() { } }  
```