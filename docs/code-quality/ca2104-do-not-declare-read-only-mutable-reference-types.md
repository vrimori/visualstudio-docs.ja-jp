---
title: "CA2104: 読み取り専用の変更可能な参照型を宣言しません | Microsoft Docs"
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
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
  - "CA2104"
helpviewer_keywords: 
  - "CA2104"
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2104: 読み取り専用の変更可能な参照型を宣言しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|  
|CheckId|CA2104|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|なし|  
  
## 原因  
 外部から参照できる型に、変更可能な参照型である、外部から参照可能な読み取り専用のフィールドがあります。  
  
## 規則の説明  
 変更可能な型とは、インスタンス データを変更できる型です。  <xref:System.Text.StringBuilder?displayProperty=fullName> クラスは、変更可能な参照型の一例です。  このクラスには、クラスのインスタンス値を変更できるメンバーが含まれます。  変更できない参照型の例は、<xref:System.String?displayProperty=fullName> クラスです。  インスタンス化された後に、値を変更できません。  
  
 参照型フィールド \(C\+\+ ではポインター\) に、読み取り専用の修飾子 \(C\# では [readonly](/dotnet/csharp/language-reference/keywords/readonly)、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)、C\+\+ では [const](/visual-cpp/cpp/const-cpp)\) を指定すると、フィールドを別インスタンスの参照型で置換できなくなります。  ただし、参照型を使用してフィールドのインスタンス データが変更されるのを防ぐことはできません。  
  
 読み取り専用の配列フィールドはこの規則の対象外ですが、別の「[CA2105: 配列フィールドは読み取り専用にできません](../code-quality/ca2105-array-fields-should-not-be-read-only.md)」規則に違反します。  
  
## 違反の修正方法  
 この規則違反を修正するには、読み取り専用の修飾子を削除します。または互換性に影響する変更点を許容できる場合、変更できない型でフィールドを置換します。  
  
## 警告を抑制する状況  
 フィールドの型を変更できない場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 この規則に違反するフィールドの宣言を次の例に示します。  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-cs[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]