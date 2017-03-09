---
title: "ステートメントは、&#39;AddHandler&#39;、&#39;RemoveHandler&#39; または &#39;RaiseEvent&#39; メソッドを宣言しません | Microsoft Docs"
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
  - "vbc31113"
  - "bc31113"
helpviewer_keywords: 
  - "BC31113"
ms.assetid: f8299c9d-6030-43e5-878e-8d2b042191b5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ステートメントは、&#39;AddHandler&#39;、&#39;RemoveHandler&#39; または &#39;RaiseEvent&#39; メソッドを宣言しません
ステートメントは、`Custom Event` プロシージャの周囲に、`AddHandler`、`RemoveHandler`、または `RaiseEvent` 宣言ステートメントを指定していません。 カスタム イベント宣言は、`Custom Event` および `End Event` ステートメントの中に囲まれたコードのブロックです。 このブロック内では、各 `Custom Event` プロシージャが、宣言ステートメントと `End` ステートメントの中に囲まれた内部ブロックとして記述されます。  
  
 **エラー ID:** BC31113  
  
### このエラーを解決するには  
  
-   `AddHandler`、`RemoveHandler`、または `RaiseEvent` 宣言ステートメントを指定します。  
  
## 参照  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- 削除](http://msdn.microsoft.com/ja-jp/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- 削除](http://msdn.microsoft.com/ja-jp/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- 削除](http://msdn.microsoft.com/ja-jp/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)