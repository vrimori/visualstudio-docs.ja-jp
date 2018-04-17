---
title: 'Ca 2239: 提供オプションのフィールドにメソッドを逆シリアル化 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.workload:
- multiple
ms.openlocfilehash: dfa5cd9490a20be91f00491ae3c860dbf4ac962f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: オプションのフィールドに逆シリアル化メソッドを指定します
|||  
|-|-|  
|TypeName|ProvideDeserializationMethodsForOptionalFields|  
|CheckId|CA2239|  
|カテゴリ|Microsoft.Usage|  
|互換性に影響する変更点|中断なし|  
  
## <a name="cause"></a>原因  
 型がでマークされているフィールド、<xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName>属性と型が逆シリアル化のイベント処理メソッドを提供していません。  
  
## <a name="rule-description"></a>規則の説明  
 <xref:System.Runtime.Serialization.OptionalFieldAttribute>属性がシリアル化時に影響を与えません。 属性でマークされたフィールドがシリアル化します。 ただし、フィールドは、逆シリアル化では無視され、その型に関連付けられている既定値を保持します。 逆シリアル化プロセス中にフィールドを設定するには、逆シリアル化イベントのハンドラーを宣言しなければなりません。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、逆シリアル化イベントの処理の型にメソッドを追加します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告を抑制するフィールドが、逆シリアル化プロセス中に無視される場合も安全です。  
  
## <a name="example"></a>例  
 次の例は、省略可能なフィールドおよび逆シリアル化イベントを持つ型処理メソッドを示しています。  
  
 [!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]  
  
## <a name="related-rules"></a>関連規則  
 [CA2236: ISerializable 型で基本クラス メソッドを呼び出します](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: ISerializable を正しく実装します](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: シリアル化コンストラクターを実装します](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: シリアル化メソッドを正しく実装します](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: すべてのシリアル化不可能なフィールドを設定します](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: ISerializable 型を SerializableAttribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2120: シリアル化コンストラクターをセキュリティで保護します](../code-quality/ca2120-secure-serialization-constructors.md)