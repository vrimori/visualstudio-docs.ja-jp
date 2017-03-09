---
title: "オーバーロードの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "関数のオーバー ロード、関数がオーバー ロードの概要"
  - "演算子のオーバー ロード、演算子のオーバー ロードの概要"
ms.assetid: cd012dd4-607c-4f8e-bd2e-2bd506ac81ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# オーバーロードの概要
C\+\+ 言語では関数と演算子をオーバーロードできます。 オーバーロードとは、特定の関数名に対し、同じスコープ内で複数の定義を与えることです。 コンパイラは、呼び出しに使用される引数に基づいて、適切なバージョンの関数または演算子を選択できます。 たとえば、関数 max はオーバーロード関数と見なされます。 次のようなコードで使用できます。  
  
```  
// overview_overload.cpp  
double max( double d1, double d2 )  
{  
   return ( d1 > d2 ) ? d1 : d2;  
}  
  
int max( int i1, int i2 )  
{  
   return ( i1 > i2 ) ? i1 : i2;  
}  
int main()  
{  
   int    i = max( 12, 8 );  
   double d = max( 32.9, 17.4 );  
}  
```  
  
 最初の変数呼び出しでは、`int` 型の 2 つの変数の最大値が要求され、関数 `max( int, int )` が呼び出されます。 ただし、2 番目の関数呼び出しでは引数が `double` 型になるため、関数 `max( double, double )` が呼び出されます。  
  
## 参照  
 [オーバー ロード \(C\+\+\)](../misc/overloading-cpp.md)