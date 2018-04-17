---
title: 'Ca 2130: セキュリティ上重要な定数は透過的である必要があります |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2fbda0886fe05d22ccf61f36792d8bfcf687547a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: セキュリティ上重要な定数は透過的である必要がある
|||  
|-|-|  
|TypeName|ConstantsShouldBeTransparent|  
|CheckId|CA2130|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 定数フィールドまたは列挙体のメンバーが付いて、<xref:System.Security.SecurityCriticalAttribute>です。  
  
## <a name="rule-description"></a>規則の説明  
 実行時に検索の必要がない値がコンパイラのインライン定数に設定されているため、定数値に対して透過性は適用されません。 透過的なコードからは定数にアクセスできないとコード レビューアーが考えることがないよう、定数フィールドは透過的セキュリティなフィールドとして定義する必要があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、フィールドまたは値から SecurityCritical 属性を削除します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、列挙値で`EnumWithCriticalValues.CriticalEnumValue`と定数`CriticalConstant`この警告が発生します。 問題を解決するには、削除、[`SecurityCritical`] ようにセキュリティ透過的な属性です。  
  
 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]