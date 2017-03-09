---
title: "コンパイラの警告 (レベル 2) CS0464 | Microsoft Docs"
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
  - "CS0464"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0464"
ms.assetid: 3dff97d4-e1f6-4a71-91e2-68cffc38d49a
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS0464
型 'type' の null と比較するといつも 'false' を生成します。  
  
 この警告は、null 許容変数と null の比較を実行し、その比較が `==` でも `!=` でもない場合に生成されます。 このエラーを解決するには、値が `null` であることを確認する必要があるかどうかを確認します。`i == null` のような比較では、true または false のいずれかになります。`i > null` のような比較では、常に false になります。  
  
## 使用例  
 次の例では CS0464 が生成されます。  
  
```  
// CS0464.cs class MyClass { public static void Main() { int? i = 0; if (i < null) ;   // CS0464 i++; } }  
```