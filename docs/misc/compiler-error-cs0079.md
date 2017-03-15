---
title: "コンパイラ エラー CS0079 | Microsoft Docs"
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
  - "CS0079"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0079"
ms.assetid: 71c85883-b72f-402f-a828-18ca92976273
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0079
イベント 'event' は \+\= または \-\= の左側でのみ使用できます  
  
 [event](/dotnet/csharp/language-reference/keywords/event) が正しく呼び出されませんでした。 詳細については、次のトピックを参照してください。[イベント](/dotnet/csharp/programming-guide/events/index) および[デリゲート](/dotnet/csharp/programming-guide/delegates/index).  
  
 次の例では CS0079 が生成されます。  
  
```  
// CS0079.cs using System; public delegate void MyEventHandler(); public class Class1 { private MyEventHandler _e; public event MyEventHandler Pow { add { _e += value; Console.WriteLine("in add accessor"); } remove { _e -= value; Console.WriteLine("in remove accessor"); } } public void Handler() { } public void Fire() { if (_e != null) { Pow();   // CS0079 // try the following line instead // _e(); } } public static void Main() { Class1 p = new Class1(); p.Pow += new MyEventHandler(p.Handler); p._e(); p.Pow += new MyEventHandler(p.Handler); p._e(); p._e -= new MyEventHandler(p.Handler); if (p._e != null) { p._e(); } p.Pow -= new MyEventHandler(p.Handler); if (p._e != null) { p._e(); } } }  
```