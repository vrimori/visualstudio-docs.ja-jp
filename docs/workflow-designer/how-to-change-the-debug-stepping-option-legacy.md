---
title: 'ワークフロー デザイナー - 方法: デバッグのステップ実行オプション (レガシ) を変更します。'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31047cedd4e8772b9ebab4ef238a8fe32bc07663
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>方法: デバッグのステップ実行オプションを変更する (レガシ)

このトピックでは、デバッグのステップ実行を同時実行アクションを持つ従来の Windows ワークフロー デザイナーでの Windows Workflow Foundation (WF) アプリケーション用のオプションを変更する方法について説明します。 .NET Framework version 3.5、または、WinFX を対象とする必要がある場合は、従来のワークフロー デザイナーを使用します。

などを持つ同時実行は、従来のアクティビティをデバッグする際に**ParallelActivity**または**ConditionedActivityGroup**、2 つのオプションのいずれかを使用して、コードをステップ実行することができます。

従来のワークフロー プロジェクトでデバッグのステップ実行オプションを変更するには、次の手順に従います。

## <a name="procedures"></a>手順

### <a name="to-change-the-debug-stepping-option"></a>デバッグのステップ実行オプションを変更するには

1.  Visual Studio を起動します。

2.  既存の従来のワークフロー プロジェクトを開くか、.NET Framework version 3.5、または、WinFX は、同時アクティビティとそのターゲットを使用する新しいプロジェクトを作成します。

3.  **ワークフロー**メニュー をポイントする、従来のワークフロー デザイナーで**デバッグ**、順にポイントして**ステップ実行オプション**です。

4.  いずれかを選択**インスタンス**または**ブランチ**です。

## <a name="see-also"></a>関連項目

- [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)
- [デバッグのステップ実行オプション (レガシ)](../workflow-designer/debug-stepping-options-legacy.md)