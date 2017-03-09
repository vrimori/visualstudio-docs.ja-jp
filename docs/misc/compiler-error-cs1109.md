---
title: "コンパイラ エラー CS1109 | Microsoft Docs"
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
  - "CS1109"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1109"
ms.assetid: bebe56b8-3831-4ebb-a49e-e0364b4c11a7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1109
拡張メソッドは、トップ レベルの静的クラスで定義される必要があります。'name' は入れ子になったクラスです。  
  
 拡張メソッドは、入れ子になったクラスでは定義できません。  
  
## 使用例  
 次の例では、クラス `Extension` がクラス `Out` の内部で入れ子になっているため、CS1109 が生成されます。  
  
```  
// cs1109.cs public class Test { } static class Out { static class Extension { static void ExtMethod(this Test c) // CS1109 { } } }  
```  
  
## 参照  
 [拡張メソッド](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)