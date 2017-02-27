---
title: "方法: デバッグのステップ実行オプションを変更する (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "分岐ステップ実行"
  - "ワークフローのデバッグ, ステップ実行オプション"
  - "デバッグ, ステップ実行オプション"
  - "インスタンス ステップ実行"
  - "ステップ実行, オプションの変更"
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 方法: デバッグのステップ実行オプションを変更する (レガシ)
このトピックでは、同時アクションを含む従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]で、[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] アプリケーションのデバッグのステップ実行オプションを変更する方法について説明します。[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]を使用します。  
  
 **ParallelActivity** や **ConditionedActivityGroup** などの、同時実行を含む従来のアクティビティをデバッグする際には、2 つのオプションのいずれかを使用してコードを段階的に実行できます。  
  
 従来のワークフロー プロジェクトでデバッグのステップ実行オプションを変更するには、次の手順に従います。  
  
## 手順  
  
#### デバッグのステップ実行オプションを変更するには  
  
1.  Visual Studio を起動します。  
  
2.  既存の従来のワークフロー プロジェクトを開くか、同時アクティビティを使用し、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする新しいプロジェクトを作成します。  
  
3.  従来の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ワークフロー\]** メニューで、**\[デバッグ\]** をポイントし、**\[ステッピング オプション\]** をポイントします。  
  
4.  **\[インスタンス\]** または **\[分岐\]** のどちらかを選択します。  
  
## 参照  
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)   
 [デバッグのステップ実行オプション \(レガシ\)](../workflow-designer/debug-stepping-options-legacy.md)