---
title: "ステートメントは、&#39;Get&#39; または &#39;Set&#39; メソッドを宣言しません | Microsoft Docs"
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
  - "bc30576"
  - "vbc30576"
helpviewer_keywords: 
  - "BC30576"
ms.assetid: 0f5aabd8-7cd0-4eaa-ae92-67be260cf63e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ステートメントは、&#39;Get&#39; または &#39;Set&#39; メソッドを宣言しません
ステートメントには、`Property` プロシージャの周囲に `Get` または `Set` 宣言ステートメントが指定されていません。 プロパティは、`Property` および `End Property` ステートメントの中に囲まれたコードのブロックとして定義します。 このブロック内では、各 `Property` プロシージャが、宣言ステートメントと End ステートメントの中に囲まれた内部ブロックとしてを記述されます。  
  
 **エラー ID:** BC30576  
  
### このエラーを解決するには  
  
-   `Get` または `Set` 宣言ステートメントを指定します。  
  
## 参照  
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)