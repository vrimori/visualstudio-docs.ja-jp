---
title: "&#39;Handles&#39; は演算子の宣言で有効ではありません | Microsoft Docs"
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
  - "bc33003"
  - "vbc33003"
helpviewer_keywords: 
  - "BC33003"
ms.assetid: 8336402c-9393-4e8e-834d-55c2268f24f6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Handles&#39; は演算子の宣言で有効ではありません
[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) ステートメントに [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause) キーワードが指定されています。  
  
 イベントを処理できるのは `Sub` プロシージャだけです。`Operator` プロシージャでは処理できません。 イベント ハンドラーの詳細については、「[How to: Call an Event Handler in Visual Basic](../Topic/How%20to:%20Call%20an%20Event%20Handler%20in%20Visual%20Basic.md)」を参照してください。  
  
 `Operator` プロシージャには `Public` キーワードと `Shared` キーワードの両方が必要です。変換演算子には `Widening` キーワードか `Narrowing` キーワードのいずれかが必要です。 詳細については、「[Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)」を参照してください。  
  
 **エラー ID:** BC33003  
  
### このエラーを解決するには  
  
-   このプロシージャでイベントを処理する場合は、`Sub` プロシージャに書き換えます。  
  
-   このプロシージャに演算子を定義する場合は、その宣言から `Handles` キーワードを削除します。  
  
## 参照  
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)