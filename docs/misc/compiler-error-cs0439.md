---
title: "コンパイラ エラー CS0439 | Microsoft Docs"
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
  - "CS0430"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0439"
ms.assetid: 5cbac869-1b1b-45f9-98c8-38c17348035f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0439
extern エイリアス宣言は、名前空間で定義された他のすべての要素の前に指定しなければなりません。  
  
 このエラーは、`extern` 宣言が、`using` 宣言などの、同じ名前空間の別なものの後に指定されているときに発生します。`extern` 宣言は、他のすべての名前空間要素の前に指定する必要があります。  
  
## 使用例  
 次の例では、CS0439 が生成されます。  
  
```  
// CS0439.cs using System; extern alias MyType;   // CS0439 // To resolve the error, make the extern alias the first line in the file. public class Test { public static void Main() { } }  
```