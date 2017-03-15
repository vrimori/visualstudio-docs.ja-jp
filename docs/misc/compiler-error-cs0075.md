---
title: "コンパイラ エラー CS0075 | Microsoft Docs"
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
  - "CS0075"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0075"
ms.assetid: 5084d260-705e-4ff5-8f7a-7f74052fcbbb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0075
負の値をキャストするには、値をかっこで囲んでください。  
  
 定義済みの型を指定するキーワードを使用してキャストしている場合、かっこを付ける必要はありません。 それ以外の場合は、かっこを付ける必要があります。\(x\) –y がキャスト式と見なされないためです。 以下は「C\# 言語の仕様」のセクション 7.6.6 からの抜粋です。  
  
 *あいまいさを排除するための規則に従うと、x および y が識別子である場合は、\(x\)y、\(x\)\(y\)、および \(x\)\(\-y\) は cast\-expression であり、\(x\)\-y は x が型を示していても cast\-expression ではありません。 ただし、x が定義済みの型 \(int など\) を示すキーワードである場合は、このようなキーワードがそれ自体で式になることはないため、先に示した 4 つの形式はすべて cast\-expression になります。*  
  
 次のコードでは CS0075 が生成されます。  
  
```  
// CS0075 namespace MyNamespace { enum MyEnum { } public class MyClass { public static void Main() { // To fix the error, place the negative // values below in parentheses int i = (System.Int32) - 4; //CS0075 MyEnum e = (MyEnum) - 1;    //CS0075 System.Console.WriteLine(i); //to avoid warning System.Console.WriteLine(e); //to avoid warning } } }  
```  
  
## 参照  
 [キャストと型変換](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)