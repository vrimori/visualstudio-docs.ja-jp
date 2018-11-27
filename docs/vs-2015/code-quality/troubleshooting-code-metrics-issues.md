---
title: コード メトリックに関する問題のトラブルシューティング | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2cc5c586e1e994ff2e14710b39c04bb424b770d2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800641"
---
# <a name="troubleshooting-code-metrics-issues"></a>コード メトリックに関する問題のトラブルシューティング
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

コード メトリックを収集するときに、次に示す問題が発生する場合があります。  
  
-   [Visual Studio 2010 のコードの複雑度の計算における変更点](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Visual Studio 2010 のコードの複雑度の計算における変更点  
 次のような状況では、同じ関数について [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] で計算したコードの複雑度のメトリックと旧バージョンの [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] で計算したメトリックとが異なる場合があります。  
  
-   関数に 1 つ以上の catch ブロックが含まれている。 以前のバージョンの [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] では、catch ブロックが計算に含まれていませんでした。 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] では、各 catch ブロックの複雑度が関数の複雑度に加算されます。  
  
-   関数に switch (VB の場合は Select Case) ステートメントが含まれている。 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] と旧バージョンの間のコンパイラの相違点により、case のフォールスルーを含んでいる一部の switch ステートメントに対して、異なる MSIL コードが生成される場合があります。  
  
## <a name="see-also"></a>関連項目  
 [マネージド コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



