---
title: "&#39;&lt;method&gt;&#39; は &#39;&lt;modifier&gt;&#39; であるため、このコンテキストではアクセスできません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30389"
  - "bc30389"
helpviewer_keywords: 
  - "BC30389"
ms.assetid: fae58a68-df91-4741-a8c9-f1bb10e166e2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;method&gt;&#39; は &#39;&lt;modifier&gt;&#39; であるため、このコンテキストではアクセスできません
`Private` で宣言されているために、このコンテキストでアクセスできないメソッドにアクセスしようとしました。 このエラーの考えられる原因は、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラがクラスのすべてのメンバーをインポートし、大文字と小文字を区別しないため、小文字だけが異なる名前が競合する可能性があることです。  
  
 **エラー ID:** BC30389  
  
### このエラーを解決するには  
  
-   メソッド `Public` を宣言することを検討してください。  
  
-   エラーの原因が名前の競合である場合は、大文字\/小文字以外で衝突している名前を区別します。  
  
## 参照  
 [Private](/dotnet/visual-basic/language-reference/modifiers/private)