---
title: "コンパイラ エラー CS0135 | Microsoft Docs"
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
  - "CS0135"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0135"
ms.assetid: 1bda402c-e8bd-4117-93d9-f4968d9e8303
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0135
'declaration1' は宣言 'declaration2' と競合します  
  
 コンパイラは、一般にコードのロジック エラーにつながる、名前の隠蔽を許可しません。  
  
## 使用例  
 次の例では CS0135 が生成されます。  
  
```  
// CS0135.cs  
public class MyClass2  
{  
   public static int i = 0;  
  
   public static void Main()  
   {  
      {  
         int i = 4;  
         i++;  
      }  
      i = 0;   // CS0135  
   }  
}  
```  
  
 [C\# 言語仕様](/dotnet/csharp/language-reference/language-specification) から、セクション 7.5.2.1:  
  
 式または宣言子で特定の識別子が単純名として出現するたびに、その出現を直接囲むローカル変数宣言領域 \(§3.3\) 内で、式または宣言子内の単純名としての同じ識別子の他のすべての出現は同じエンティティを指す必要があります。 この規則により、特定のブロック、スイッチ ブロック、for\-、foreach\-、using\- ステートメント、または匿名関数内で、名前の意味は常に同じになります。