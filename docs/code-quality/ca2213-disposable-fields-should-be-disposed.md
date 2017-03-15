---
title: "CA2213: 破棄可能なフィールドは破棄されなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DisposableFieldsShouldBeDisposed"
  - "CA2213"
helpviewer_keywords: 
  - "CA2213"
  - "DisposableFieldsShouldBeDisposed"
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2213: 破棄可能なフィールドは破棄されなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 <xref:System.IDisposable?displayProperty=fullName> を実装する型が、<xref:System.IDisposable> を実装している型も持つフィールドを宣言しています。  このフィールドの <xref:System.IDisposable.Dispose%2A> メソッドは、宣言している型の <xref:System.IDisposable.Dispose%2A> メソッドから呼び出されていません。  
  
## 規則の説明  
 型は、アンマネージ リソースのすべての破棄に責任があります。これは、<xref:System.IDisposable> を実装することで実現します。  この規則で、破棄できる型 `T` が、破棄できる型 `FT` のインスタンスであるフィールド `F` を宣言しているかどうかがチェックされます。  `F` フィールドごとに、`FT.Dispose` の呼び出し位置が特定されます。  また、`T.Dispose` から呼び出されたメソッドと、1 レベル低いメソッド \(`FT.Dispose` によって呼び出されたメソッドから呼び出されたメソッド\) を検索します。  
  
## 違反の修正方法  
 <xref:System.IDisposable> を実装する型を持つフィールドで保持されるアンマネージ リソースの割り当てと解放を行うコードを担当している場合、この規則違反を修正するには、このフィールドで <xref:System.IDisposable.Dispose%2A> を呼び出します。  
  
## 警告を抑制する状況  
 このフィールドで保持されているリソースを解放するコードを担当していない場合、または <xref:System.IDisposable.Dispose%2A> の呼び出しがこの規則でチェックされる呼び出しレベルよりも深いレベルで発生する場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 <xref:System.IDisposable> を実装する型 `TypeA` \(上記の説明では `FT`\) を次の例に示します。  
  
 [!CODE [FxCop.Usage.IDisposablePattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern#1)]  
  
## 使用例  
 この規則に違反する型 `TypeB` を次の例に示します。この型は、フィールド `aFieldOfADisposableType` \(上の説明では `F`\) を破棄できる型 \(`TypeA`\) として宣言し、フィールドで <xref:System.IDisposable.Dispose%2A> を呼び出していないため、規則違反です。  `TypeB` は、上の説明の `T` に相当します。  
  
 [!code-cs[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## 参照  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Dispose パターン](../Topic/Dispose%20Pattern.md)