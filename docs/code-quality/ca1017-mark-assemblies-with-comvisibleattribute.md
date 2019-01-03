---
title: CA1017:アセンブリに ComVisibleAttribute を設定します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2c6d5f2356f6174739cc4a19e49265f0b163d035
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864739"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017:アセンブリに ComVisibleAttribute を設定します

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 アセンブリがない、<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>属性が適用されています。

## <a name="rule-description"></a>規則の説明
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>属性は、COM クライアントがマネージ コードにアクセスする方法を決定します。 アセンブリで COM の参照範囲を明示することをお勧めします。 COM の参照範囲は、アセンブリ全体に設定し、個々 の型と型のメンバー用にオーバーライドできます。 属性が存在しない場合、アセンブリの内容は COM クライアントに表示されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、アセンブリに属性を追加します。 属性を適用し、その値に設定、アセンブリを COM クライアントに表示したくない場合`false`します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。 アセンブリを参照できる場合は、属性を適用し、その値に設定`true`します。

## <a name="example"></a>例
 次の例では、アセンブリが、<xref:System.Runtime.InteropServices.ComVisibleAttribute>を COM クライアントに表示されるを防ぐために適用される属性。

 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>関連項目

- [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)
- [要件 (相互運用のための .NET 型の)](/dotnet/framework/interop/qualifying-net-types-for-interoperation)