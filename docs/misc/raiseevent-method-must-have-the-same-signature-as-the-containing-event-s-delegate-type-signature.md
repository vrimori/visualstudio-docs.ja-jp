---
title: "&#39;RaiseEvent&#39; メソッドには、含んでいるイベントのデリゲート型 &#39;&lt;signature&gt;&#39; として同じシグネチャを指定する必要があります | Microsoft Docs"
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
  - "bc31137"
  - "vbc31137"
helpviewer_keywords: 
  - "BC31137"
ms.assetid: 9db77546-9205-4fd2-baf6-6eb1b46b1f1a
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;RaiseEvent&#39; メソッドには、含んでいるイベントのデリゲート型 &#39;&lt;signature&gt;&#39; として同じシグネチャを指定する必要があります
`Custom Event` 宣言には、カスタム イベントの `As` 句で指定されたデリゲート型と同じシグネチャを持つ `RaiseEvent` 宣言が必要です。  
  
 シグネチャが一致するには、`RaiseEvent` 宣言とデリゲートに同じ数のパラメーターがあり、パラメーターの型が一致している必要があります。  
  
 **エラー ID:** BC31137  
  
### このエラーを解決するには  
  
-   デリゲート型のパラメーターに合わせて `RaiseEvent` 宣言のパラメーターを変更します。  
  
## 使用例  
 この例は、`RaiseEvent` 宣言に対して適切なパラメーターの型を持つカスタム イベントを示します。  
  
 [!CODE [VbVbalrEventError#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#2)]  
  
## 参照  
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [RaiseEvent \- 削除](http://msdn.microsoft.com/ja-jp/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)