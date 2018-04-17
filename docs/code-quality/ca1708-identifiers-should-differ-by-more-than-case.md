---
title: 'CA1708: 識別子は、複数のケースで異なる必要があります |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35626f9e59aa1138c6d1756953ed5fdd72906deb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: 識別子は、大文字と小文字の区別以外にも相違していなければなりません
|||  
|-|-|  
|TypeName|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|カテゴリ|Microsoft.Naming|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 2 つの型、メンバー、パラメーター、または完全修飾名前空間の名前は、小文字に変換されるときと同じです。  
  
## <a name="rule-description"></a>規則の説明  
 名前空間、型、メンバー、およびパラメーターの各識別子は、大文字/小文字以外のみでは区別できません。共通言語ランタイムを対象とする言語は、大文字と小文字を区別する必要はないためです。 たとえば、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]広く使用されている大文字と小文字の言語です。  
  
 この規則は、公開されているメンバーのみに適用されます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 大文字小文字の他の識別子を比較した場合に一意の名前を選択します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。 ライブラリを使用可能なすべての言語で使用できない可能性があります、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。  
  
## <a name="example-of-a-violation"></a>違反の例  
 次の例では、この規則違反を示します。  
  
 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1709: 識別子では、大文字と小文字が正しく区別されなければなりません](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)