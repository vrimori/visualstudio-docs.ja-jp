---
title: "コード スタイルとクイック アクション | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 25bb9d99-aeff-4053-925d-2177f5e79574
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.openlocfilehash: d42bb9165748b7282aa42f062b545add62ad1c93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="code-styles-and-quick-actions"></a>コード スタイルとクイック アクション
C# および Visual Basic プロジェクトのコード スタイルの優先順位は、**[ツール] > [オプション]** ウィンドウを開き、**[テキスト エディター] > [C#]/[Basic] > [コード スタイル] > [全般]** の順に選択して設定できます。  このウィンドウで設定したオプションは、ローカル コンピューターに適用されます。  選択すると、次のように、リスト内の各項目について優先順位のプレビューが表示されます。

![コード スタイルのオプション](media/code-style-quick-actions-dialog.png)

各行のドロップダウン リストを使って、項目ごとに **[優先順位]** と **[重要度]** を設定できます。  重要度は **[なし]**、**[提案事項]**、**[警告]**、または **[エラー]** に設定でき、Visual Studio は適切に動作します。  これらのコード スタイルで[クイック アクション](quick-actions.md)を使ってコードを優先スタイルに自動的に書き直す場合は、非優先スタイルが使われたときに電球アイコン ![小さい電球アイコン](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") が表示されるように、**[なし]** 以外に設定する必要があります。  これらの優先順位は、電球アイコンをクリックして、または適切なコード行にカーソルを置いて **Ctrl + .** キーを押すと 適用できます。

.NET のコード スタイルの設定は、[EditorConfig](editorconfig-code-style-settings-reference.md) ファイルで管理することもできます。  この場合、[オプション] ウィンドウで選んだ設定はフォールバック設定になり、EditorConfig ファイルが優先されます。  このファイルを使って、リポジトリまたはチーム全体のコーディング スタイルを適用および構成できます。

## <a name="see-also"></a>関連項目
* [クイック アクション](quick-actions.md)