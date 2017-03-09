---
title: "コンパイラの警告 (レベル 4) CS0402 | Microsoft Docs"
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
  - "CS0402"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0402"
ms.assetid: 5a252c95-18c7-4569-bae0-e1f7b582cf6a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 4) CS0402
'identifier' : エントリ ポイントがジェネリックであることや、ジェネリック型の中に存在することはできません。  
  
 エントリ ポイントがジェネリック型の中で見つかりました。 この警告を除去するには、非ジェネリック クラスまたは構造体に Main を実装します。  
  
```  
// CS0402.cs // compile with: /W:4 class C<T> { public static void Main()  // CS0402 { } } class CMain { public static void Main() {} }  
```