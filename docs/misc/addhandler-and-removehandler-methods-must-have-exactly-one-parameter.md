---
title: "&#39;AddHandler&#39; および &#39;RemoveHandler&#39; メソッドには、パラメーターを 1 つだけ指定しなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31133"
  - "bc31133"
helpviewer_keywords: 
  - "BC31133"
ms.assetid: f6295626-dd63-408c-ab5f-76367f94d6ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddHandler&#39; および &#39;RemoveHandler&#39; メソッドには、パラメーターを 1 つだけ指定しなければなりません
カスタム イベント宣言には `AddHandler` または `RemoveHandler` 宣言が必要で、それぞれがカスタム イベントの `As` 句で指定されたデリゲート型の 1 つのパラメーターを取ります。  
  
 **エラー ID:** BC31133  
  
### このエラーを解決するには  
  
-   パラメーター リストから余分なパラメーターを削除し、パラメーターの型をカスタム イベントの `As` 句で指定されたデリゲート型と同じ型に変更します。  
  
## 使用例  
 この例は、`AddHandler` および `RemoveHandler` 宣言に対して適切なパラメーターの型を持つカスタム イベントを示します。  
  
 [!CODE [VbVbalrEventError#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#1)]  
  
## 参照  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- 削除](http://msdn.microsoft.com/ja-jp/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- 削除](http://msdn.microsoft.com/ja-jp/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)