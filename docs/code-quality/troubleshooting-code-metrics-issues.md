---
title: "コード メトリックに関する問題のトラブルシューティング |Microsoft ドキュメント"
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
ms.openlocfilehash: 4ef318d7c71a5770ea7a78ff078340b4f2dff960
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-code-metrics-issues"></a>コード メトリックに関する問題のトラブルシューティング
コード メトリックスを収集するときに、いくつかの次の問題が発生する可能性があります。  
  
-   [Visual Studio 2010 のコードの複雑な計算での変更](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Visual Studio 2010 のコードの複雑な計算での変更  
 同じ関数のコードの複雑性メトリックが計算された[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]の以前のバージョンで計算されたメトリックによって異なる場合が[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]次の状況で。  
  
-   関数を 1 つまたは複数の catch ブロック。 以前のバージョンの[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]、catch ブロックが計算に含まれていません。 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]、各ブロックの catch ブロックの複雑さは、関数の複雑さに追加します。  
  
-   関数には、switch (VB の場合はオン) ステートメントが含まれています。 コンパイラの相違[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]以前のバージョンはフォール スルー ケースを含む一部の switch ステートメントの別の MSIL コードを生成することができます。  
  
## <a name="see-also"></a>関連項目  
 [マネージ コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)