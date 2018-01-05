---
title: "Ca 1819: プロパティは配列を返すできません |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cc11a71b9f6a68db2d795694af0326561b235f8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: プロパティは、配列を返すことはできません
|||  
|-|-|  
|TypeName|PropertiesShouldNotReturnArrays|  
|CheckId|CA1819|  
|カテゴリ|Microsoft.Performance|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリック型の public または protected のプロパティは、配列を返します。  
  
## <a name="rule-description"></a>規則の説明  
 プロパティによって返される配列は書き込みで保護されている場合でも、このプロパティは読み取り専用 配列の改ざんを防ぐには、プロパティで配列のコピーを返す必要があります。 一般に、このようなプロパティを呼び出すときのパフォーマンス低下は理解されません。 具体的には、インデックス付きプロパティとしてプロパティを使用する可能性があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、か、プロパティ、メソッドまたはコレクションを取得するプロパティを変更します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 属性は、配列を返すプロパティを含めることができますが、コレクションを返すプロパティを含めることはできません。 派生した属性のプロパティに対して生成される警告を抑制することができます、<xref:System.Attribute>クラスです。 それ以外の場合、この規則による警告は抑制しないでください。  
  
## <a name="example-violation"></a>違反の例  
  
### <a name="description"></a>説明  
 次の例では、この規則に違反するプロパティを示します。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]  
  
### <a name="comments"></a>コメント  
 この規則違反を修正するには、か、プロパティ、メソッドまたは配列ではなくコレクションを取得するプロパティを変更します。  
  
## <a name="change-the-property-to-a-method-example"></a>プロパティ メソッドの例を変更します  
  
### <a name="description"></a>説明  
 次の例では、メソッド、プロパティを変更することで違反を修正します。  
  
### <a name="code"></a>コード  
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]  
  
## <a name="return-a-collection-example"></a>コレクションを返す例  
  
### <a name="description"></a>説明  
 次の例は、返されるプロパティを変更することで違反を修正します。  
  
 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]  
  
## <a name="allowing-users-to-modify-a-property"></a>プロパティを変更するユーザーを許可します。  
  
### <a name="description"></a>説明  
 クラスのプロパティを変更するコンシューマーを許可する場合があります。 次の例では、この規則に違反する読み取り/書き込みプロパティを示します。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]  
  
### <a name="comments"></a>コメント  
 次の例は、返されるプロパティを変更することで違反を修正、<xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>です。  
  
### <a name="code"></a>コード  
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1024: 適切な場所にプロパティを使用します](../code-quality/ca1024-use-properties-where-appropriate.md)