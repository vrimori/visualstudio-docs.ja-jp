---
title: 'Ca 1415: P 呼び出します正しく宣言'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb03f6a5e0242af79242f2b3ae735fa4df694c20
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: P/Invoke を正しく宣言します
|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|改行の場合は、アセンブリ外パラメーターを宣言する P/invoke は表示できません。 互換性に影響するの場合は、P/invoke パラメーターを宣言するが、アセンブリ外見なすことができます。|

## <a name="cause"></a>原因
 プラットフォーム呼び出しメソッド宣言が正しくありません。

## <a name="rule-description"></a>規則の説明
 プラットフォームがメソッドへのアクセスのアンマネージ コードを呼び出すし、によって定義されている、`Declare`キーワード[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]または<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>です。 プラットフォーム呼び出しメソッドの宣言を OVERLAPPED 構造体パラメーターへのポインターを持つ Win32 関数を対象として、対応するマネージ型のパラメーターがへのポインターではないためこのルールは現時点では、検索、<xref:System.Threading.NativeOverlapped?displayProperty=fullName>構造体。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、プラットフォームを正しく宣言メソッドを呼び出します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 例を次にプラットフォームが、規則に違反して、規則に適合するメソッドを呼び出します。

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>関連項目
 [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)