---
title: "コンパイラ エラー CS0529 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0529"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0529"
ms.assetid: 61de8086-f991-455c-b009-bb8cd05f34bd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0529
継承インターフェイス 'interface1' により、'interface2' のインターフェイス階層内で循環参照が発生します  
  
 [interface](/dotnet/csharp/language-reference/keywords/interface) の継承リストに、自分自身への直接または間接参照が含まれています。 インターフェイスは、それ自体からは継承できません。  
  
 次の例では CS0529 が生成されます。  
  
```  
// CS0529.cs namespace x { public interface a { } public interface b : a, c { } public interface c : b   // CS0529, b inherits from c { } }  
```