---
title: "Ca 1033: インターフェイス メソッドは、子型によって呼び出し可能である必要があります |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4a9596a147ab16961d6c1396c0d367f87c6182e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: インターフェイス メソッドは、子型によって呼び出し可能でなければなりません
|||  
|-|-|  
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|  
|CheckId|CA1033|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 シールされていない外部から参照できる型によって、パブリック インターフェイスを持つメソッドを明示的に実装しています。また、同じ名前を持つ外部から参照できる代替のメソッドがありません。  
  
## <a name="rule-description"></a>規則の説明  
 パブリック インターフェイスのメソッドを明示的に実装する基本型を検討してください。 現在のインスタンスへの参照によってのみは、基本型から派生する型を継承されたインターフェイス メソッドにアクセスできます (`this` C# の場合) は、インターフェイスにキャストします。 派生型再実装する場合 (明示的)、継承されたインターフェイスのメソッド、基底の実装にアクセスできなくできます。 現在のインスタンス参照を通じて呼び出しを呼び出す派生の実装です。これにより、再帰と最終的にスタック オーバーフローします。  
  
 このルールでの明示的な実装の違反が報告されません<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>ときに、外部から参照できる`Close()`または`System.IDisposable.Dispose(Boolean)`メソッドが用意されています。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、同じ機能を公開してに派生型を表示する新しいメソッドを実装するか、非明示的な実装に変更します。 重大な変更が許容される場合は、代わりにシール型の作成を開始します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 外部から参照できるメソッドが明示的に実装されるメソッドとは異なる名前が同じ機能を持つ指定された場合、この規則による警告を抑制しても安全です。  
  
## <a name="example"></a>例  
 次の例は、型`ViolatingBase`、ルールを型に違反する`FixedBase`違反の修正プログラムを表示します。  
  
 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]  
  
## <a name="see-also"></a>参照  
 [インターフェイス](/dotnet/csharp/programming-guide/interfaces/index)