---
title: "コード メトリックに関する問題のトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: ea1e787c1d509123a650cf2bd20e5fa8bffd5b4e
ms.openlocfilehash: 9f3f41548412d84cd1219aae45b7c87ea5383de9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

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
