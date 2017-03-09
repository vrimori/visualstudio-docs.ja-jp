---
title: "例外のトラブルシューティング : System.OverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "OverflowException クラス"
ms.assetid: bd380db7-5d05-4d7f-be5b-e654fdadf14c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.OverflowException
<xref:System.OverflowException> 例外は、checked コンテキストの算術演算、キャスト演算、または変換演算でオーバーフローが発生するとスローされます。 演算の結果、格納先の型に対して大きすぎる値、無限大、または非数 \(NaN\) が生成されると、オーバーフローが発生します。  
  
## 関連するヒント  
 **数値からキャストする場合、値は無限大より小さい有効な数値であることが必要です。**  
 キャスト元の値には、無限大や非数を指定できません。  
  
 **0 で除算していないことを確認します。**  
 ゼロで除算すると、通常、この例外が発生します。  
  
## コメント  
 オーバーフローが検出される言語では、オーバーフローが発生すると <xref:System.OverflowException> 例外がスローされます。 たとえば C\# の場合、`checked` キーワードを使用してオーバーフロー状態が検出されます。<xref:System.OverflowException> 例外は、checked コンテキストだけで発生します。  
  
 整数型または小数型の算術演算や変換による結果が格納先の型の範囲外である場合、次の事態が発生します。  
  
-   checked コンテキストでは、演算が定数式の場合はコンパイル エラーが発生します。 それ以外の場合は、実行時に演算が実行されると <xref:System.OverflowException> 例外がスローされます。  
  
-   unchecked コンテキストでは、結果の格納先の型に収まらない上位ビットが破棄されて、結果が切り詰められます。  
  
 データ型の値の範囲については、「[Data Types](/dotnet/visual-basic/language-reference/data-types/data-type-summary)」、「[整数型の一覧表](/dotnet/csharp/language-reference/keywords/integral-types-table)」、または「[浮動小数点型の一覧表](/dotnet/csharp/language-reference/keywords/floating-point-types-table)」をご覧ください。  
  
## 参照  
 <xref:System.OverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)