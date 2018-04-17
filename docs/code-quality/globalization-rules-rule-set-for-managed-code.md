---
title: マネージ コードのグローバリゼーション規則ルール設定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 54e1df6f8c49112747ccd7254f01a57d33dccf0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>マネージ コードの "グローバリゼーション規則" 規則セット
さまざまな言語、ロケール、およびカルチャに正しく表示されないアプリケーションでのデータを妨げる可能性のある問題に重点を置く設定 Microsoft グローバリゼーション規則規則を使用することができます。 この規則セットの場合は、アプリケーションをローカライズすると、グローバル化された、またはその両方を含める必要があります。  
  
|ルール|説明|  
|----------|-----------------|  
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|指定します|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|アクセラレータが重複しません。|  
|[CA 1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|ロケール特有の文字列をハードコードしません|  
|[CA 1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|ローカライズされたパラメーターとしてリテラルを渡さないでください。|  
|[CA 1304](../code-quality/ca1304-specify-cultureinfo.md)|CultureInfo を指定します|  
|[CA 1305](../code-quality/ca1305-specify-iformatprovider.md)|IFormatProvider を指定します|  
|[CA 1306](../code-quality/ca1306-set-locale-for-data-types.md)|データ型のロケールを設定|  
|[CA 1307](../code-quality/ca1307-specify-stringcomparison.md)|StringComparison を指定します。|  
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|文字列を大文字に正規化します。|  
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|StringComparison を使用します|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|P/invoke 文字列引数に対してマーシャ リングを指定します。|