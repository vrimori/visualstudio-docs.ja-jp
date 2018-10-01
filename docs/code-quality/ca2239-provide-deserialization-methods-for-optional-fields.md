---
title: 'CA2239: オプションのフィールドに逆シリアル化メソッドを指定します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8c1b8adb3454b7309eefa49ded129ce899c3cf58
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548583"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: オプションのフィールドに逆シリアル化メソッドを指定します

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 型がでマークされているフィールド、<xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName>属性と型が逆シリアル化イベント処理メソッドを提供していません。

## <a name="rule-description"></a>規則の説明
 <xref:System.Runtime.Serialization.OptionalFieldAttribute>属性がシリアル化の影響を与えません。 属性でマークされたフィールドがシリアル化します。 ただし、フィールドは、逆シリアル化では無視され、その種類に関連付けられた既定値が保持されます。 逆シリアル化プロセス中にフィールドを設定するには、逆シリアル化イベント ハンドラーを宣言しなければなりません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、型にメソッドを処理する逆シリアル化イベントを追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 逆シリアル化プロセス中に、フィールドが無視される場合は、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例
 省略可能なフィールドと逆シリアル化イベントを使用して型の処理メソッドを次の例に示します。

 [!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]

## <a name="related-rules"></a>関連するルール
 [CA2236: ISerializable 型で基本クラス メソッドを呼び出します](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable を正しく実装します](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: シリアル化メソッドを正しく実装します](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: すべてのシリアル化不可能なフィールドを設定します](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: ISerializable 型を SerializableAttribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120: シリアル化コンストラクターをセキュリティで保護します](../code-quality/ca2120-secure-serialization-constructors.md)