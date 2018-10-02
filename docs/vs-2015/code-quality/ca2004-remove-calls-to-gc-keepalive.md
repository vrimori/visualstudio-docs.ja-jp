---
title: 'Ca 2004: GC への呼び出しを削除します。KeepAlive |Microsoft Docs'
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
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8fbaa0bae44b09cef1d75c31c342ac6cf3e463df
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589088"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: GC.KeepAlive への呼び出しを削除します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 2004: GC への呼び出しを削除します。KeepAlive](https://docs.microsoft.com/visualstudio/code-quality/ca2004-remove-calls-to-gc-keepalive)します。

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|カテゴリ|Microsoft.Reliability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 クラスの使用`SafeHandle`への呼び出しがまだ含まれているが`GC.KeepAlive`します。

## <a name="rule-description"></a>規則の説明
 変換する場合`SafeHandle`使用状況、呼び出しをすべて削除`GC.KeepAlive`(オブジェクト)。 この場合は、クラス必要はありませんを呼び出す`GC.KeepAlive`、ファイナライザーはありませんが、依存するいると仮定すると`SafeHandle`して OS ハンドルを完了します。  呼び出しで保持するためのコスト`GC.KeepAlive`ごくわずかであり、パフォーマンスの認識によって測定される場合がありますがへの呼び出し`GC.KeepAlive`必要であるか、または有効期間がコードになりますが困難になりますが、存在しなくなった問題を解決するためには維持します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 呼び出しを削除`GC.KeepAlive`します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 変換する技術的には位置が正しくない場合にのみ、この警告を抑制できます`SafeHandle`クラスで使用します。



