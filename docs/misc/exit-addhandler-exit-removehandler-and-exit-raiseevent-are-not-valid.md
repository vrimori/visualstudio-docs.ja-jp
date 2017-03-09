---
title: "&#39;Exit AddHandler&#39;、&#39;Exit RemoveHandler&#39; および &#39;Exit RaiseEvent&#39; は有効ではありません | Microsoft Docs"
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
  - "vbc31111"
  - "bc31111"
helpviewer_keywords: 
  - "BC31111"
ms.assetid: e02264f3-0645-4de5-b622-8a2a74496b64
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit AddHandler&#39;、&#39;Exit RemoveHandler&#39; および &#39;Exit RaiseEvent&#39; は有効ではありません
'Exit AddHandler'、'Exit RemoveHandler' および 'Exit RaiseEvent' は有効ではありません。 イベント メンバーを終了するには、'Return' を使用してください。  
  
 `Exit` ステートメントを使用して、`Custom Event` 宣言内の `AddHandler` メソッド、`RemoveHandler` メソッド、または `RaiseEvent` メソッドを終了することはできません。 代わりに、戻り値の式を指定しないで `Return` ステートメントを使用して、メソッドを終了します。  
  
 **エラー ID:** BC31111  
  
### このエラーを解決するには  
  
-   `Exit` ステートメントを `Return` ステートメントに置き換えます。  
  
     `Return` ステートメントが戻り値の式を指定しないようにします。  
  
## 参照  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- 削除](http://msdn.microsoft.com/ja-jp/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- 削除](http://msdn.microsoft.com/ja-jp/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- 削除](http://msdn.microsoft.com/ja-jp/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Return Statement](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)