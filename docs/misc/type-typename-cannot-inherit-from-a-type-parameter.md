---
title: "&#39;&lt;typename&gt;&#39; は、型パラメーターから継承することはできません。 | Microsoft Docs"
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
  - "bc32055"
  - "vbc32055"
helpviewer_keywords: 
  - "BC32055"
ms.assetid: 97af7cad-6e40-41e3-892d-1fbcbd86356d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; は、型パラメーターから継承することはできません。
クラスまたはインターフェイスに、ジェネリック型パラメーターを指定する [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement) が含まれています。  
  
 まだ定義されていない型から、型を継承することはできません。 継承には基底クラスのメンバーを再利用する機能が関与するため、これらのメンバーが定義されている必要があります。 ジェネリック型パラメーターは、型引数で指定した特定の型によって置き換えられるプレースホルダーです。 そのため、型をプレースホルダーから継承することはできません。  
  
 **エラー ID:** BC32055  
  
### このエラーを解決するには  
  
-   継承型を別の型から継承する必要がある場合は、型パラメーターではなく、特定の型を使用します。  
  
-   基本型をジェネリック型パラメーターで表す必要がある場合、他の型がこの型を継承することはできません。[Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement) を削除します。  
  
## 参照  
 [ビルド内にありません: Visual Basic の継承](http://msdn.microsoft.com/ja-jp/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)