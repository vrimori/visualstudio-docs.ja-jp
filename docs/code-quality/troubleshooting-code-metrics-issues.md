---
title: コード メトリックに関する問題のトラブルシューティング
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3d4e83d264e474a8ff578d1b832c4c2a2484bcd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937075"
---
# <a name="troubleshooting-code-metrics-issues"></a>コード メトリックに関する問題のトラブルシューティング
コード メトリックを収集するときに、次に示す問題が発生する場合があります。

-   [Visual Studio 2010 のコードの複雑度の計算における変更点](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Visual Studio 2010 のコードの複雑度の計算における変更点
 次のような状況では、同じ関数について [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] で計算したコードの複雑度のメトリックと旧バージョンの [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] で計算したメトリックとが異なる場合があります。

- 関数に 1 つ以上の catch ブロックが含まれている。 以前のバージョンの [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] では、catch ブロックが計算に含まれていませんでした。 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] では、各 catch ブロックの複雑度が関数の複雑度に加算されます。

- 関数に switch (VB の場合は Select Case) ステートメントが含まれている。 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] と旧バージョンの間のコンパイラの相違点により、case のフォールスルーを含んでいる一部の switch ステートメントに対して、異なる MSIL コードが生成される場合があります。

## <a name="see-also"></a>関連項目
 [マネージド コードの複雑さと保守性の測定](../code-quality/code-metrics-values.md)