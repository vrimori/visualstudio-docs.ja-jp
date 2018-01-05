---
title: "コード メトリックに関する問題のトラブルシューティング | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f31d0f5d236327db483c9698579c8c03129acd64
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-code-metrics-issues"></a>コード メトリックに関する問題のトラブルシューティング
コード メトリックを収集するときに、次に示す問題が発生する場合があります。  
  
-   [Visual Studio 2010 のコードの複雑度の計算における変更点](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Visual Studio 2010 のコードの複雑度の計算における変更点  
 次のような状況では、同じ関数について [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] で計算したコードの複雑度のメトリックと旧バージョンの [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] で計算したメトリックとが異なる場合があります。  
  
-   関数に 1 つ以上の catch ブロックが含まれている。 以前のバージョンの [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] では、catch ブロックが計算に含まれていませんでした。 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] では、各 catch ブロックの複雑度が関数の複雑度に加算されます。  
  
-   関数に switch (VB の場合は Select Case) ステートメントが含まれている。 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] と旧バージョンの間のコンパイラの相違点により、case のフォールスルーを含んでいる一部の switch ステートメントに対して、異なる MSIL コードが生成される場合があります。  
  
## <a name="see-also"></a>参照  
 [マネージ コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)