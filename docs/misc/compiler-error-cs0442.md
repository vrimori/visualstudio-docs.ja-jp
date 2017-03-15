---
title: "コンパイラ エラー CS0442 | Microsoft Docs"
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
  - "CS0442"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0442"
ms.assetid: a411660d-0db6-4b63-b19e-f4538fc201e5
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0442
'Property': 抽象プロパティにプライベート アクセサーは指定できません  
  
 このエラーは、アクセス修飾子 "private" を使用して抽象アクセサーを変更する場合に発生します。 解決するには、別のアクセス修飾子を使用するか、プロパティを非抽象にします。  
  
## 使用例  
 次の例では CS0442 が生成されます。  
  
```  
// CS0442.cs public abstract class MyClass { public abstract int AbstractProperty { get; private set;   // CS0442 // Try this instead: // set; } }  
```