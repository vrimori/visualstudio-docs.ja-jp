---
title: "コード分析の問題のトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e552570eb48b9210b366ebbfe157fe656ab3fe0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-code-analysis-issues"></a>コード分析に関する問題のトラブルシューティング
このトピックには、次の Visual Studio コード分析の問題のトラブルシューティング情報が含まれています。  
  
-   [Visual Studio 2010 ルール セットはない以前のバージョンの Visual Studio に反映での変更](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a>Visual Studio 2010 ルール セットはない以前のバージョンの Visual Studio に反映での変更  
 規則セットを作成するときに[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]子規則セットを格納している、以前のバージョンの Visual Studio を使用するコンピューターで実行されるコード分析で子規則セットへの変更を適用されないことができます。 この問題を解決するには、子のルール セットを含む規則セットである親のルール セットの書き換えを強制する必要があります。  
  
1.  親の規則で設定を開いている[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]です。  
  
2.  追加や、ルールの削除など、変更を加えるし、規則セットを保存します。  
  
3.  規則セットを再度、変更、元に戻すおよび規則セットを再度を保存します。  
  
## <a name="see-also"></a>関連項目  
 [アプリケーション品質の分析](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [マネージ コードの品質の分析](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [規則セットを使用したコード分析規則のグループ化](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)