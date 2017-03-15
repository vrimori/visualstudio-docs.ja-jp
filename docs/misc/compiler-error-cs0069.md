---
title: "コンパイラ エラー CS0069 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0069"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0069"
ms.assetid: a1b32906-7773-47c6-8515-162a201a9be5
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0069
インターフェイスのイベントに、add または remove アクセサーを指定することはできません。  
  
 イベントのアクセサー関数を [interface](/dotnet/csharp/language-reference/keywords/interface) で定義することはできません。 詳細については、[イベント](/dotnet/csharp/programming-guide/events/index) および [インターフェイス](/dotnet/csharp/programming-guide/interfaces/index) を参照してください。  
  
 次の例では CS0069 エラーが生成されます。  
  
```  
// CS0069.cs // compile with: /target:library public delegate void EventHandler(); public interface a { event EventHandler Click { remove {} }   // CS0069 event EventHandler Click2;   // OK }  
```