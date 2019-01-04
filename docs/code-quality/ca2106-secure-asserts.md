---
title: CA2106:アサートをセキュリティで保護します
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 164d2bbe335f4b69892cf069bade5cf0df1e0787
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864674"
---
# <a name="ca2106-secure-asserts"></a>CA2106:アサートをセキュリティで保護します

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 メソッドは、アクセス許可をアサートして、呼び出し元のセキュリティ チェックは行われません。

## <a name="rule-description"></a>規則の説明
 セキュリティ チェックを実行せずにセキュリティ アクセス許可をアサートすると、悪用される可能性があるセキュリティの弱点がコード内に残る場合があります。 セキュリティ アクセス許可がアサートされたときに、セキュリティのスタック ウォークが停止します。 呼び出し元のすべてのチェックを実行せずにアクセス許可をアサートする場合、呼び出し元直接コードを実行しない、アクセス許可を使用します。 セキュリティ チェックが、アサートは、有害な方法では使用できませんを確認する場合は、許容せずにアサートします。 呼び出すコードは、無害なのか、ユーザーが任意の情報を呼び出したコードに渡すことはできません、アサートは問題ありません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、メソッド、またはその宣言型セキュリティ確認要求を追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 注意が必要なセキュリティ レビュー後にのみこの規則による警告を抑制します。

## <a name="see-also"></a>関連項目

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)