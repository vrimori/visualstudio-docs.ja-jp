---
title: CA2114:メソッド セキュリティは型のスーパーセットでなければなりません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec58e8060447a02309a0a902bcf63eea8805ca8c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53881793"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114:メソッド セキュリティは型のスーパーセットでなければなりません

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 型が宣言型のセキュリティと、同じセキュリティ アクションに対して宣言型セキュリティをそのメソッドのいずれかが、セキュリティ アクションが[リンク確認要求](/dotnet/framework/misc/link-demands)型をチェックする権限がないアクセス許可のサブセットとメソッドによってチェックされます。

## <a name="rule-description"></a>規則の説明
 メソッドは、両方の同じアクション メソッド レベルと型レベルの宣言セキュリティは必要ありません。 2 つのチェックが組み合わされていません。メソッド レベルの要求のみが適用されます。 型のアクセス許可を要求する場合など、 `X`、アクセス許可を要求のメソッドのいずれかと`Y`、コードにアクセス許可がない`X`メソッドを実行します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 両方のアクションが必要であるかどうかを確認するコードを確認します。 両方のアクションが必要な場合は、メソッド レベルのアクションがタイプ レベルで指定されたセキュリティが含まれることを確認します。 種類のアクセス許可を要求する場合など、 `X`、し、そのメソッドは、アクセス許可を要求する必要がありますも`Y`、メソッドが明示的に要求する必要があります`X`と`Y`します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 メソッドは、型で指定されたセキュリティを必要としない場合、この規則による警告を抑制するのには安全です。 ただし、これは通常のシナリオではありません、慎重に設計レビューの必要性を示す可能性があります。

## <a name="example-1"></a>例 1

次の例では、環境のアクセス許可を使用して、この規則に違反する危険性を示します。 この例では、アプリケーション コードは、型に必要な権限を拒否する前にセキュリティで保護された型のインスタンスを作成します。 実際の脅威のシナリオでは、オブジェクトのインスタンスを取得することもできます必要があります。

次の例では、ライブラリの需要は一種の書き込みアクセス許可と、メソッドに対する読み取りアクセス許可。

[!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example-2"></a>例 2

次のアプリケーション コードでは、型レベルのセキュリティ要件を満たしていない場合でも、メソッドを呼び出すことによって、ライブラリの脆弱性を示します。

[!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

この例を実行すると、次の出力が生成されます。

```txt
[All permissions] Personal information: 6/16/1964 12:00:00 AM
[No write permission (demanded by type)] Personal information: 6/16/1964 12:00:00 AM
[No read permission (demanded by method)] Could not access personal information: Request failed.
```

## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)
- [リンク確認要求](/dotnet/framework/misc/link-demands)
- [データとモデリング](/dotnet/framework/data/index)