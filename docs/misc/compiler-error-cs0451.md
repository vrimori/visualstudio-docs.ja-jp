---
title: "コンパイラ エラー CS0451 | Microsoft Docs"
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
  - "CS0451"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0451"
ms.assetid: e73544f8-856b-4a92-90e0-dd6cb9d688b1
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0451
'new\(\)' 制約は 'struct' 制約と一緒には使用できません。  
  
 ジェネリック型に対して制約を指定するとき、`new()` 制約は、クラス型制約、インターフェイス型制約、参照型制約、型パラメーター制約と組み合わせた場合のみ使用できます。値型の制約と組み合わせて使用することはできません。  
  
## 使用例  
 次の例では CS0451 が生成されます。  
  
```  
// CS0451.cs using System; public class C4 { public void F4<T>() where T : struct, new() {}   // CS0451 } // OK public class C5 { public void F5<T>() where T : struct {} } public class C6 { public void F6<T>() where T : new() {} }  
  
```