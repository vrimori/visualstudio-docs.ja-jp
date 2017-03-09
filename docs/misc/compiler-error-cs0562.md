---
title: "コンパイラ エラー CS0562 | Microsoft Docs"
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
  - "CS0562"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0562"
ms.assetid: dceecce5-90ce-4554-820c-f4c06b2b8258
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0562
単項演算子のパラメーターは、それを含む型でなければなりません。  
  
 演算子のオーバーロードのためのメソッド宣言は、特定のガイドラインに沿っている必要があります。 詳細については、「[オーバーロードされた演算子](/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators)」と「[Operator Overloading Sample](http://msdn.microsoft.com/ja-jp/1c6b4610-0a49-4532-8fa7-f694cfc65743)」を参照してください。  
  
## 使用例  
 次の例では CS0562 が生成されます。  
  
```  
// CS0562.cs public class iii { public static implicit operator int(iii x) { return 0; } public static implicit operator iii(int x) { return null; } public static iii operator +(int aa)   // CS0562 // try the following line instead // public static iii operator +(iii aa) { return (iii)0; } public static void Main() { } }  
```