---
title: "コンパイラ エラー CS0065 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0065"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0065"
ms.assetid: 49ca30a8-513a-40ed-aa0c-eb696a25b91f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0065
'event': イベント プロパティには、add および remove アクセサーの両方を指定する必要があります  
  
 フィールドではないイベントには、両方のアクセス方法が必要です。  
  
 次の例では CS0065 が生成されます。  
  
```  
// CS0065.cs using System; public delegate void Eventhandler(object sender, int e); public class MyClass { public event EventHandler Click   // CS0065, { // to fix, uncomment the add and remove definitions /* add { Click += value; } remove { Click -= value; } */ } public static void Main() { } }  
```  
  
## 参照  
 [イベント](/dotnet/csharp/programming-guide/events/index)