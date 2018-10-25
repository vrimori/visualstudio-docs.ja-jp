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
ms.openlocfilehash: 19f903ae02413bf18474aa2d95d71d765c288fa9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900632"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: 未公開のリソース形式を出荷しません

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 リソース ファイルは、現在サポートされていない .NET Framework のバージョンを使用して構築されました。

## <a name="rule-description"></a>規則の説明
 .NET Framework のプレリリース バージョンを使用してビルドされたリソース ファイルは、サポートされているバージョンの .NET Framework で使用できるしない場合があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、.NET Frameworkk のサポートされているバージョンを使用して、リソースをビルドします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。