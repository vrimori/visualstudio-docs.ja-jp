---
title: "CA1046: 参照型で、演算子 equals をオーバー ロードしない |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 344dfe7a4e35bf42e9e0a4efb2ca9bdf1b8f5d6b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: 参照型で、演算子 equals をオーバーロードしないでください
|||  
|-|-|  
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリックまたは入れ子になったパブリック参照型では、等値演算子がオーバー ロードします。  
  
## <a name="rule-description"></a>規則の説明  
 参照型の場合、等値演算子は既定の実装でほぼ問題がありません。 既定で、2 つの参照が等値と見なされるのは、同じオブジェクトを参照する場合のみです。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、等値演算子の実装を削除します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 参照型が組み込みの値の型と同様に動作する場合は、この規則による警告を抑制するのには安全です。 型のインスタンスで加算または減算を実行する意味である場合、正しく可能性があります、等値演算子を実装して、抑制する状況、違反が発生します。  
  
## <a name="example"></a>例  
 次の例は、2 つの参照を比較するときに、既定の動作を示します。  
  
 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## <a name="example"></a>例  
 次のアプリケーションでは、いくつかの参照を比較します。  
  
 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
 **新しい (2, 2) と b を = = 新しい (2, 2) が等しいか?違います**  
**c とが等しいか。うん**  
**b は = = しますか?違います**  
**c は = = しますか?うん**   
## <a name="related-rules"></a>関連規則  
 [CA1013: オーバーロードする加算および減算で、演算子 equals をオーバーロードします](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [等値演算子](/dotnet/standard/design-guidelines/equality-operators)