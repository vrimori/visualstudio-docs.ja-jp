---
title: "コンパイラ エラー CS0681 | Microsoft Docs"
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
  - "CS0681"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0681"
ms.assetid: aa51ad94-df0a-481d-aaea-5b4291ebc41c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0681
修飾子 'abstract' はフィールドで有効ではありません。 プロパティを使用してください  
  
 フィールドを抽象型にすることはできません。 ただし、フィールドにアクセスする抽象プロパティを含めることはできます。  
  
## 使用例  
 次の例では CS0681 が生成されます。  
  
```  
// CS0681.cs // compile with: /target:library abstract class C { abstract int num;  // CS0681 }  
  
```  
  
## 使用例  
 代わりに、次のコードをお試しください。  
  
```  
// CS0681b.cs // compile with: /target:library abstract class C { public abstract int num { get; set; } }  
```