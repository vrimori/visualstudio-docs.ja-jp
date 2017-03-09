---
title: "コンパイラの警告 (レベル 1) CS0657 | Microsoft Docs"
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
  - "CS0657"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0657"
ms.assetid: d12d2efc-f44e-40e6-b825-5a66ead0c08e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS0657
'attribute modifier' はこの宣言に対して無効な属性の場所です。 この宣言に対して有効な属性の場所は 'locations' です。 このブロック内の属性はすべて無視されます。  
  
 コンパイラで、無効な場所に属性の修飾子が見つかりました。 詳細については、「[属性の対象](http://msdn.microsoft.com/ja-jp/59a261f0-1cfb-4aa5-b610-6b735389882c)」を参照してください。  
  
 次の例では CS0657 が生成されます。  
  
```  
// CS0657.cs // compile with: /target:library public class TestAttribute : System.Attribute {} [return: Test]   // CS0657 return not valid on a class class Class1 {}  
```