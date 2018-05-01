---
title: Visual Studio のコードのスタイル設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/10/2017
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 4898a2e4a55f5c11179ae5a00e46c87a44519a7b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="code-style-preferences"></a>コードのスタイル設定

C# プロジェクトおよび Visual Basic プロジェクトに対してコードのスタイル設定を設定するには、**[ツール]** メニューから **[オプション]** ダイアログ ボックスを開きます。 **[テキスト エディター]** > **[C#]** または **[基本]** > **[コード スタイル]** >  **[全般]** を選択します。 このウィンドウで設定したオプションは、ローカル コンピューターに適用されます。 選択すると、次のように、リスト内の各項目について優先順位のプレビューが表示されます。

![コード スタイルのオプション](media/code-style-quick-actions-dialog.png)

各行のドロップダウン リストを使って、項目ごとに **[優先順位]** と **[重大度レベル]** の値を設定できます。 重大度は、**なし**、**提案**、**警告**、または **エラー**に設定できます。 コード スタイルの[クイック アクション](../ide/quick-actions.md)を有効にする場合、**[重大度レベル]** の設定は**なし**以外に設定してください。 クイック アクションの電球アイコン ![小さい電球アイコン](media/vs2015_lightbulbsmall.png)は、優先されていないスタイルが使用されていて、[クイック アクション] 一覧のオプションを選ぶと優先されるスタイルにコードが自動的に再作成される場合に表示されます。

.NET のコード スタイルの設定は、[EditorConfig](../ide/editorconfig-code-style-settings-reference.md) ファイルで管理することもできます。 この場合、**[オプション]** ダイアログ ボックスで選択されたオプションよりも、EditorConfig ファイル内の設定が優先されます。 この EditorConfig ファイルを使って、リポジトリまたはプロジェクト全体のコーディング スタイルを適用および構成できます。

### <a name="see-also"></a>関連項目

[クイック アクション](../ide/quick-actions.md)  
[EditorConfig の .NET コーディング規則の設定](../ide/editorconfig-code-style-settings-reference.md)