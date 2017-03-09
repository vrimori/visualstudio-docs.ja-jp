---
title: "コンパイラの警告 (レベル 2) CS0437 | Microsoft Docs"
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
  - "CS0437"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0437"
ms.assetid: cba5c9b6-a0bc-4f19-b1f0-c1f66436ee91
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS0437
'assembly2' の型 'type' は、'fassembly1' のインポートされた名前空間 'namespace' と競合しています。 'assembly' で定義された型を使用しています。  
  
 この警告は、ソース ファイル file\_2 内の型が、'file\_1' のインポートされた名前空間と競合している場合に発生します。 この場合、コンパイルには、ソース ファイル内の型が使用されます。  
  
## 使用例  
  
```  
// CS0437_a.cs // compile with: /target:library namespace Util { public class A { public void Test() { System.Console.WriteLine("CS0437_a.cs"); } } }  
```  
  
## 使用例  
 次の例では CS0437 が生成されます。  
  
```  
// CS0437_b.cs // compile with: /reference:CS0437_a.dll /W:2 // CS0437 expected class Util { public class A { public void Test() { System.Console.WriteLine("CS0437_b.cs"); } } } public class Test { public static void Main() { Util.A x = new Util.A(); x.Test(); } }  
```