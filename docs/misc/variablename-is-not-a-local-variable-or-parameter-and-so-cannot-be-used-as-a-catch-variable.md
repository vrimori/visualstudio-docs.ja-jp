---
title: "&#39;&lt;variablename&gt;&#39; はローカル変数またはパラメーターでないため、&#39;Catch&#39; 変数として使うことはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31082"
  - "vbc31082"
helpviewer_keywords: 
  - "BC31082"
ms.assetid: de197563-5848-4c1a-a519-cc4b5ea9a4c9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;variablename&gt;&#39; はローカル変数またはパラメーターでないため、&#39;Catch&#39; 変数として使うことはできません
`Try...Catch...Finally` ステートメント内の変数は、ローカルで宣言されているか、現在のプロシージャのパラメーターである必要があります。  
  
 **エラー ID:** BC31082  
  
### このエラーを解決するには  
  
1.  `Try...Catch...Finally` ステートメントのローカル変数またはパラメーターを宣言します。  
  
## 参照  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)