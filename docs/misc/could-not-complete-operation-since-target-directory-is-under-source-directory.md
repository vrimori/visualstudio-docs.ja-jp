---
title: "ターゲット ディレクトリがソース ディレクトリ内にあるため、操作を完了できませんでした | Microsoft Docs"
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
  - "vbrIO_CyclicOperation"
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ターゲット ディレクトリがソース ディレクトリ内にあるため、操作を完了できませんでした
循環操作が失敗しました。 循環操作は循環しているため、完了できません。 たとえば、オブジェクト A がオブジェクト B の継承を試行し、同様にオブジェクト B がオブジェクト A の継承を試行するような場合です。  
  
### このエラーを解決するには  
  
-   継承を行うときには、参照の循環がないことを確認します。  
  
## 参照  
 [Error Types](/dotnet/visual-basic/programming-guide/language-features/error-types)   
 [Debugging Basics: Breakpoints](http://msdn.microsoft.com/ja-jp/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)