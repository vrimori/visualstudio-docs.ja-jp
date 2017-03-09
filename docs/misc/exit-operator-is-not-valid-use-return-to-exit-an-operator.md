---
title: "&#39;Exit Operator&#39; は有効ではありません。 演算子を終了するには、&#39;Return&#39; を使用してください。 | Microsoft Docs"
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
  - "bc33008"
  - "vbc33008"
helpviewer_keywords: 
  - "BC33008"
ms.assetid: 8c44456b-8fd2-4168-ad8c-b6da129242ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Operator&#39; は有効ではありません。 演算子を終了するには、&#39;Return&#39; を使用してください。
`Exit Operator` ステートメントが `Operator` プロシージャに含まれています。  
  
 `Operator` プロシージャから戻るには、[Return Statement](/dotnet/visual-basic/language-reference/statements/return-statement) を使用する必要があります。[Exit Statement](/dotnet/visual-basic/language-reference/statements/exit-statement) では `Operator` キーワードを使用できず、`End Operator` ステートメントが呼び出し元コードに制御を返しません。  
  
 **エラー ID:** BC33008  
  
### このエラーを解決するには  
  
-   `Exit Operator` ステートメントを `Return` ステートメントに置き換えます。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)