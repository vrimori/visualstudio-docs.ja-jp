---
title: Visual Studio のコードのスタイル設定
ms.date: 03/10/2017
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 6dd046fa8a01cde7abdc33484da3ff8227eda966
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
ms.locfileid: "34063685"
---
# <a name="code-style-preferences"></a>コードのスタイル設定

C# プロジェクトおよび Visual Basic プロジェクトに対してコードのスタイル設定を設定するには、**[ツール]** メニューから **[オプション]** ダイアログ ボックスを開きます。 **[テキスト エディター]** > **[C#]** または **[基本]** > **[コード スタイル]** >  **[全般]** を選択します。 このウィンドウで設定したオプションは、ローカル コンピューターに適用されます。

選択すると、リスト内の各項目について優先順位のプレビューが表示されます。

![コード スタイルのオプション](media/code-style-quick-actions-dialog.png)

## <a name="preference-and-severity"></a>優先順位と重大度

各行のドロップダウン リストを使って、項目ごとに **[優先順位]** と **[重大度レベル]** の値を設定できます。 重大度は、**なし**、**提案**、**警告**、または **エラー**に設定できます。 コード スタイルの[クイック アクション](../ide/quick-actions.md)を有効にする場合、**[重大度レベル]** の設定は**なし**以外に設定してください。 クイック アクションの電球アイコン ![小さい電球アイコン](media/vs2015_lightbulbsmall.png) は、優先されていないスタイルが使用されていて、[クイック アクション] 一覧のオプションを選ぶと優先されるスタイルにコードが自動的に再作成される場合に表示されます。

## <a name="editorconfig-files"></a>EditorConfig ファイル

.NET のコード スタイルの設定は、[EditorConfig](../ide/editorconfig-code-style-settings-reference.md) ファイルで管理することもできます。 EditorConfig ファイル内の設定が、**[オプション]** ダイアログ ボックスで選択したオプションよりも優先されます。 この EditorConfig ファイルを使って、リポジトリまたはプロジェクト全体のコーディング スタイルを適用および構成できます。

## <a name="see-also"></a>関連項目

- [クイック アクション](../ide/quick-actions.md)
- [EditorConfig の .NET コーディング規則の設定](../ide/editorconfig-code-style-settings-reference.md)