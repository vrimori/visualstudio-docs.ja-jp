---
title: "コンパイラ エラー CS1629 | Microsoft Docs"
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
  - "CS1629"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1629"
ms.assetid: 907eae46-0265-4cd0-b27b-ff555d004259
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1629
アンセーフ コードは反復子には記述できません。  
  
 C\# 言語仕様は、反復子に安全でないコードを許可していません。  
  
 次の例では CS1629 が生成されます。  
  
```  
// CS1629.cs // compile with: /unsafe using System.Collections.Generic; class C { IEnumerator<int> IteratorMeth() { int i; unsafe  // CS1629 { int *p = &i; yield return *p; } } }  
```