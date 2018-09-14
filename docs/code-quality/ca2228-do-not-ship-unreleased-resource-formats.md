---
title: 'CA2228: 未公開のリソース形式を出荷しません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2823933e4792dd6127ffbd4b1bfe5dfe1b71a0c
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547552"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: 未公開のリソース形式を出荷しません
|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 リソース ファイルは、のバージョンを使用して構築された、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]現在サポートされていません。

## <a name="rule-description"></a>規則の説明
 プレリリース バージョンを使用してビルドされたリソース ファイル、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]サポートされているバージョンの .NET Framework で使用できない可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、ビルドのサポートされているバージョンを使用して、リソース、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。