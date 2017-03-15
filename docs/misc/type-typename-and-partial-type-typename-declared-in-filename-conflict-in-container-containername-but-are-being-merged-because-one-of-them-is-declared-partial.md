---
title: "&#39;&lt;filename&gt;&#39; で宣言された型 &#39;&lt;typename&gt;&#39; と部分型 &#39;&lt;typename&gt;&#39; がコンテナー &#39;&lt;containername&gt;&#39; で競合しますが、そのうち 1 つが部分的な宣言であるためマージされました | Microsoft Docs"
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
  - "vbc40047"
  - "bc40047"
helpviewer_keywords: 
  - "BC40047"
ms.assetid: 05f62dd9-f97d-4893-8904-76ecd2da474c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;filename&gt;&#39; で宣言された型 &#39;&lt;typename&gt;&#39; と部分型 &#39;&lt;typename&gt;&#39; がコンテナー &#39;&lt;containername&gt;&#39; で競合しますが、そのうち 1 つが部分的な宣言であるためマージされました
クラスまたは構造体が同じ種類のコンテナーの複数の定義に表示され、複数の定義が `Partial` とマークされていません。  
  
 クラスまたは構造体の複数の定義のうち、少なくとも 1 つで [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) キーワードを使用する必要がありますが、すべての部分定義で使用することをお勧めします。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40047  
  
### このエラーを解決するには  
  
-   クラスまたは構造体のすべての部分定義で [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) キーワードを使用します。