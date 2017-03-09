---
title: "&#39;&lt;specifier&gt;&#39; は、インターフェイス イベント宣言には使用できません | Microsoft Docs"
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
  - "bc30275"
  - "vbc30275"
helpviewer_keywords: 
  - "BC30275"
ms.assetid: bd12c952-c619-4753-8d6d-90ef4086fdc2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;specifier&gt;&#39; は、インターフェイス イベント宣言には使用できません
インターフェイス内の `Event` ステートメントに、`Implements` のような使用できないキーワードが含まれています。 インターフェイスは、メンバーを定義することのみが可能で、実装はできません。  
  
 **エラー ID:** BC30275  
  
### このエラーを解決するには  
  
1.  宣言ステートメントからそのキーワードを削除します。  
  
2.  インターフェイス メンバーの実装を、インターフェイスを実装するクラスに移動します。  
  
## 参照  
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)