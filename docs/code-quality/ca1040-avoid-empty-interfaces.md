---
title: 'CA1040: 空のインターフェイスは使用しないでください'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 247344cac2f2f36d1db28d1fe217cbfa5d9b6234
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: 空のインターフェイスは使用しないでください
|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 インターフェイスのメンバーの宣言またはその他の 2 つ以上のインターフェイスを実装はできません。

## <a name="rule-description"></a>規則の説明
 インターフェイスには、動作や使用のコントラクトを実現するメンバーが定義されます。 インターフェイスで示される機能は、継承の階層構造内に型が存在するかどうかにかかわらず、どの型からも適用できます。 型ではインターフェイスのメンバーに実装することで、インターフェイスが実装されます。 空のインターフェイスでは、すべてのメンバーは定義しません。 したがって、実装できるコントラクトは定義しません。

 デザインに空白を含める場合は、型のインターフェイスの実装が期待される、マーカーまたはの種類のグループを識別する方法として、インターフェイスを使用している可能性があります。 この id は、実行時に発生する可能性は、これを実現するための正しい方法は、カスタム属性を使用するです。 存在するか、属性がない場合や、属性のプロパティを使用して、対象の種類を識別します。 Id は、空のインターフェイスを使用することができますし、コンパイル時に行う必要がある場合。

## <a name="how-to-fix-violations"></a>違反の修正方法
 インターフェイスを削除するか、メンバーを追加します。 空のインターフェイスが、一連の型のラベル付けに使用される場合は、カスタム属性を持つインターフェイスを置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 インターフェイスを使用して、コンパイル時に一連の型を識別するこの規則による警告を抑制しても安全です。

## <a name="example"></a>例
 次の例では、空のインターフェイスを示します。

 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]