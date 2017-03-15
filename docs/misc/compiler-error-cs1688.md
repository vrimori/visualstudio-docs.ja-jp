---
title: "コンパイラ エラー CS1688 | Microsoft Docs"
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
  - "CS1688"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1688"
ms.assetid: e15672a1-2570-4e65-99fc-7acc190ae643
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1688
デリゲート型 'delegate' には 1 つ以上の out パラメーターが含まれているため、パラメーター リストを含まない匿名メソッド ブロックをこのデリゲート型に変換することはできません  
  
 多くの場合、匿名メソッド ブロックではパラメーターを省略できます。 このエラーは、匿名メソッド ブロックにパラメーター リストがなく、デリゲートに `out` パラメーターがある場合に発生します。 コンパイラでは、正常に動作する見込みがない `out` パラメーターの存在を無視する必要があるため、このような状況は許可されません。  
  
## 使用例  
 次のコードではエラー CS1688 が生成されます。  
  
```  
// CS1688.cs using System; delegate void OutParam(out int i); class ErrorCS1676 { static void Main() { OutParam o; o = delegate  // CS1688 // Try this instead: // o = delegate(out int i) { Console.WriteLine(""); }; } }  
```