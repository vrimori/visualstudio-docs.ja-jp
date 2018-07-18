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
ms.openlocfilehash: f444779fc5db725c090f96ec51a86d8427a14d17
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919182"
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
 プレリリース バージョンを使用してビルドされたリソース ファイル、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]サポートされる .NET Framework のバージョンで使用できない可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、ビルドのサポートされているバージョンを使用して、リソース、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。