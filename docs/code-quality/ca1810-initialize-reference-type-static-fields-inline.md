---
title: "CA1810: 参照型の静的フィールドをインラインで初期化します | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
helpviewer_keywords: 
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1810: 参照型の静的フィールドをインラインで初期化します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InitializeReferenceTypeStaticFieldsInline|  
|CheckId|CA1810|  
|分類|Microsoft.Performance|  
|互換性に影響する変更点|なし|  
  
## 原因  
 参照型で明示的な静的コンストラクターを宣言しています。  
  
## 規則の説明  
 型で明示的な静的コンストラクターを宣言すると、Just\-In\-Time \(JIT\) コンパイラが、静的コンストラクターが呼び出されたことを確認するために、型の静的メソッドと静的インスタンス コンストラクターに個別にチェックを追加します。  任意の静的メンバーがアクセスされたとき、または型のインスタンスが作成されたときに、静的な初期化が発生します。  ただし、可変の型を宣言していて使用しないと、静的な初期化は発生しません。初期化によってグローバルな状態が変化する場合、これは重要な問題になることがあります。  
  
 静的データがすべてインラインで初期化され、明示的な静的コンストラクターが宣言されていない場合、Microsoft Intermediate Language \(MSIL\) コンパイラは、`beforefieldinit` フラグと暗黙的な静的コンストラクターを追加します。これによって静的データは MSIL の型定義に初期化されます。  JIT コンパイラで `beforefieldinit` フラグが検出されると、ほとんどの場合、静的コンストラクターのチェックは追加されません。  静的な初期化は、静的フィールドにアクセスされる前に発生することは保証されていますが、静的メソッドまたは静的インスタンス コンストラクターが呼び出される前に発生することは保証されていません。  静的な初期化は、可変の型が宣言された後であればいつでも発生する可能性があることに注意してください。  
  
 静的コンストラクターのチェックによってパフォーマンスが低下することがあります。  多くの場合、静的コンストラクターは、静的フィールドを初期化するためにのみ使用されます。このとき必要なのは、静的な初期化が静的フィールドへ最初にアクセスされる前に発生することのみです。  このような場合、および他のほとんどの型の場合、`beforefieldinit` の動作は適切です。  静的な初期化によってグローバル状態に影響を及ぼし、さらに次のいずれかの条件に該当する場合は、不適切になります。  
  
-   グローバル状態に及ぼす影響のコストが高く、型を使用しなければ必要がない場合。  
  
-   型の静的フィールドにアクセスしなくても、グローバル状態の結果にアクセスできる場合。  
  
## 違反の修正方法  
 この規則違反を修正するには、静的データが宣言されたとき、および静的コンストラクターを削除するときに、静的データをすべて初期化します。  
  
## 警告を抑制する状況  
 この規則による警告を抑制しても安全なのは、パフォーマンスが重要視されていない場合、静的な初期化によるグローバル状態の変化のコストが高い場合、その型の静的メソッドが呼び出されるかその型のインスタンスが作成される前にグローバル状態の変化が発生すると保証されている必要がある場合のいずれかです。  
  
## 使用例  
 この規則に違反する型 `StaticConstructor` と、規則に適合するように静的コンストラクターをインラインの初期化で置換した型 `NoStaticConstructor` を次の例に示します。  
  
 [!CODE [FxCop.Performance.RefTypeStaticCtor#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor#1)]  
  
 `NoStaticConstructor` クラスの MSIL 定義に `beforefieldinit` フラグを追加していることに注意してください。  
  
  **.class public auto ansi StaticConstructor**  
 **extends \[mscorlib\]System.Object**  
**{**  
**} \/\/ end of class StaticConstructor**  
**.class public auto ansi beforefieldinit NoStaticConstructor**  
 **extends \[mscorlib\]System.Object**  
**{**  
**} \/\/ end of class NoStaticConstructor**   
## 関連規則  
 [CA2207: 値型のスタティック フィールドのインラインを初期化します](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)