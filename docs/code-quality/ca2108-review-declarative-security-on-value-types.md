---
title: 'CA2108: 値型での宣言セキュリティをレビューします'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa2ed7050ff7b804d3224390393c3c860bc25c30
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916039"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: 値型での宣言セキュリティをレビューします
|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 パブリックまたはプロテクトの値の型がで保護されて、[データとモデリング](/dotnet/framework/data/index)または[リンク確認要求](/dotnet/framework/misc/link-demands)です。

## <a name="rule-description"></a>規則の説明
 値の型が割り当てられているし、他のコンス トラクターの実行前に、既定のコンス トラクターによって初期化します。 値の型が Demand または LinkDemand によって保護された呼び出し元に以外の任意のコンス トラクターはセキュリティ チェックを満たすためのアクセス許可が設定されていない場合は、既定値は失敗し、セキュリティ例外がスローされます。 値の型の割り当ては解除されません。既定のコンス トラクターで設定された状態で除外されます。 値の型のインスタンスを通過する呼び出し元が作成またはインスタンスにアクセスする権限を持っているとは限りません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 型から、セキュリティ チェックを削除して、代わりに使用するメソッドのレベルのセキュリティがチェックしない限り、この規則違反を修正することはできません。 この方法で、違反を修正していなくてもように値の型のインスタンスの取得から適切なアクセス許可を持つ呼び出し元に注意してください。 既定の状態で、値の型のインスタンスが、機密情報を公開しないと、有害な方法では使用できませんを確認する必要があります。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 任意の呼び出し元は、既定の状態にある値型のインスタンスを取得するセキュリティの脅威がない場合は、この規則による警告を抑制することができます。

## <a name="example"></a>例
 次の例は、この規則に違反する値の型を含むライブラリを示しています。 なお、`StructureManager`型が値型のインスタンスを渡す呼び出し元が作成またはインスタンスにアクセスする権限を持つことを前提とします。

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]

## <a name="example"></a>例
 次のアプリケーションでは、ライブラリの脆弱性について説明します。

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]

 この例を実行すると、次の出力が生成されます。

 **構造体のカスタム コンス トラクター: 要求が失敗しました。** 
**新しい値 SecuredTypeStructure 100 100**
**新しい値 SecuredTypeStructure 200 200**
## <a name="see-also"></a>関連項目
 [リンク確認要求](/dotnet/framework/misc/link-demands)[データとモデリング](/dotnet/framework/data/index)