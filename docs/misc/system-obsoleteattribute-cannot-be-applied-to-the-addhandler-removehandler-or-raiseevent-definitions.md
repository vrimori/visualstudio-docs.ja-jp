---
title: "&#39;System.ObsoleteAttribute&#39; を &#39;AddHandler&#39;、&#39;RemoveHandler&#39;、または &#39;RaiseEvent&#39; 定義に適用できません | Microsoft Docs"
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
  - "bc31142"
  - "vbc31142"
helpviewer_keywords: 
  - "BC31142"
ms.assetid: 2bddde2e-9ca0-4f72-8910-0789a6350af8
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.ObsoleteAttribute&#39; を &#39;AddHandler&#39;、&#39;RemoveHandler&#39;、または &#39;RaiseEvent&#39; 定義に適用できません
'System.ObsoleteAttribute' を 'AddHandler'、'RemoveHandler'、または 'RaiseEvent' 定義に適用できません。 必要であれば、属性をイベントに直接適用してください。  
  
 カスタム イベントは <xref:System.ObsoleteAttribute> を、その `AddHandler`、`RemoveHandler`、または `RaiseEvent` プロシージャに適用します。  
  
 <xref:System.ObsoleteAttribute> は、プログラミング要素を使用されていないとマークし、要素が将来の製品バージョンで削除される予定であることをユーザーに通知します。  
  
 カスタム イベントの特定の部分が依然使用中で、他の部分がもはや使用されないのは意味がありません。  
  
 **エラー ID:** BC31142  
  
### このエラーを解決するには  
  
-   個々のプロシージャ宣言から <xref:System.ObsoleteAttribute> を削除し、全体的なイベントの宣言に適用します。  
  
## 参照  
 <xref:System.ObsoleteAttribute>   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler Statement](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [RemoveHandler Statement](/dotnet/visual-basic/language-reference/statements/removehandler-statement)   
 [RaiseEvent Statement](/dotnet/visual-basic/language-reference/statements/raiseevent-statement)