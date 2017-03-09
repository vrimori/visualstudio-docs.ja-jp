---
title: "型パラメーター名 &#39;&lt;typeparametername1&gt;&#39; は、&#39;&lt;partialtypename&gt;&#39; のその他の partial 型の 1 つに対して定義されている、対応する型パラメーターの名前 &#39;&lt;typeparametername2&gt;&#39; と一致しません。 | Microsoft Docs"
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
  - "vbc30931"
  - "bc30931"
helpviewer_keywords: 
  - "BC30931"
ms.assetid: 01b053c3-d1b5-4e69-b908-3d5cfc73913b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーター名 &#39;&lt;typeparametername1&gt;&#39; は、&#39;&lt;partialtypename&gt;&#39; のその他の partial 型の 1 つに対して定義されている、対応する型パラメーターの名前 &#39;&lt;typeparametername2&gt;&#39; と一致しません。
ジェネリック クラスまたは構造体は、競合する型パラメーターが指定された複数の部分宣言で定義されています。  
  
 クラスまたは構造体の定義を複数の部分宣言間で分割する際、コンパイラは、そのすべての部分宣言の和集合としてこの型を処理します。 このことは、メンバーだけでなく、実装、継承、およびアクセス レベルにも該当します。  
  
 ジェネリック クラスまたは構造体の定義で、型パラメーターに対して複数の名前を指定することはできません。  
  
 **エラー ID:** BC30931  
  
### このエラーを解決するには  
  
-   型パラメーターに必要な名前を決定し、すべての部分宣言でこの同じ名前を使用します。  
  
## 参照  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Structure Statement](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [ビルド内にありません: クラス: オブジェクトの設計図](http://msdn.microsoft.com/ja-jp/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Structures](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)