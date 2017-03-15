---
title: "コンパイラ エラー CS0275 | Microsoft Docs"
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
  - "CS0275"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0275"
ms.assetid: 4d59f11c-b0ea-4c91-b2cb-cbe3be9a9ba2
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0275
'accessor': アクセシビリティ修飾子をインターフェイスのアクセサーで使用することはできません  
  
 このエラーは、インターフェイスのプロパティまたはインデクサーのアクセサーのいずれかでアクセス修飾子を使用すると発生します。 解決するには、アクセス修飾子を削除します。  
  
## 使用例  
 次の例では CS0275 が生成されます。  
  
```  
// CS0275.cs public interface MyInterface { int Property { get; internal set;   // CS0275 } }  
```