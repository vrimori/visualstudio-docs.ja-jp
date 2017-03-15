---
title: "コンパイラ エラー CS0647 | Microsoft Docs"
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
  - "CS0647"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0647"
ms.assetid: b62d7fc9-4711-428e-ab66-09ea1c9970f0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0647
'attribute' 属性を作成時にエラーが発生しました \-\- 'reason'  
  
 次の例では CS0647 が生成されます。  
  
```  
// CS0647.cs using System.Runtime.InteropServices; [Guid("z")]   // CS0647, incorrect uuid format. // try the following line instead // [Guid("00000000-0000-0000-0000-000000000001")] public class MyClass { public static void Main() { } }  
```