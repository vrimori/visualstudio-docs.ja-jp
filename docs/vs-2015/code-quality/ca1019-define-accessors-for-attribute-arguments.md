---
title: 'Ca 1019: 属性引数にアクセサーを定義する |Microsoft Docs'
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
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ff0329c5c9d565685d4e5c0ff950b31dea3299f6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854889"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: 属性引数にアクセサーを定義します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 そのコンス トラクターでは、属性は、対応するプロパティがない引数を定義します。

## <a name="rule-description"></a>規則の説明
 属性では、対象に適用するときに必ず指定する必須の引数を定義できます。 この引数は、コンストラクターに位置指定パラメーターで属性を指定できるようになるため、位置指定引数とも呼ばれます。 必須のすべての引数について、対応する読み取り専用のプロパティも属性で規定する必要があります。これは、引数値を実行時に取得できるようにするためです。 このルールは、各コンス トラクターのパラメーターの対応するプロパティを定義したかを確認します。

 また、属性ではオプションの引数も定義できます。これは名前付き引数とも呼ばれます。 この引数は、名前でコンストラクターに属性を指定するときに使用されます。また、対応する読み取り/書き込みプロパティが必要です。

 必須およびオプションの引数では、対応するプロパティとコンス トラクターのパラメーターを使用する必要があります、同じ名前が異なる大文字小文字の区別を付けます。 プロパティは pascal 形式を使用する大文字と小文字、およびパラメーター使用して camel 規約に従った大文字小文字の区別します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、コンス トラクターのパラメーターがない 1 つの読み取り専用プロパティを追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 取得できる必須の引数の値したくない場合は、この規則による警告を抑制します。

## <a name="custom-attributes-example"></a>カスタム属性の例

### <a name="description"></a>説明
 次の例では、必須 (位置) パラメーターを定義する 2 つの属性を示します。 属性の最初の実装が正しく定義されていません。 2 番目の実装が正しいです。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>位置指定引数と名前付き引数

### <a name="description"></a>説明
 位置指定引数と名前付き引数は、どの引数には、属性の必須とする引数は省略可能なライブラリのコンシューマーをクリアすること。

 次の例では、位置指定引数と名前付きの両方の引数を持つ属性の実装を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>コメント
 次の例では、2 つのプロパティにカスタム属性を適用する方法を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA1813: シールされていない属性を使用しません](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>関連項目
 [属性](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)



