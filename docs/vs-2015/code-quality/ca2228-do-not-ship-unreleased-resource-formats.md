---
title: 'Ca 2228: 未公開のリソース形式を出荷しません |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 84dc7c20f4109f7d66ed83b22fcec36dacc5eb3f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589680"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: 未公開のリソース形式を出荷しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 2228: 未公開のリソース形式を出荷しません](https://docs.microsoft.com/visualstudio/code-quality/ca2228-do-not-ship-unreleased-resource-formats)します。

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 リソース ファイルは、のバージョンを使用して構築された、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]現在サポートされていません。

## <a name="rule-description"></a>規則の説明
 プレリリース バージョンを使用してビルドされたリソース ファイル、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]サポートされているバージョンの .NET Framework で使用できない可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、ビルドのサポートされているバージョンを使用して、リソース、 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]k。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。



