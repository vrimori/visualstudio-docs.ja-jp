---
title: 'Ca 1051: 参照できるインスタンス フィールドを宣言しません |Microsoft Docs'
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
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4c752b11a41bac148099042ff9c95845917a05ee
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190914"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: 参照できるインスタンス フィールドを宣言しないでください
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照の型は、外部から参照できるインスタンス フィールドを持ちます。

## <a name="rule-description"></a>規則の説明
 フィールドの主な用途は、実装の詳細にする必要があります。 フィールドは`private`または`internal`プロパティを使用して公開する必要があります。 プロパティにアクセスするように、フィールドにアクセスして、重大な変更を導入せず、型の機能を展開すると、プロパティのアクセサーでコードを変更できます簡単になります。 プライベートまたは内部フィールドの値を返すだけのプロパティに従った; フィールドへのアクセスを実行する最適化されました。ほとんどのパフォーマンスの向上は、プロパティに対する外部から参照できるフィールドの使用に関連付けられません。

 外部から参照`public`、 `protected`、および`protected internal`(`Public`、`Protected`と`Protected Friend`Visual basic) のアクセシビリティ レベル。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正することをフィールド`private`または`internal`を外部から参照のプロパティを使用して公開します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。 外部から参照できるフィールドは、プロパティに提供されるすべての特典を提供していません。 さらに、パブリック フィールドで保護することはできません[リンク確認要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)します。 参照してください[ca 2112: セキュリティで保護された型はフィールドを公開する必要があります](../code-quality/ca2112-secured-types-should-not-expose-fields.md)します。

## <a name="example"></a>例
 次の例は、型を示します (`BadPublicInstanceFields`) をこの規則に違反します。 `GoodPublicInstanceFields` 修正後のコードを示します。

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA2112: セキュリティで保護された型はフィールドを公開してはなりません](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>関連項目
 [リンク確認要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)



