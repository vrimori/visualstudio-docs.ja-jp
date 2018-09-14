---
title: 'CA1407: Com 参照可能な型で静的メンバーを使用しません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ba8ef8cc0b75ed70ea6e98be2a4bac3e041e1d8
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45552017"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Com 参照可能な型で静的メンバーを使用しません
|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 コンポーネント オブジェクト モデル (COM) を参照できると明確にマークされている型が含まれています、`public``static`メソッド。

## <a name="rule-description"></a>規則の説明
 COM をサポートしません`static`メソッド。

 このルールは、プロパティ、イベント アクセサー メソッド、またはいずれかを使用してマークされているメソッドのオーバー ロード演算子は無視されます、<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>属性または<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>属性。

 既定では、次は COM から参照できる: アセンブリ、型のパブリック、パブリック型は、パブリック インスタンス メンバーおよびパブリック値型のすべてのメンバー。

 このルールで発生すると、アセンブリ レベルの<xref:System.Runtime.InteropServices.ComVisibleAttribute>に設定する必要があります`false`とクラス -<xref:System.Runtime.InteropServices.ComVisibleAttribute>に設定する必要があります`true`次のコードに示すように、します。

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正すると同じ機能を提供するインスタンス メソッドを使用してデザインを変更して、`static`メソッド。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 COM クライアントがによって提供される機能へのアクセスを必要としない場合、この規則による警告を抑制するのには安全では、`static`メソッド。

## <a name="example-violation"></a>例の違反

### <a name="description"></a>説明
 次の例は、`static`この規則に違反するメソッド。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>コメント
 この例で、 **Book.FromPages** COM からメソッドを呼び出すことができません

## <a name="example-fix"></a>例の修正プログラム

### <a name="description"></a>説明
 前の例では、違反を修正するインスタンス メソッド、メソッドを変更できますが、このインスタンスで意味がないことが。 優れたソリューションが明示的に適用するには`ComVisible(false)`メソッドは、COM から表示できない他の開発者をオフにする方法

 次の例では、適用<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>メソッドにします。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>関連するルール
 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Visual Basic 6 クライアントに対しては Int64 引数を使用しません](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>関連項目
 [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)