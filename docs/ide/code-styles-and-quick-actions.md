---
title: コードのスタイル設定
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
ms.openlocfilehash: 718110b3339628052d8a4a2e3ebbcdd163707a97
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065262"
---
# <a name="code-style-preferences"></a>コードのスタイル設定

C# プロジェクトおよび Visual Basic プロジェクトに対してコードのスタイル設定を設定するには、**[ツール]** メニューから **[オプション]** ダイアログ ボックスを開きます。 **[オプション]** ダイアログ ボックスで、**[テキスト エディター]** > **[C#]** または **[Basic]** > **[コード スタイル]** > **[全般]** の順に選択します。 このウィンドウで設定したオプションは、ローカル コンピューターにのみ適用されます。

選択すると、リスト内の各項目について優先順位のプレビューが表示されます。

![コード スタイルのオプション](media/code-style-quick-actions-dialog.png)

> [!NOTE]
> このトピックは、Windows 上の Visual Studio に適用されます。 Visual Studio for Mac については、[Visual Studio for Mac でのエディターの動作](/visualstudio/mac/editor-behavior)に関するページを参照してください。

## <a name="preference-and-severity"></a>優先順位と重大度

各行のドロップダウン リストを使って、項目ごとに **[優先順位]** と **[重大度レベル]** の値を設定できます。 重大度は、**なし**、**提案**、**警告**、または **エラー**に設定できます。 コード スタイルの[クイック アクション](../ide/quick-actions.md)を有効にする場合、**[重大度レベル]** の設定は**なし**以外に設定してください。 **クイック アクション**の電球アイコン ![小さい電球アイコン](media/vs2015_lightbulbsmall.png) は、優先されていないスタイルが使用されていて、**[クイック アクション]** 一覧のオプションを選ぶと優先されるスタイルにコードが自動的に再作成される場合に表示されます。

## <a name="editorconfig-files"></a>EditorConfig ファイル

.NET のコード スタイルの設定は、[EditorConfig](../ide/editorconfig-code-style-settings-reference.md) ファイルで管理することもできます。 EditorConfig ファイル内の設定が、**[オプション]** ダイアログ ボックスで選択したオプションよりも優先されます。 この EditorConfig ファイルを使って、リポジトリまたはプロジェクト全体のコーディング スタイルを適用および構成できます。

## <a name="format-document-command"></a>[ドキュメントのフォーマット] コマンド

Visual Studio 2017 バージョン 15.8 以降では、using の削除と並べ替え、コード スタイルの基本設定の適用など、ファイルでの追加コードのクリーンアップを行うように **[ドキュメントのフォーマット]** コマンド (**[編集]** > **[詳細設定]** > **[ドキュメントのフォーマット]**) を構成することができます。 [[書式設定] オプション ページ](reference/options-text-editor-csharp-formatting.md#format-document-settings)で、**ドキュメントのフォーマット**で適用する設定を定義することができます。

コードのクリーンアップでは、*.editorconfig* ファイルで構成した設定が優先されます。そのルールまたはファイルがない場合は、**[ツール]** > **[オプション]** > **[テキスト エディター]** > **[C#]** > **[コード スタイル]** または **[書式設定]** の設定が優先されます。

Visual Studio 2017 で初めて **[ドキュメントのフォーマット]** コマンドをトリガーするときに、黄色の情報バーが表示され、コードのクリーンアップ設定を構成するように求められます。

> [!TIP]
> *.editorconfig* ファイルで **none** として構成されているルールはコードのクリーンアップに関するものではありませんが、**[クイック アクションとリファクタリング]** メニューを使用して個別に適用できます。

## <a name="see-also"></a>関連項目

- [クイック アクション](../ide/quick-actions.md)
- [EditorConfig の .NET コーディング規則の設定](../ide/editorconfig-code-style-settings-reference.md)
- [エディターの動作 (Visual Studio for Mac)](/visualstudio/mac/editor-behavior)