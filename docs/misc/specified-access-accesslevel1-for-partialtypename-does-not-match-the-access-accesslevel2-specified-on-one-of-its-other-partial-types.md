---
title: "&#39;&lt;partialtypename&gt;&#39; に指定されているアクセス &#39;&lt;accesslevel1&gt;&#39; は、その他の部分型の 1 つで指定されているアクセス &#39;&lt;accesslevel2&gt;&#39; と一致しません | Microsoft Docs"
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
  - "vbc30925"
  - "BC30925"
helpviewer_keywords: 
  - "BC30925"
ms.assetid: aabe0f4a-dc02-4828-a837-20cd47a7bd43
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;partialtypename&gt;&#39; に指定されているアクセス &#39;&lt;accesslevel1&gt;&#39; は、その他の部分型の 1 つで指定されているアクセス &#39;&lt;accesslevel2&gt;&#39; と一致しません
クラスまたは構造体が、競合するアクセス レベル指定を持つ複数の部分宣言で定義されています。  
  
 クラスまたは構造体の定義を複数の部分宣言で分割すると、コンパイラは、そのすべての部分宣言の和集合としてこの型を処理します。 このことは、メンバーだけでなく、実装、継承、アクセス レベルにも該当します。  
  
 クラスまたは構造体の定義でアクセス レベルを混在させることはできません。 組み合わせ `Protected Friend` でさえ、キーワードが同じ宣言ステートメント内で連続している場合に限り許可されます。  
  
 **エラー ID:** BC30925  
  
### このエラーを解決するには  
  
-   クラスで必要なアクセス レベルを判別し、競合しているアクセス レベルの指定を削除します。  
  
## 参照  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [ビルド内にありません: クラス: オブジェクトの設計図](http://msdn.microsoft.com/ja-jp/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Structures](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)