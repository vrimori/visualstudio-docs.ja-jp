---
title: ': Ca 1407 COM 参照可能な型で静的メンバー |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9b3d14351ddb0e7e98c5c93bd1fe62c5b106dca1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889049"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Com 参照可能な型で静的メンバーを使用しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 COM クライアントがによって提供される機能へのアクセスを必要としない場合、この規則による警告を抑制するのには安全では、`static`メソッド。

## <a name="example-violation"></a>例の違反

### <a name="description"></a>説明
 次の例は、`static`この規則に違反するメソッド。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>コメント
 この例で、 **Book.FromPages** COM からメソッドを呼び出すことができません

## <a name="example-fix"></a>例の修正プログラム

### <a name="description"></a>説明
 前の例では、違反を修正するインスタンス メソッド、メソッドを変更できますが、このインスタンスで意味がないことが。 優れたソリューションが明示的に適用するには`ComVisible(false)`メソッドは、COM から表示できない他の開発者をオフにする方法

 次の例では、適用<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>メソッドにします。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA1017: アセンブリに ComVisibleAttribute を設定します](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Visual Basic 6 クライアントに対しては Int64 引数を使用しません](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: Com 参照可能な値型ではパブリックでないフィールドを使用しません](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>関連項目
 [アンマネージ コードとの相互運用](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



