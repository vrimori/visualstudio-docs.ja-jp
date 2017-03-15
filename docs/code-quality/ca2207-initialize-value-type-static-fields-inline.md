---
title: "CA2207: 値型のスタティック フィールドのインラインを初期化します | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InitializeValueTypeStaticFieldsInline"
  - "CA2207"
helpviewer_keywords: 
  - "CA2207"
  - "InitializeValueTypeStaticFieldsInline"
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2207: 値型のスタティック フィールドのインラインを初期化します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InitializeValueTypeStaticFieldsInline|  
|CheckId|CA2207|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 値型で明示的な静的コンストラクターを宣言しています。  
  
## 規則の説明  
 値型を宣言すると、既定の初期化が行われます。このとき、値型のフィールドはすべてゼロに設定され、参照型のフィールドはすべて `null` \(Visual Basic では `Nothing`\) に設定されます。  明示的な静的コンストラクターは、インスタンス コンストラクターまたはその型の静的メンバーが呼び出される前に実行することが保証されているだけです。  そのため、インスタンス コンストラクターを呼び出さずに型が作成されると、静的コンストラクターの実行は保証されません。  
  
 静的データがインラインで初期化され、明示的な静的コンストラクターが宣言されない場合、C\# と Visual Basic のコンパイラによって MSIL クラス定義に `beforefieldinit` フラグが追加されます。  また、コンパイラによって、静的な初期化コードを含むプライベートの静的コンストラクターも追加されます。  プライベートの静的コンストラクターは、型の静的フィールドのいずれかにアクセスする前に実行することが保証されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、静的データが宣言されたとき、および静的コンストラクターを削除するときに、静的データをすべて初期化します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 関連規則  
 [CA1810: 参照型の静的フィールドをインラインで初期化します](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)