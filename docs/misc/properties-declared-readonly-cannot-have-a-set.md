---
title: "&#39;ReadOnly&#39; として宣言されているプロパティに &#39;Set&#39; を使用することはできません | Microsoft Docs"
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
  - "vbc30022"
  - "bc30022"
helpviewer_keywords: 
  - "BC30022"
ms.assetid: a22eff96-8c18-47c4-9ef0-f98b2ab8a5d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReadOnly&#39; として宣言されているプロパティに &#39;Set&#39; を使用することはできません
`Set` プロシージャはプロパティの値を書き込みます。`ReadOnly` プロパティを書き込むことはできません。  
  
 **エラー ID:** BC30022  
  
### このエラーを解決するには  
  
-   `ReadOnly` キーワードを `Property` ステートメントから削除するか、`Set` プロシージャをプロパティ本体から削除します。  
  
## 参照  
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)   
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)