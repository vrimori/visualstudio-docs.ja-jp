---
title: "&#39;Custom&#39; 修飾子は、インターフェイスで宣言されたイベントでは無効です | Microsoft Docs"
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
  - "bc31121"
  - "vbc31121"
helpviewer_keywords: 
  - "BC31121"
ms.assetid: b5687034-a2b2-4961-88b7-0ba73023573e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Custom&#39; 修飾子は、インターフェイスで宣言されたイベントでは無効です
カスタム イベントはその `AddHandler`、`RemoverHandler`、および `RaiseEvent` メソッドで実装を提供する必要があるので、インターフェイス内でカスタム イベントを宣言できません。  
  
 `Custom` キーワードは、イベントを実装する派生クラスで使用できます。  
  
 **エラー ID:** BC31121  
  
### このエラーを解決するには  
  
-   インターフェイス内のイベント宣言から `Custom` キーワードを削除します。  
  
## 使用例  
 この例では、カスタム イベントとしてインターフェイスで宣言されているイベントを実装する方法を示します。  
  
 [!CODE [VbVbalrEventError#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#3)]  
  
## 参照  
 [カスタム \- 削除](http://msdn.microsoft.com/ja-jp/dc62be07-c896-4866-a533-982a661d143f)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)