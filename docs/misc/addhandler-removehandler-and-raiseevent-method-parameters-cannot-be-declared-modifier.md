---
title: "&#39;AddHandler&#39;、&#39;RemoveHandler&#39;、および &#39;RaiseEvent&#39; メソッド パラメーターは &#39;&lt;modifier&gt;&#39; と宣言できません | Microsoft Docs"
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
  - "vbc31138"
  - "bc31138"
helpviewer_keywords: 
  - "BC31138"
ms.assetid: 6d8df92a-95fc-4a7d-ab1e-06d312155c55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddHandler&#39;、&#39;RemoveHandler&#39;、および &#39;RaiseEvent&#39; メソッド パラメーターは &#39;&lt;modifier&gt;&#39; と宣言できません
`AddHandler`、`RemoveHandler`、および `RaiseEvent` メソッドのパラメーターは、`Optional` または `ParamArray` 修飾子を使用して宣言できません。  
  
 `Optional` または `ParamArray` 修飾子は、`Declare`、`Function`、`Property`、および `Sub` 宣言内のパラメーターでのみ使用できます。  
  
 **エラー ID:** BC31138  
  
### このエラーを解決するには  
  
-   パラメーター リストから `Optional` または `ParamArray` キーワードを削除します。  
  
## 参照  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- 削除](http://msdn.microsoft.com/ja-jp/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- 削除](http://msdn.microsoft.com/ja-jp/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- 削除](http://msdn.microsoft.com/ja-jp/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)