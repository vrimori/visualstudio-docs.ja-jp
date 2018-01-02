---
title: "Visual Studio のコードのスタイル設定 | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.openlocfilehash: 24470f4fdb1a75d6ebd2743b2ade72e6195842b4
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2017
---
# <a name="code-style-preferences"></a>コードのスタイル設定

C# プロジェクトおよび Visual Basic プロジェクトに対してコードのスタイル設定を設定するには、**[ツール]** メニューから **[オプション]** ダイアログ ボックスを開きます。 **[テキスト エディター]**、**[C#]**、**[Basic]**、**[コード スタイル]**、**[全般]** を選択します。 このウィンドウで設定したオプションは、ローカル コンピューターに適用されます。 選択すると、次のように、リスト内の各項目について優先順位のプレビューが表示されます。

![コード スタイルのオプション](media/code-style-quick-actions-dialog.png)

各行のドロップダウン リストを使って、項目ごとに **[優先順位]** と **[重要度]** を設定できます。 重要度は **[なし]**、**[提案事項]**、**[警告]**、または **[エラー]** に設定でき、Visual Studio は適切に動作します。 これらのコード スタイルで[クイック アクション](quick-actions.md)を使ってコードを優先スタイルに自動的に書き直す場合は、非優先スタイルが使われたときに電球アイコン ![小さい電球アイコン](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") が表示されるように、**[なし]** 以外に設定する必要があります。 これらの優先順位は、電球アイコンをクリックして、または適切なコード行にカーソルを置いて **Ctrl + .** キーを押すと 適用できます。

.NET のコード スタイルの設定は、[EditorConfig](../ide/editorconfig-code-style-settings-reference.md) ファイルで管理することもできます。 この場合、**[オプション]** ダイアログ ボックスで選択されたオプションよりも、EditorConfig ファイル内の設定が優先されます。 この EditorConfig ファイルを使って、リポジトリまたはプロジェクト全体のコーディング スタイルを適用および構成できます。

## <a name="see-also"></a>関連項目

[クイック アクション](quick-actions.md)  
[EditorConfig の .NET コーディング規則の設定](../ide/editorconfig-code-style-settings-reference.md)