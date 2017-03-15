---
title: "コンパイラの警告 (レベル 1) CS1634 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1634"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1634"
ms.assetid: 4fd00eeb-89e3-4c18-827d-9b00a4bd8c9a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS1634
disable または restore を指定してください。  
  
 このエラーは、\#pragma warning 句が間違った形式で指定されている場合 \(disable や restore が省略されているなど\) に発生します。 詳細については、[\#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) のトピックを参照してください。  
  
## 使用例  
 次の例では CS1634 が生成されます。  
  
```  
// CS1634.cs // compile with: /W:1 #pragma warning   // CS1634 // Try this instead: // #pragma warning disable 0219 class MyClass { public static void Main() { } }  
```