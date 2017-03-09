---
title: "&#39;&lt;member&gt;&#39; は、すべての Enum で暗黙的に宣言されている、同じ名前の予約メンバーと競合しています | Microsoft Docs"
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
  - "bc31420"
  - "vbc31420"
helpviewer_keywords: 
  - "BC31420"
ms.assetid: f2ea5a8b-f63c-4c93-bfac-418ae5a150a5
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;member&gt;&#39; は、すべての Enum で暗黙的に宣言されている、同じ名前の予約メンバーと競合しています
型メンバーの名前が、すべての列挙体で暗黙的に宣言されている名前と競合します。  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラは、宣言されている特定のプログラミング要素に対応して、暗黙的なメンバーを作成します。 列挙体は暗黙的にメンバー `value__member` を宣言します。  
  
 **エラー ID:** BC31420  
  
### このエラーを解決するには  
  
-   メンバーの名前を変更します。  
  
## 参照  
 [NotInBuild:Visual Basic における宣言ステートメント](http://msdn.microsoft.com/ja-jp/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [Enumerations Overview](/dotnet/visual-basic/programming-guide/language-features/constants-enums/enumerations-overview)   
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)