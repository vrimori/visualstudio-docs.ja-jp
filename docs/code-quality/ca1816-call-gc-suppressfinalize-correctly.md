---
title: "CA1816: GC.SuppressFinalize を正しく呼び出します | Microsoft Docs"
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
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
helpviewer_keywords: 
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1816: GC.SuppressFinalize を正しく呼び出します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|分類|Microsoft.  使用法|  
|互換性に影響する変更点|なし|  
  
## 原因  
  
-   <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> を実装するメソッドで、<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> を呼び出していません。  
  
-   <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> を実装しないメソッドで、<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> を呼び出しています。  
  
-   メソッドが <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> を呼び出し、this  \(Visual Basic では Me\) 以外の値を渡します。  
  
## 規則の説明  
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> メソッドを使用すると、オブジェクトがガベージ コレクションで使用できるようになる前であれば、任意のタイミングでリソースを解放できます。  <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> メソッドを呼び出すと、オブジェクトのリソースが解放されます。  これにより、終了処理が不要になります。  <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> は <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> を呼び出します。こうすることで、ガベージ コレクターからオブジェクトのファイナライザーは呼び出されません。  
  
 ファイナライザーを持つ派生型で [System.IDisposable](assetId:///System.IDisposable?qualifyHint=True&autoUpgrade=False) の再実装および呼び出しを行わなくて済むようにするには、ファイナライザーを持たない、シールされていない型で <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> を呼び出す必要があります。  
  
## 違反の修正方法  
 この規則違反を修正するには  
  
 メソッドで <xref:System.IDisposable.Dispose%2A> を実装する場合は、<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> の呼び出しを追加します。  
  
 メソッドで <xref:System.IDisposable.Dispose%2A> を実装しない場合は、<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> の呼び出しを、削除するか、型の <xref:System.IDisposable.Dispose%2A> 実装に移動します。  
  
 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> のすべての呼び出しを変更して、this \(Visual Basic では Me\) を渡すようにします。  
  
## 警告を抑制する状況  
 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> を使用して他のオブジェクトの有効期間を制御する場合にのみ、この規則による警告を抑制します。  <xref:System.IDisposable.Dispose%2A> の実装で <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> を呼び出さない場合は、この規則による警告を抑制しないでください。  終了処理を省略した場合のエラーによってパフォーマンスが低下します。また何も利点がありません。  
  
## 使用例  
 次の例は、<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> を正しく呼び出さないメソッドを示しています。  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-cs[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## 使用例  
 次に、<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> を正しく呼び出しているメソッドの例を示します。  
  
 [!CODE [FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1)]  
  
## 関連規則  
 [CA2215: Dispose メソッドから基本クラスの破棄を呼び出します](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216: 破棄できる型ではファイナライザーを宣言します](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## 参照  
 [Dispose パターン](../Topic/Dispose%20Pattern.md)