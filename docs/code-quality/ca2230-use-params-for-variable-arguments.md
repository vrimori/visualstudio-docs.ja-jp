---
title: "2230: 可変引数に対して使用します params |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d578a68cfa5ff6b29d3e625dfd00b76e9994240a
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: 可変引数に対して param を使用します
|||  
|-|-|  
|TypeName|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|カテゴリ|Microsoft.Usage|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリックまたはプロテクト型に使用するパブリックまたはプロテクト メソッドが含まれています、`VarArgs`呼び出し規約です。  
  
## <a name="rule-description"></a>規則の説明  
 `VarArgs`呼び出し規約は、可変個のパラメーターを受け取る特定のメソッド定義で使用します。 メソッドを使用して、`VarArgs`共通言語仕様 (CLS) 準拠ではない呼び出し規約、およびプログラミング言語間でアクセスできない可能性があります。  
  
 C# で、`VarArgs`呼び出し規約は、メソッドのパラメーター リストの最後にときに使用、`__arglist`キーワード。 Visual Basic はサポートしません、`VarArgs`省略記号ボタンを使用するアンマネージ コードでのみ、使用は、呼び出し規約、および Visual C`...`表記します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正する C# の場合、使用、 [params](/dotnet/csharp/language-reference/keywords/params)キーワードの代わりに`__arglist`です。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例では、ルールに違反している使用し、規則に適合するいずれかを使用する、2 つの方法を示します。  
  
 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [言語への非依存性、および言語非依存コンポーネント](/dotnet/standard/language-independence-and-language-independent-components)