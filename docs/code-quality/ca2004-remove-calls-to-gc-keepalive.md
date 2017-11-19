---
title: "Ca 2004: は、GC への呼び出しを削除します。KeepAlive |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: edb47391872da6754e39a27d2e8a50dc61293af1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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