---
title: "方法: デバッグのステップ実行オプション (レガシ) の変更 |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ea687b0a08aa4697ac9f7c7b0aca875af131a561
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>方法: デバッグのステップ実行オプションを変更する (レガシ)
このトピックのデバッグのステップ実行オプションを変更する方法について説明[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]を同時実行アクションを持つ従来の Windows ワークフロー デザイナーでのアプリケーションです。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]を使用します。

 などを持つ同時実行は、従来のアクティビティをデバッグする際に**ParallelActivity**または**ConditionedActivityGroup**、2 つのオプションのいずれかを使用して、コードをステップ実行することができます。

 従来のワークフロー プロジェクトでデバッグのステップ実行オプションを変更するには、次の手順に従います。

## <a name="procedures"></a>手順

#### <a name="to-change-the-debug-stepping-option"></a>デバッグのステップ実行オプションを変更するには

1.  Visual Studio を起動します。

2.  既存の従来のワークフロー プロジェクトを開くか、同時アクティビティを使用し、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする新しいプロジェクトを作成します。

3.  **ワークフロー**では、従来のメニュー [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]、 をポイント**デバッグ**、順にポイントして**ステップ実行オプション**です。

4.  いずれかを選択**インスタンス**または**ブランチ**です。

## <a name="see-also"></a>関連項目

- [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)
- [デバッグのステップ実行オプション (レガシ)](../workflow-designer/debug-stepping-options-legacy.md)