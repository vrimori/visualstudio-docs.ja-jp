---
title: CA2108:値型での宣言セキュリティを確認します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb7795b2e1cdcdf8d32578396bb879f4573a45e8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55003287"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108:値型での宣言セキュリティを確認します

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

パブリックまたはプロテクトの値の型がによってセキュリティ保護、[データとモデリング](/dotnet/framework/data/index)または[リンク確認要求](/dotnet/framework/misc/link-demands)します。

## <a name="rule-description"></a>規則の説明

値の型に割り当てられ他のコンス トラクターの実行前に既定のコンス トラクターによって初期化します。 値の型が Demand または LinkDemand によってセキュリティ保護されていて、呼び出し元には、以外の任意のコンス トラクター、セキュリティ チェックに適合するアクセス許可がありません。 既定値は失敗すると、およびセキュリティ例外がスローされます。 値の型の割り当ては解除されません。既定のコンス トラクターによって設定された状態で中断するとします。 値型のインスタンスを渡す呼び出し元が作成またはインスタンスにアクセスする権限を持っているとは限りません。

## <a name="how-to-fix-violations"></a>違反の修正方法

種類、セキュリティ チェックを削除して、その場所に使用してメソッド レベルのセキュリティを確認しますしない限り、この規則違反を修正することはできません。 この方法で、違反を修正、値型のインスタンスを取得するから不適切なアクセス許可を持つ呼び出し元が防止されることはできません。 既定の状態で、値型のインスタンスは、機密情報を公開しないと、有害な方法では使用できませんをことを確認する必要があります。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

呼び出し元は、既定の状態にある値型のインスタンスを取得するセキュリティの脅威がない場合は、この規則による警告を抑制できます。

## <a name="example-1"></a>例 1

次の例では、この規則に違反する値の型を含むライブラリを示します。 `StructureManager`型では、値型のインスタンスを渡す呼び出し元が作成またはインスタンスにアクセスする権限を持っている前提としています。

[!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]

## <a name="example-2"></a>例 2

次のアプリケーションでは、ライブラリの脆弱性を示しています。

[!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]

この例を実行すると、次の出力が生成されます。

```txt
Structure custom constructor: Request failed.
New values SecuredTypeStructure 100 100
New values SecuredTypeStructure 200 200
```

## <a name="see-also"></a>関連項目

- [リンク確認要求](/dotnet/framework/misc/link-demands)
- [データとモデリング](/dotnet/framework/data/index)
