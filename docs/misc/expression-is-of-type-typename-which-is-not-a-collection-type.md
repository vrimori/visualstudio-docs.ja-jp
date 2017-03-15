---
title: "式の型は &#39;&lt;typename&gt;&#39; で、コレクション型ではありません。 | Microsoft Docs"
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
  - "bc32023"
  - "vbc32023"
helpviewer_keywords: 
  - "BC32023"
ms.assetid: d0f151be-6b65-498b-b571-03faf24df0d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 式の型は &#39;&lt;typename&gt;&#39; で、コレクション型ではありません。
`For Each` ステートメントで指定されたグループ変数は、コレクション オブジェクトまたは配列ではなく、その型が <xref:System.Collections.IEnumerable> インターフェイスを実装していません。 型は、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コレクションのデザイン パターンをサポートしているか、または <xref:System.Collections.IEnumerable> を実装している必要があります。  
  
 **エラー ID:** BC32023  
  
### このエラーを解決するには  
  
-   [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コレクションのデザインをサポートしているか、または <xref:System.Collections.IEnumerable> を実装しているクラス型にするグループ変数を宣言します。  
  
## 参照  
 <xref:System.Collections.IEnumerable>   
 [For Each...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [Visual Basic のコレクション クラス](http://msdn.microsoft.com/ja-jp/0cb2d1ad-c58d-42c0-8e69-d81f5a15e532)