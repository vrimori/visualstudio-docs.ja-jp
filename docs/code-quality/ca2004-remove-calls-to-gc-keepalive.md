---
title: 'CA2004: GC.KeepAlive への呼び出しを削除します'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2f05764f5147a064815cdb744420686fb6a5a7c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: GC.KeepAlive への呼び出しを削除します
|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|カテゴリ|Microsoft.Reliability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 クラスの使用`SafeHandle`への呼び出しがまだ含まれては`GC.KeepAlive`します。

## <a name="rule-description"></a>規則の説明
 変換する場合`SafeHandle`使用法、呼び出しをすべて削除`GC.KeepAlive`(オブジェクト)。 この場合、クラスのないを呼び出す`GC.KeepAlive`、ファイナライザーはありませんに依存するいると仮定して`SafeHandle`が OS ハンドルを完了します。  コストへの呼び出しに残す`GC.KeepAlive`ごくわずかであり、パフォーマンスに対する認識によって評価される場合がありますをへの呼び出し`GC.KeepAlive`必要であるか、または問題が存在しない可能性がありますが、有効期間を解決するためには維持します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 呼び出しを削除`GC.KeepAlive`です。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 変換する技術的には間違っている場合にのみ、この警告を抑制できます`SafeHandle`クラス内で使用します。