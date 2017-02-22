---
title: "CA1802: 適切な場所にリテラルを使用します | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
helpviewer_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1802: 適切な場所にリテラルを使用します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|分類|Microsoft.Performance|  
|互換性に影響する変更点|なし|  
  
## 原因  
 フィールドが `static` および `readonly` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では `Shared` および `ReadOnly`\) として宣言され、コンパイル時に計算できる値によって初期化されています。  
  
## 規則の説明  
 宣言型の静的コンストラクターが呼び出されると、`static` `readonly` フィールドの値は実行時に計算されます。  `static` `readonly` フィールドが宣言されるときに初期化され、静的コンストラクターが明示的に宣言されなかった場合、コンパイラは静的コンストラクターを出力してフィールドを初期化します。  
  
 `const` フィールドの値は、コンパイル時に計算され、メタデータに格納されます。その結果、`static` `readonly` フィールドに比べて実行時のパフォーマンスが向上します。  
  
 対象フィールドに代入された値はコンパイル時に計算できるので、宣言を `const` フィールドに変更して、値が実行時ではなくコンパイル時に計算されるようにします。  
  
## 違反の修正方法  
 この規則の違反を修正するには、`static` 修飾子および `readonly` 修飾子を `const` 修飾子で置き換えます。  
  
## 警告を抑制する状況  
 パフォーマンスを重視しない場合は、この規則による警告を抑制するか、または規則を無効にしても安全です。  
  
## 使用例  
 この規則に違反している型 `UseReadOnly` と、規則に適合する型 `UseConstant` を次の例に示します。  
  
 [!CODE [FxCop.Performance.UseLiterals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals#1)]