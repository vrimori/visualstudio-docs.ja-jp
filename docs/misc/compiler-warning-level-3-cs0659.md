---
title: "コンパイラの警告 (レベル 3) CS0659 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0659"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0659"
ms.assetid: 63435ee6-c92f-4124-95d4-d8f4e5f0af80
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 3) CS0659
'class' は Object.Equals\(object o\) をオーバーライドしますが、Object.GetHashCode\(\) をオーバーライドしません。  
  
 コンパイラで **Equals** 関数のオーバーライドは検出されましたが、**GetHashCode** のオーバーライドは検出されませんでした。**Equals** のオーバーライドは、**GetHashCode** をオーバーライドする場合に使用します。  
  
 詳細については、次のトピックを参照してください。  
  
-   <xref:System.Collections.Hashtable>。  
  
-   [等値演算子](../Topic/Equality%20Operators.md)  
  
-   [NIB: Equals メソッドの実装](http://msdn.microsoft.com/ja-jp/30f28aaf-8b9e-46cd-a746-58a12473af2c)  
  
-   <xref:System.Object.GetHashCode%2A>  
  
 次の例では CS0659 が生成されます。  
  
```  
// CS0659.cs // compile with: /W:3 /target:library class Test { public override bool Equals(object o) { return true; }   // CS0659 } // OK class Test2 { public override bool Equals(object o) { return true; } public override int GetHashCode() { return 0; } }  
```