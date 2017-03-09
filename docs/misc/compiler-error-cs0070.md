---
title: "コンパイラ エラー CS0070 | Microsoft Docs"
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
  - "CS0070"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0070"
ms.assetid: bb0de7c6-c734-4a8f-ab62-0a50eac2a91f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0070
イベント 'event' は \+\=、\-\= の左辺にのみ使用できます。ただし、'type' 型内から使用されている場合を除きます  
  
 定義されているクラスの外部では、[event](/dotnet/csharp/language-reference/keywords/event) は参照の追加または削除のみできます。 詳細については、「[イベント](/dotnet/csharp/programming-guide/events/index)」を参照してください。  
  
 次の例では CS0070 エラーが生成されます。  
  
```  
// CS0070.cs using System; public delegate void EventHandler(); public class A { public event EventHandler Click; public static void OnClick() { EventHandler eh; A a = new A(); eh = a.Click; } public static void Main() { } } public class B { public int Foo () { EventHandler eh = new EventHandler(A.OnClick); A a = new A(); eh = a.Click;   // CS0070 // try the following line instead // a.Click += eh; return 1; } }  
```