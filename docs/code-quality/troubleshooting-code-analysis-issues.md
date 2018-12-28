---
title: コード分析に関する問題のトラブルシューティング
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b481a200cfd085cddcd0e8826eef94f7d4e5fbee
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804391"
---
# <a name="troubleshooting-code-analysis-issues"></a>コード分析に関する問題のトラブルシューティング
このトピックでは、次の Visual Studio コード分析の問題についてのトラブルシューティング情報を示します。

-   [Visual Studio 2010 規則セットでの変更が以前のバージョンの Visual Studio に反映されない](#ChildRuleSetChangesInPreviousVersions)

##  <a name="ChildRuleSetChangesInPreviousVersions"></a>Visual Studio 2010 規則セットでの変更が以前のバージョンの Visual Studio に反映されない
 子規則セットを含む [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 規則セットを作成すると、子規則セットに対する変更が、旧バージョンの Visual Studio を使用するコンピューターで実行されるコード分析に適用されない場合があります。 この問題を解決するには、親規則セット、つまり子規則セットを含む規則セットを強制的に書き換える必要があります。

1. [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] で親規則セットを開きます。

2. 規則の追加、削除などの変更を加え、規則セットを保存します。

3. 規則セットを再度開き、変更を元に戻し、規則セットを再度保存します。

## <a name="see-also"></a>関連項目

- [アプリケーション品質の分析](../code-quality/code-analysis-for-managed-code-overview.md)
- [マネージド コードの品質の分析](../code-quality/code-analysis-for-managed-code-overview.md)
- [規則セットを使用したコード分析規則のグループ化](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)