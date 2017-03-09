---
title: "CA2215: Dispose メソッドから基本クラスの破棄を呼び出します | Microsoft Docs"
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
  - "CA2215"
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "Dispose methods should call base class dispose"
helpviewer_keywords: 
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "CA2215"
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2215: Dispose メソッドから基本クラスの破棄を呼び出します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 <xref:System.IDisposable?displayProperty=fullName> を実装する型が、<xref:System.IDisposable> も実装する型から継承しています。  型を継承する <xref:System.IDisposable.Dispose%2A> メソッドで、親の型の <xref:System.IDisposable.Dispose%2A> メソッドを呼び出していません。  
  
## 規則の説明  
 型が、破棄できる型から継承している場合、使用している <xref:System.IDisposable.Dispose%2A> メソッド内から基本型の <xref:System.IDisposable.Dispose%2A> メソッドを呼び出す必要があります。  基本型メソッド Dispose を呼び出すと、基本型で作成されたリソースがすべて解放されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.IDisposable.Dispose%2A> メソッドで `base`.<xref:System.IDisposable.Dispose%2A> を呼び出します。  
  
## 警告を抑制する状況  
 `base`.<xref:System.IDisposable.Dispose%2A> の呼び出しが規則のチェック対象より深い呼び出しレベルで発生している場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 <xref:System.IDisposable> を実装する型 `TypeA` を次の例に示します。  
  
 [!CODE [FxCop.Usage.IDisposablePattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern#1)]  
  
## 使用例  
 型 `TypeA` から継承し、<xref:System.IDisposable.Dispose%2A> メソッドを正しく呼び出す型 `TypeB` を次の例に示します。  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_1.vb)]  
  
## 参照  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Dispose パターン](../Topic/Dispose%20Pattern.md)