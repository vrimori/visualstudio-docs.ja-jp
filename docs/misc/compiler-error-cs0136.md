---
title: "コンパイラ エラー CS0136 | Microsoft Docs"
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
  - "CS0136"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0136"
ms.assetid: 379a1a7d-c52c-4f2b-9e77-c1107d26faf4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0136
ローカルの変数 'var' をこのスコープで宣言することはできません。これは、'parent or current\/child' スコープで別の意味を持つ 'var' の意味が変更されるのを避けるためです。  
  
 変数宣言が、スコープ内にある別の宣言を隠しています。 CS0136 が発生した行で宣言されている変数の名前を変更します。  
  
## 使用例  
 次の例では CS0136 が生成されます。  
  
```  
// CS0136.cs  
namespace MyNamespace  
{  
   public class MyClass  
   {  
      public static void Main()  
      {  
         int i = 0;  
         {  
            char i = 'a';   // CS0136, hides int i  
         }  
         i++;  
      }  
   }  
}  
```  
  
 [C\# 言語仕様](/dotnet/csharp/language-reference/language-specification) から、セクション 7.5.2.1:  
  
 式または宣言子で特定の識別子が単純名として出現するたびに、その出現を直接囲むローカル変数宣言領域 \(§3.3\) 内で、式または宣言子内の単純名としての同じ識別子の他のすべての出現は同じエンティティを指す必要があります。 この規則により、特定のブロック、スイッチ ブロック、for\-、foreach\-、using\- ステートメント、または匿名関数内で、名前の意味は常に同じになります。