---
title: "コンパイラ エラー CS0737 | Microsoft Docs"
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
  - "CS0737"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0737"
ms.assetid: d2247770-5546-46f2-a01d-8e2ebfcbb859
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0737
'type name' はインターフェイス メンバー 'member name' を実装しません。 'method name' は public ではないため、インターフェイス メンバーを実装できません。  
  
 インターフェイス メンバーを実装するメソッドは、パブリック アクセシビリティを持つ必要があります。 すべてのインターフェイス メンバーは `public` です。  
  
### このエラーを解決するには  
  
1.  [public](/dotnet/csharp/language-reference/keywords/public) アクセス修飾子をメソッドに追加します。  
  
## 使用例  
 次のコードでは CS0737 が生成されます。  
  
```  
// cs0737.cs interface ITest { // Default access of private with no modifier. int Return42(); // Try the following line instead. // public int Return42(); } struct Struct1 : ITest // CS0737 { int Return42() { return (42); } } public class Test { public static int Main(string[] args) { Struct1 s1 = new Struct1(); return (1); } }  
```  
  
## 参照  
 [インターフェイス](/dotnet/csharp/programming-guide/interfaces/index)