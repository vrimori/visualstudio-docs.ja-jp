---
title: "CA1049: ネイティブ リソースを所有する型は、破棄可能でなければなりません | Microsoft Docs"
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
  - "CA1049"
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
helpviewer_keywords: 
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
  - "CA1049"
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1049: ネイティブ リソースを所有する型は、破棄可能でなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|  
|CheckId|CA1049|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 ある型が <xref:System.IntPtr?displayProperty=fullName> フィールド、<xref:System.UIntPtr?displayProperty=fullName> フィールド、または <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> フィールドを参照していますが、<xref:System.IDisposable?displayProperty=fullName> を参照していません。  
  
## 規則の説明  
 この規則では、<xref:System.IntPtr>、<xref:System.UIntPtr>、および <xref:System.Runtime.InteropServices.HandleRef> の各フィールドに、アンマネージ リソースへのポインターが格納されていると仮定しています。  アンマネージ リソースを割り当てる型では、<xref:System.IDisposable> を実装することで、呼び出し元が必要に応じてリソースを解放し、リソースを保持するオブジェクトの有効期間を短縮できるようにする必要があります。  
  
 アンマネージ リソースをクリーンアップするデザイン方法として、<xref:System.Object.Finalize%2A?displayProperty=fullName> メソッド \(暗黙的\) と <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> メソッド \(明示的\) を使用して、リソースを解放する手法を実現することが推奨されます。  ガベージ コレクターは、オブジェクトにアクセスできないと判断した後、ある時点でオブジェクトの <xref:System.Object.Finalize%2A> メソッドを呼び出します。  <xref:System.Object.Finalize%2A> が呼び出された後に、追加のガベージ コレクションでオブジェクトを解放する必要があります。  <xref:System.IDisposable.Dispose%2A> メソッドを使用すると、ガベージ コレクターの処理に任せてリソースを解放する場合よりも早く、呼び出し元の必要に応じて明示的にリソースを解放できます。  アンマネージ リソースをクリーンアップした後に、<xref:System.IDisposable.Dispose%2A> で <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> メソッドを呼び出し、<xref:System.Object.Finalize%2A> を呼び出す必要はなくなったことをガベージ コレクターに通知します。これによって、追加のガベージ コレクションが必要なくなり、オブジェクトの有効期間が短くなります。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.IDisposable> を実装します。  
  
## 警告を抑制する状況  
 型でアンマネージ リソースを参照していない場合は、この規則による警告を抑制しても安全です。  それ以外の場合、この規則による警告を抑制しないでください。<xref:System.IDisposable> の実装に失敗すると、アンマネージ リソースが使用できなくなったり、十分に活用できなくなったりします。  
  
## 使用例  
 アンマネージ リソースをクリーンアップする <xref:System.IDisposable> を実装する型を次の例に示します。  
  
 [!code-cs[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]  
  
## 関連規則  
 [CA2115: ネイティブ リソースを使用しているときには GC.KeepAlive を呼び出します](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)  
  
 [CA1816: GC.SuppressFinalize を正しく呼び出します](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA2216: 破棄できる型ではファイナライザーを宣言します](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA1001: 破棄可能なフィールドを所有する型は、破棄可能でなければなりません](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)  
  
## 参照  
 [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)   
 [Dispose パターン](../Topic/Dispose%20Pattern.md)