---
title: "CA2220: ファイナライザーは基本クラスのファイナライザーを呼び出さなければなりません | Microsoft Docs"
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
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
helpviewer_keywords: 
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2220: ファイナライザーは基本クラスのファイナライザーを呼び出さなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 <xref:System.Object.Finalize%2A?displayProperty=fullName> をオーバーライドする型が、その基本クラスの <xref:System.Object.Finalize%2A> メソッドを呼び出していません。  
  
## 規則の説明  
 終了処理は、継承の階層構造を使用して反映する必要があります。  この場合、型は、型の <xref:System.Object.Finalize%2A> メソッド内から、基本クラスの <xref:System.Object.Finalize%2A> メソッドを呼び出す必要があります。  C\# コンパイラでは、基本クラスのファイナライザーへの呼び出しが自動的に追加されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.Object.Finalize%2A> メソッドからその基本型の <xref:System.Object.Finalize%2A> メソッドを呼び出します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  共通言語ランタイムを対象にするコンパイラでは、基本タイプのファイナライザーの呼び出しを Microsoft Intermediate Language \(MSIL\) に自動的に挿入するものもあります。  この規則から警告がレポートされ、呼び出しが自動的に挿入されない場合、手動でコードに追加する必要があります。  
  
## 使用例  
 次の Visual Basic コード例に、基本クラスの <xref:System.Object.Finalize%2A> メソッドを適切に呼び出している型 `TypeB` を示します。  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## 参照  
 [Dispose パターン](../Topic/Dispose%20Pattern.md)