---
title: "1001: 破棄可能なフィールドを所有する型は、破棄可能でなければなりません |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 30609be8b70f65cb48478c6d6d2c0f3b6d89a029
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: 破棄可能なフィールドを所有する型は、破棄可能でなければなりません
|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|CheckId|CA1001|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|改行の種類がアセンブリの外側に表示されていない場合。<br /><br /> – 型は、アセンブリ外部から参照できる場合です。|  
  
## <a name="cause"></a>原因  
 クラスの宣言およびインスタンス フィールドを実装する<xref:System.IDisposable?displayProperty=fullName>型とクラスを実装していません<xref:System.IDisposable>です。  
  
## <a name="rule-description"></a>規則の説明  
 クラスを実装する、<xref:System.IDisposable>所有しているアンマネージ リソースを破棄するインターフェイスです。 インスタンス フィールドを<xref:System.IDisposable>型では、フィールドをアンマネージ リソースを所有していることを示します。 宣言するクラス、<xref:System.IDisposable>フィールドを間接的にアンマネージ リソースを所有して実装する必要があります、<xref:System.IDisposable>インターフェイスです。 クラスは、アンマネージ リソースを直接所有していない、ファイナライザーを実装する必要があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、実装<xref:System.IDisposable>との間、<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>メソッドの呼び出し、<xref:System.IDisposable.Dispose%2A>フィールドのメソッドです。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例は、規則に違反するクラスとクラスを実装することによって、ルールを満たす<xref:System.IDisposable>です。 クラスは、クラスがアンマネージ リソースを直接所有していないために、ファイナライザーを実装しません。  
  
 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA2213: 破棄可能なフィールドは破棄されなければなりません](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216: 破棄できる型ではファイナライザーを宣言します](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215: Dispose メソッドから基本クラスの破棄を呼び出します](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049: ネイティブ リソースを所有する型は、破棄可能でなければなりません](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)