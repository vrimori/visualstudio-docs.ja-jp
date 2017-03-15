---
title: "インターフェイス &#39;&lt;interfacename&gt;&#39; は、このクラスによって実装されていません | Microsoft Docs"
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
  - "bc31035"
  - "vbc31035"
helpviewer_keywords: 
  - "BC31035"
ms.assetid: 99ddabb5-20e0-4cf6-a8d4-1ca91f3c7511
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# インターフェイス &#39;&lt;interfacename&gt;&#39; は、このクラスによって実装されていません
このクラスまたは構造体のメンバーが、このクラスまたは構造体に実装されていないインターフェイスのメンバーを実装しようとしています。  
  
 **エラー ID:** BC31035  
  
### このエラーを解決するには  
  
-   クラスまたは構造体の先頭に `Implements` ステートメントを追加して、適切なインターフェイスを実装します。  
  
-   このエラーの原因であるメンバーから、`Implements` キーワードを削除します。  
  
## 参照  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)