---
title: "コンパイラの警告 (レベル 2) CS0440 | Microsoft Docs"
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
  - "CS0440"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0440"
ms.assetid: ade6761f-4d7d-42bc-a0c5-bbb1b987a1aa
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS0440
'global::' はエイリアスではなく常にグローバル名前空間を参照するため、'global' という名前のエイリアスを定義することはお勧めしません。  
  
 この警告は、global という名前のエイリアスを定義した場合に発生します。  
  
## 使用例  
 次の例では、CS0440 が生成されます。  
  
```  
// CS0440.cs // Compile with: /W:1 using global = MyClass;   // CS0440 class MyClass { static void Main() { // Note how global refers to the global namespace // even though it is redefined above. global::System.Console.WriteLine(); } }  
```