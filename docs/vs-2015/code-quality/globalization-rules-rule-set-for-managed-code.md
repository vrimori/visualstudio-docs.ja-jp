---
title: マネージ コードの"グローバリゼーション規則"規則の設定 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d56d80a88cb28318869f37b4fb33f8782a137e3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268919"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>マネージド コードの "グローバリゼーション規則" 規則セット
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft グローバリゼーション規則ルールを異なる言語、ロケール、およびカルチャに正しく表示されないアプリケーションでのデータを妨げる可能性のある問題に集中するセットを使用できます。 この規則セットの場合は、アプリケーションをローカライズすると、グローバル化された、またはその両方を含める必要があります。  
  
|ルール|説明|  
|----------|-----------------|  
|[CA 1300](../code-quality/ca1300-specify-messageboxoptions.md)|Messageboxoption を指定します|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|アクセラレータが重複の回避します。|  
|[CA 1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|ロケール特有の文字列をハードコードしません|  
|[CA 1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|ローカライズされたパラメーターとしてリテラルを渡さないでください。|  
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|CultureInfo を指定します|  
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|IFormatProvider を指定します|  
|[CA 1306](../code-quality/ca1306-set-locale-for-data-types.md)|データ型のロケールを設定します。|  
|[CA 1307](../code-quality/ca1307-specify-stringcomparison.md)|StringComparison を指定します。|  
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|文字列を大文字に正規化します。|  
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|StringComparison を使用します|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|P/invoke 文字列引数に対してマーシャ リングを指定します。|



