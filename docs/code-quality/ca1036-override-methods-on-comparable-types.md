---
title: "1036: ca 比較可能な型のメソッド オーバーライド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9c8eedd58df2665b9e00051e40a07a0ac226ec6c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: 比較可能な型でメソッドをオーバーライドします
|||  
|-|-|  
|TypeName|OverrideMethodsOnComparableTypes|  
|CheckId|CA1036|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 パブリックまたはプロテクト型が実装する、<xref:System.IComparable?displayProperty=fullName>インターフェイスし、オーバーライドしません<xref:System.Object.Equals%2A?displayProperty=fullName>か、等しいかどうか、非等値より大きいか小さい言語固有の演算子がオーバー ロードしません。 ルールは、型がインターフェイスの実装のみを継承する場合、違反を報告しません。  
  
## <a name="rule-description"></a>規則の説明  
 カスタムの並べ替え順序を定義する型の実装、<xref:System.IComparable>インターフェイスです。 <xref:System.IComparable.CompareTo%2A>メソッド型の 2 つのインスタンスの正しい並べ替え順序を示す整数値を返します。 この規則は、並べ替え順を設定する型を識別します。これは、"等しい"の通常の意味は、未満より大きいは適用されないことを意味します。 実装を提供するときに<xref:System.IComparable>、通常必要がありますもオーバーライド<xref:System.Object.Equals%2A>と一致する値を返すように<xref:System.IComparable.CompareTo%2A>です。 オーバーライドする場合<xref:System.Object.Equals%2A>には、コーディングと演算子のオーバー ロードをサポートする言語に合致する演算子を指定する必要がありますも<xref:System.Object.Equals%2A>します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、オーバーライド<xref:System.Object.Equals%2A>です。 使用するプログラミング言語では、演算子のオーバー ロードをサポートする場合は、次の演算子を指定します。  
  
-   op_Equality  
  
-   op_Inequality  
  
-   op_LessThan  
  
-   op_GreaterThan  
  
 C# の場合、これらの演算子を表すために使用されるトークンは次のように: = =、! =、 \<、および >。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 演算子がないために違反が発生し、使用するプログラミング言語がサポートされない演算子のオーバー ロードすると、Visual Basic .NET の場合は、この規則による警告を抑制しても安全です。 発生したときに等値演算子で op_Equality 演算子を実装するいると判断した場合は、アプリケーションのコンテキストで意味を持ちません場合を除いてのこの規則による警告を抑制しても安全です。 ただしは常に op_Equality 経由、および演算子を = =、Object.Equals をオーバーライドする場合。  
  
## <a name="example"></a>例  
 次の例には、正しく実装する型が含まれています。<xref:System.IComparable>です。 コードのコメントに関連するさまざまなルールに適合するメソッドを識別する<xref:System.Object.Equals%2A>と<xref:System.IComparable>インターフェイスです。  
  
 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## <a name="example"></a>例  
 次のアプリケーションの動作をテストする、<xref:System.IComparable>前に示したが実装されます。  
  
 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## <a name="see-also"></a>参照  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [等値演算子](/dotnet/standard/design-guidelines/equality-operators)