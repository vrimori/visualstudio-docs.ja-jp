---
title: "コンパイラ エラー CS0430 | Microsoft Docs"
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
  - "CS0430"
ms.assetid: b63c4f9a-b1cd-41d2-a02e-2ed0f177450f
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0430
extern エイリアス 'alias' は、\/reference オプションで指定されませんでした  
  
 このエラーは、extern エイリアスが見つかったものの、エイリアスがコマンド ラインで参照として指定されなかった場合に発生します。 CS0430 を解決するには、**\/reference** を使用してコンパイルします。  
  
## 使用例  
  
```  
// CS0430_a.cs // compile with: /target:library public class MyClass {}  
```  
  
## 使用例  
 **\/reference:MyType\=cs0430\_a.dll** を使用してコンパイルし、前の例で作成された DLL を参照すると、このエラーは解決します。 次の例では CS0430 が生成されます。  
  
```  
// CS0430_b.cs extern alias MyType;   // CS0430 public class Test { public static void Main() {} }  
  
```