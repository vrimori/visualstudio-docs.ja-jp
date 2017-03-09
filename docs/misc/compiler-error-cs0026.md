---
title: "コンパイラ エラー CS0026 | Microsoft Docs"
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
  - "CS0026"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0026"
ms.assetid: 8767fbc1-8ba7-4e88-a9f9-7e620411882b
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0026
キーワード 'this' は、静的プロパティ、静的メソッド、または静的フィールド初期化子では無効です  
  
 [this](/dotnet/csharp/language-reference/keywords/this) キーワードは、型のインスタンスであるオブジェクトを参照します。 静的メソッドはクラスを含むインスタンスに依存しないため、"this" キーワードは無意味であり、使用できません。 詳細については、次のトピックを参照してください。[静的クラスと静的クラス メンバー](/dotnet/csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members) および[オブジェクト](/dotnet/csharp/programming-guide/classes-and-structs/objects).  
  
## 使用例  
 次の例では、CS0026 が生成されます。  
  
```  
// CS0026.cs public class A { public static int i = 0; public static void Main() { // CS0026 this.i = this.i + 1; // Try the following line instead: // i = i + 1; } }  
```