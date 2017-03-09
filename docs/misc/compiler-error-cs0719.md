---
title: "コンパイラ エラー CS0719 | Microsoft Docs"
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
  - "CS0719"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0719"
ms.assetid: 308a1a54-43b9-4970-8206-88e8f76d394e
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0719
'type': 配列要素をスタティック型にすることはできません  
  
 配列要素はインスタンスですが、スタティック型のインスタンスは作成できないため、スタティック型の配列は意味をなしません。  
  
 次の例では CS0719 が生成されます。  
  
```  
// CS0719.cs public static class SC { public static void F() { } } public class CMain { public static void Main() { SC[] sca = new SC[10];  // CS0719 } }  
```