---
title: ワークフロー デザイナーのデバッグのステップ実行オプション (レガシ)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f46c0ab382a0e189c595e6e0f8aeb69c71814faf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="debug-stepping-options-legacy"></a>デバッグのステップ実行オプション (レガシ)

このトピックでは、従来の Windows ワークフロー デザイナーで、同時アクティビティを含む Windows Workflow Foundation (WF) アプリケーションをデバッグする方法について説明します。 .NET Framework version 3.5、または、WinFX を対象とする必要がある場合は、従来のワークフロー デザイナーを使用します。

などを持つ同時実行は、従来のアクティビティをデバッグする際に**ParallelActivity**または**ConditionedActivityGroup**、次の 2 つのオプションのいずれかを使用するには、コードをステップ実行.

-   **分岐ステップ実行します。** このステップ実行モードでは、ステップ実行をなど、複合アクティビティの特定の分岐をデバッグすることができます、 **ParallelActivity**または**ConditionalActivityGroup**アクティビティ。 このオプションを使用してデバッグを実行すると、ワークフローで他のアクティビティが同時に実行されるため、コントロールの変更は確認できません。 デバッガーは、現在選択されている分岐のアクティビティのみステップ スルーし、ワークフロー内の他のアクティビティが同時に実行されていることがあります。 たとえば、既定では、左端の分岐、 **ParallelActivity**アクティビティとの最初の子アクティビティ、 **ConditionedActivityGroup**アクティビティがステッピングに使用されます。 ユーザーが他の分岐または子アクティビティをデバッグする場合には、明示的なブレークポイントをその分岐または子アクティビティに配置する必要があります。 ブレークポイントに達すると、ステッピングはその分岐で続行します。

-   **インスタンス ステップ実行します。** このステップ実行モードを使用すれば、ワークフロー内で同時に実行されるアクティビティを段階的に実行してデバッグすることができます。 このオプションを使用すると、現在実行中のアクティビティがワークフロー内で実行されるときに、コントロールの変更を確認できます。

既定では分岐ステップ実行オプションが選択されていますが、ユーザーは従来のワークフローのデバッグ時にこれら 2 つのオプションの間で切り替えることができます。

従来のステート マシン ワークフローをデバッグするときには、インスタンス ステップ実行オプションを選択する必要があります。

## <a name="see-also"></a>関連項目

- [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)
- [方法: デバッグのステップ実行オプションを変更する (レガシ)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)