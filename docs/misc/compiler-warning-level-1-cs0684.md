---
title: "コンパイラの警告 (レベル 1) CS0684 | Microsoft Docs"
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
  - "CS0684"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0684"
ms.assetid: d6c8aaf6-c1cf-4c0e-b367-4c3e418d8bc4
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 1) CS0684
'interface' インターフェイスは、'CoClassAttribute' でマークされていますが、'ComImportAttribute' ではマークされていません  
  
 インターフェイスに **CoClassAttribute** を指定した場合は、**ComImportAttribute** も指定する必要があります。  
  
 次の例では CS0684 が生成されます。  
  
```  
// CS0684.cs // compile with: /W:1 using System; using System.Runtime.InteropServices; [CoClass(typeof(C))] // CS0684 // try the following line instead // [CoClass(typeof(C)), ComImport] interface I { } class C { static void Main() {} }  
```