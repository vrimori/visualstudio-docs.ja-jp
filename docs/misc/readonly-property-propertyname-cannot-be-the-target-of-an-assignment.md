---
title: "&#39;ReadOnly&#39; プロパティ &#39;&lt;propertyname&gt;&#39; を代入式のターゲットにすることはできません。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30098"
  - "vbc30098"
helpviewer_keywords: 
  - "BC30098"
ms.assetid: d0c6cdac-a49d-49d2-ba92-ddf01eed0620
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReadOnly&#39; プロパティ &#39;&lt;propertyname&gt;&#39; を代入式のターゲットにすることはできません。
値を代入するコンテキストに `ReadOnly` プロパティがあります。 実行時に値を代入できるのは、書き込み可能な変数、プロパティ、および配列要素だけです。  
  
 **エラー ID:** BC30098  
  
### このエラーを解決するには  
  
-   変数を宣言する `Property` ステートメントから `ReadOnly` キーワードを削除するか、または値を割り当てるステートメントを削除します。  
  
## 参照  
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)   
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)