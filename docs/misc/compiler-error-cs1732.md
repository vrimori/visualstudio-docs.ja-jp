---
title: "コンパイラ エラー CS1732 | Microsoft Docs"
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
  - "CS1732"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1732"
ms.assetid: 72c7f7fc-d5f2-4538-9b02-50dda54d3b1e
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1732
パラメーターが必要です。  
  
 このエラーは、ラムダ式の入力パラメーターの後にコンマが含まれているが、それに続くパラメーターが指定されていない場合に生成されます。  
  
### このエラーを解決するには  
  
1.  コンマを削除するか、コンパイラが期待する入力パラメーターをコンマの後に追加します。  
  
## 使用例  
 次の例では CS1732 が生成されます。  
  
```  
// cs1732.cs // compile with: /target:library class Test { delegate void D(int x, int y); static void Main() { D d = (x,) => { }; // CS1732 } }  
```