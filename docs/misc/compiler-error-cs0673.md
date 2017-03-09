---
title: "コンパイラ エラー CS0673 | Microsoft Docs"
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
  - "CS0673"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0673"
ms.assetid: 5921cc27-c0ff-43be-8044-b454c8631c86
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0673
System.Void は C\# から使用できません。void 型オブジェクトを取得するには typeof\(void\) を使用してください。  
  
 C\# では **System.Void** を使用できません。  
  
 次の例では CS0673 が生成されます。  
  
```  
// CS0673.cs class MyClass { public static void Main() { System.Type t = typeof(System.Void);   // CS0673 // try the following line instead // System.Type t = typeof(void); } }  
```