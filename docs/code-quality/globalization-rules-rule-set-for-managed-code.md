---
title: マネージド コードの "グローバリゼーション規則" 規則セット
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3dea6c153196223f91726eaaedcace4f62c2868c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015265"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>マネージド コードの "グローバリゼーション規則" 規則セット
Microsoft グローバリゼーション規則ルールを異なる言語、ロケール、およびカルチャに正しく表示されないアプリケーションでのデータを妨げる可能性のある問題に集中するセットを使用できます。 この規則セットの場合は、アプリケーションをローカライズすると、グローバル化された、またはその両方を含める必要があります。

|ルール|説明|
|----------|-----------------|
|[CA 1300](../code-quality/ca1300-specify-messageboxoptions.md)|MessageBoxOption を指定します|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|重複するアクセラレータを使用しません|
|[CA 1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|ロケール特有の文字列をハードコードしません|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|ローカライズされるパラメーターとしてリテラルを渡さない|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|CultureInfo を指定します|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|IFormatProvider を指定します|
|[CA 1306](../code-quality/ca1306-set-locale-for-data-types.md)|データ型のロケールを設定します|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|StringComparison の指定|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|文字列を大文字に標準化します|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|順序を示す StringComparison を使用します|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|P/Invoke 文字列引数に対してマーシャリングを指定します|