---
title: "コンパイラの警告 (レベル 2) CS0469 | Microsoft Docs"
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
  - "CS0469"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0469"
ms.assetid: 773925ce-a8b2-4098-9ead-b96197442848
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 2) CS0469
'goto case' 値は型 'type' に暗黙的に変換できません  
  
 `goto case` を使用する場合は、goto case の値からスイッチの型への暗黙的な変換が必要です。  
  
## 使用例  
 次の例では CS0469 が生成されます。  
  
```  
// CS0469.cs // compile with: /W:2 class Test { static void Main() { char c = (char)180; switch (c) { case (char)127: break; case (char)180: goto case 127;   // CS0469 // try the following line instead // goto case (char) 127; } } }  
```