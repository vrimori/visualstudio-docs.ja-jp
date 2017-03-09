---
title: "コンパイラ エラー CS1675 | Microsoft Docs"
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
  - "CS1675"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1675"
ms.assetid: add10021-f751-45c7-addc-0f73fa4a267c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1675
Enums に型パラメーターを指定することはできません。  
  
 このエラーを解決するには、`enum` 宣言から型パラメーターを削除します。  
  
## 使用例  
 次の例では CS1675 が生成されます。  
  
```  
// CS1675.cs enum E<T>  // CS1675 { } class CMain { public static void Main() { } }  
```