---
title: "CA2216: 破棄できる型ではファイナライザーを宣言します | Microsoft Docs"
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
  - "DisposableTypesShouldDeclareFinalizer"
  - "CA2216"
helpviewer_keywords: 
  - "CA2216"
  - "DisposableTypesShouldDeclareFinalizer"
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2216: 破棄できる型ではファイナライザーを宣言します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposableTypesShouldDeclareFinalizer|  
|CheckId|CA2216|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 <xref:System.IDisposable?displayProperty=fullName> を実装し、アンマネージ リソースの使用を提案するフィールドが含まれる型では、<xref:System.Object.Finalize%2A?displayProperty=fullName> で記述するようにファイナライザーを実装していません。  
  
## 規則の説明  
 この規則違反は、破棄できる型に次の種類のフィールドが含まれるときにレポートされます。  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.IDisposable.Dispose%2A> メソッドを呼び出すファイナライザーを実装します。  
  
## 警告を抑制する状況  
 アンマネージ リソースを解放する目的で型に <xref:System.IDisposable> を実装していない場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 この規則に違反する型を次の例に示します。  
  
 [!code-cs[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]  
  
## 関連規則  
 [CA2115: ネイティブ リソースを使用しているときには GC.KeepAlive を呼び出します](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)  
  
 [CA1816: GC.SuppressFinalize を正しく呼び出します](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA1049: ネイティブ リソースを所有する型は、破棄可能でなければなりません](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)  
  
## 参照  
 <xref:System.IDisposable?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [Dispose パターン](../Topic/Dispose%20Pattern.md)