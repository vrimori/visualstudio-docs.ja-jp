---
title: 'CA2103: 命令型のセキュリティを確認します'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a20dc939b305e3ec917f57bcd9f7cc8f8aa735f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914908"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: 命令型のセキュリティを確認します
|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 メソッドが強制セキュリティを使用しています。また、そのメソッドで、確認要求がアクティブな場合に変更できるステータス情報または戻り値を使用して、アクセス許可を構築している可能性があります。

## <a name="rule-description"></a>規則の説明
 命令型のセキュリティでは、マネージ オブジェクトを使用して、宣言セキュリティは、属性を使用してアクセス許可と操作をメタデータに格納すると比較して、コードの実行中にアクセス許可とセキュリティ アクションを指定します。 命令型のセキュリティでは非常に柔軟なアクセス許可オブジェクトの状態を設定し、実行時までは利用できない情報を使用してセキュリティ アクションを選択することができます。 柔軟性は、アクションで設定されている限り、権限の状態を判断するを使用するランタイム情報が変更されるリスクをものです。

 できる限り、宣言セキュリティを使用します。 宣言型の要求が理解しやすくします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 アクセス許可の状態に頼りませんについては、アクセス許可が使用されている限り、変更できるかどうかを確認する命令型のセキュリティ確認要求を確認してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 アクセス許可が変化するデータに依存しない場合は、この規則による警告を抑制するのには安全です。 ただし、等価な宣言型に強制確認要求を変更することをお勧めします。

## <a name="see-also"></a>関連項目
 [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)[データとモデリング](/dotnet/framework/data/index)