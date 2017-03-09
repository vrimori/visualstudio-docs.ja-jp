---
title: "&#39;AddHandler&#39; および &#39;RemoveHandler&#39; メソッド パラメーターは &#39;ByRef&#39; と宣言できません | Microsoft Docs"
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
  - "vbc31134"
  - "bc31134"
helpviewer_keywords: 
  - "BC31134"
ms.assetid: 942f0b91-e71a-499a-ad10-a5dfcb4e72b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddHandler&#39; および &#39;RemoveHandler&#39; メソッド パラメーターは &#39;ByRef&#39; と宣言できません
`AddHandler` および `RemoveHandler` メソッドのパラメーターは、`ByRef` 修飾子を使用して宣言できません。  
  
 **エラー ID:** BC31134  
  
### このエラーを解決するには  
  
-   パラメーターから `ByRef` キーワードを削除します。  
  
## 参照  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- 削除](http://msdn.microsoft.com/ja-jp/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- 削除](http://msdn.microsoft.com/ja-jp/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)