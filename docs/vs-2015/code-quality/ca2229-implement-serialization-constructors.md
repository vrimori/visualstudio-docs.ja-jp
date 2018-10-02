---
title: 'Ca 2229: シリアル化コンス トラクターを実装する |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ea0aeb5e1a493d49c1b5fa6db4fbce8f0ad8ea71
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589203"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: シリアル化コンストラクターを実装します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 2229: シリアル化コンス トラクターを実装](https://docs.microsoft.com/visualstudio/code-quality/ca2229-implement-serialization-constructors)します。

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 型が実装、<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>インターフェイス、デリゲートまたはインターフェイスではないと、次の条件のいずれかが true:

-   型には、取得するコンス トラクターはありません、<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>オブジェクトと<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>オブジェクト (シリアル化コンス トラクターの署名)。

-   型が封印されていないと、そのシリアル化コンス トラクターのアクセス修飾子が保護された (ファミリ) ではありません。

-   型がシールされている、シリアル化コンス トラクターのアクセス修飾子がプライベートではありません。

## <a name="rule-description"></a>規則の説明
 このルールは、カスタムのシリアル化をサポートする型に関連します。 型は、実装している場合、カスタムのシリアル化をサポートしている、<xref:System.Runtime.Serialization.ISerializable>インターフェイス。 シリアル化コンス トラクターは、逆シリアル化、またはを使用してシリアル化されたオブジェクトを再作成に必要な<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>メソッド。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、シリアル化コンストラクターを実装します。 シールされたクラスの場合、コンストラクターをプライベートにするか、プロテクトにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 ルールの違反を抑制しないでください。 型を使用して、逆シリアル化はならず、多くのシナリオでは機能しません。

## <a name="example"></a>例
 次の例では、規則に適合する型を示します。

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA2237: ISerializable 型を SerializableAttribute に設定します](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>関連項目
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>



