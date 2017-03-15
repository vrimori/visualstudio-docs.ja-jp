---
title: "コンストラクターは、Function ではなく、Sub として宣言しなければなりません | Microsoft Docs"
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
  - "bc30493"
  - "vbc30493"
helpviewer_keywords: 
  - "BC30493"
ms.assetid: bcacfd4b-cac0-4ad3-a6df-5fb37c189e8f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# コンストラクターは、Function ではなく、Sub として宣言しなければなりません
`Function New` を宣言しようとしました。 コンストラクターは `Sub New` として宣言しなければなりません。  
  
 **エラー ID:** BC30493  
  
### このエラーを解決するには  
  
-   `Sub` の代わりに `Function` を使用します。  
  
## 参照  
 [Sub Statement](/dotnet/visual-basic/language-reference/statements/sub-statement)