---
title: '方法: デバッグのステップ実行オプション (レガシ) の変更 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 1fbe4ef5feeff7201a5c8772c1e754402db9ffd5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539512"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>方法: デバッグのステップ実行オプションを変更する (レガシ)
このトピックでは、同時アクションを含む従来の [!INCLUDE[wf](../includes/wf-md.md)]で、[!INCLUDE[wfd1](../includes/wfd1-md.md)] アプリケーションのデバッグのステップ実行オプションを変更する方法について説明します。 [!INCLUDE[wfd2](../includes/wfd2-md.md)] または [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]を使用します。  
  
 など、同時実行のある従来のアクティビティをデバッグする際に**ParallelActivity**または**ConditionedActivityGroup**、2 つのオプションのいずれかを使用して、コードをステップ実行することができます。  
  
 従来のワークフロー プロジェクトでデバッグのステップ実行オプションを変更するには、次の手順に従います。  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-change-the-debug-stepping-option"></a>デバッグのステップ実行オプションを変更するには  
  
1.  Visual Studio を起動します。  
  
2.  既存の従来のワークフロー プロジェクトを開くか、同時アクティビティを使用し、[!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] または [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] を対象とする新しいプロジェクトを作成します。  
  
3.  **ワークフロー** 、従来のメニュー [!INCLUDE[wfd2](../includes/wfd2-md.md)]、 をポイント**デバッグ**、順にポイント**ステッピング オプション**します。  
  
4.  いずれかを選択**インスタンス**または**ブランチ**します。  
  
## <a name="see-also"></a>関連項目  
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)   
 [デバッグのステップ実行オプション (レガシ)](../workflow-designer/debug-stepping-options-legacy.md)