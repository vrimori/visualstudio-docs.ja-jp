---
title: "スタックの一番上にないメソッドのローカル変数の値を設定することはできません。 | Microsoft Docs"
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
  - "bc30711"
  - "vbc30711"
helpviewer_keywords: 
  - "BC30711"
ms.assetid: b2aa290f-3311-448a-af46-ff2a2add5788
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# スタックの一番上にないメソッドのローカル変数の値を設定することはできません。
呼び出しスタックの一番上にある場合にのみ、変数を変更することができます。 たとえば、`procedure1` が `procedure2` を呼び出し、現在の位置が `procedure1` である場合、`procedure2` 内の変数を変更することはできません。  
  
 **エラー ID:** BC30711  
  
### このエラーを解決するには  
  
-   呼び出しスタックの一番上にある変数を変更します。  
  
## 参照  
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)