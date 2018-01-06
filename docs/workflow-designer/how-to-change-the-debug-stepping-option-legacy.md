---
title: "方法: デバッグのステップ実行オプション (レガシ) の変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: bc92b5babe53b249fc66d93adbc0d69e6f7cf0e3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>方法: デバッグのステップ実行オプションを変更する (レガシ)
このトピックでは、同時アクションを含む従来の [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]で、[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] アプリケーションのデバッグのステップ実行オプションを変更する方法について説明します。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]を使用します。  
  
 などを持つ同時実行は、従来のアクティビティをデバッグする際に**ParallelActivity**または**ConditionedActivityGroup**、2 つのオプションのいずれかを使用して、コードをステップ実行することができます。  
  
 従来のワークフロー プロジェクトでデバッグのステップ実行オプションを変更するには、次の手順に従います。  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-change-the-debug-stepping-option"></a>デバッグのステップ実行オプションを変更するには  
  
1.  Visual Studio を起動します。  
  
2.  既存の従来のワークフロー プロジェクトを開くか、同時アクティビティを使用し、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする新しいプロジェクトを作成します。  
  
3.  **ワークフロー**では、従来のメニュー [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]、 をポイント**デバッグ**、順にポイントして**ステップ実行オプション**です。  
  
4.  いずれかを選択**インスタンス**または**ブランチ**です。  
  
## <a name="see-also"></a>参照  
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)   
 [デバッグのステップ実行オプション (レガシ)](../workflow-designer/debug-stepping-options-legacy.md)