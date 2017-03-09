---
title: "型 &#39;&lt;typename&gt;&#39; と部分型 &#39;&lt;typename&gt;&#39; がコンテナー &#39;&lt;containername&gt;&#39; で競合しますが、そのうち 1 つが部分として宣言されているためマージされます | Microsoft Docs"
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
  - "bc40046"
  - "vbc40046"
helpviewer_keywords: 
  - "BC40046"
ms.assetid: c243e70b-ecd5-49ef-a260-a7bb12a4a3b1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型 &#39;&lt;typename&gt;&#39; と部分型 &#39;&lt;typename&gt;&#39; がコンテナー &#39;&lt;containername&gt;&#39; で競合しますが、そのうち 1 つが部分として宣言されているためマージされます
1 つのクラスまたは構造体が同じコンテナー型の複数の定義で使用されており、複数の定義が `Partial` としてマークされていません。  
  
 クラスまたは構造体の複数の定義のうち、少なくとも 1 つで [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) キーワードを使用する必要がありますが、すべての部分定義で使用することをお勧めします。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」をご覧ください。  
  
 **エラー ID:** BC40046  
  
### このエラーを解決するには  
  
-   クラスまたは構造体のすべての部分定義で [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) キーワードを使用します。  
  
## 参照  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)