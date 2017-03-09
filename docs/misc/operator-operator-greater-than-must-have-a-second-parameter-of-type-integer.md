---
title: "演算子 &#39;&lt;operator&gt;&#39; には、&#39;Integer&#39; 型の第 2 パラメーターを指定しなければなりません | Microsoft Docs"
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
  - "BC33041"
  - "vbc33041"
helpviewer_keywords: 
  - "BC33041"
ms.assetid: 5cd56f6d-2f0f-49de-a8e6-59bdb57bdb1d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 演算子 &#39;&lt;operator&gt;&#39; には、&#39;Integer&#39; 型の第 2 パラメーターを指定しなければなりません
ビット シフト演算子が `Integer` 以外の型の第 2 パラメーターを使って宣言されています。  
  
 式で右シフト \(`>>`\) 演算子または左シフト \(`<<`\) 演算子を使用する場合、2 番目のオペランドでシフト数を指定します。 このオペランドの場合、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では、拡大する任意のデータ型を `Integer` に提供できます。 ただし、2 番目のオペランドの定義は厳密に `Integer` です。 クラスまたは構造体をそのクラスまたは構造体のビット シフト演算子で定義する場合は、定義で 2 番目のオペランドに `Integer` を指定する必要があります。  
  
 **エラー ID:** BC33041  
  
### このエラーを解決するには  
  
-   ビット シフト演算子の定義を変更し、`Integer` 値を返すようにします。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Bit Shift Operators](/dotnet/visual-basic/language-reference/operators/bit-shift-operators)