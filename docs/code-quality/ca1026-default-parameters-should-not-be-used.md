---
title: CA1026:既定パラメーターを使用することはできません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 30a925d685a327499f426bc3e6d060b897dd90c3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53839678"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026:既定パラメーターを使用することはできません

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照の型には、既定のパラメーターを使用する、外部から参照できるメソッドが含まれています。

## <a name="rule-description"></a>規則の説明
 既定のパラメーターを使用するメソッドは下で、共通言語仕様 (CLS); を使用します。ただし、CLS では、これらのパラメーターに割り当てられている値を無視するコンパイラが使用できます。 既定のパラメーター値を無視するコンパイラ用に記述されたコードでは、既定の各パラメーターの引数を明示的に指定する必要があります。 プログラミング言語間で使用する動作を維持するためには、既定のパラメーターを提供するメソッドのオーバー ロードを持つ既定のパラメーターを使用するメソッドを置き換える必要があります。

 コンパイラは、マネージ コードにアクセスするときの既定のパラメーターの値を管理拡張機能の C++ の無視します。 Visual Basic コンパイラを使用する既定のパラメーターを持つメソッドをサポートしている、 [(省略可能)](/dotnet/visual-basic/language-reference/modifiers/optional)キーワード。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、既定パラメーターを指定するメソッドのオーバー ロードを持つ既定のパラメーターを使用するメソッドを置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、既定のパラメーターを使用するメソッドと同等の機能を提供するオーバー ロードされたメソッドを示します。

 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>関連するルール
 [CA 1025:反復する引数を params 配列で置き換えます](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>関連項目
 [言語への非依存性、および言語非依存コンポーネント](/dotnet/standard/language-independence-and-language-independent-components)