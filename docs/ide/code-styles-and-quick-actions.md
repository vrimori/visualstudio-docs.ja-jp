---
title: "コード スタイルとクイック アクション | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 25bb9d99-aeff-4053-925d-2177f5e79574
author: BrianPeek
ms.author: brpeek
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: acc01617fffd7465cee01267482112aac5e352fc
ms.lasthandoff: 03/27/2017

---

# <a name="code-styles-and-quick-actions"></a>コード スタイルとクイック アクション
C# および Visual Basic プロジェクトのコード スタイルの優先順位は、**[ツール] > [オプション]** ウィンドウを開き、**[テキスト エディター] > [C#]/[Basic] > [コード スタイル] > [全般]** の順に選択して設定できます。  このウィンドウで設定したオプションは、ローカル コンピューターに適用されます。  選択すると、次のように、リスト内の各項目について優先順位のプレビューが表示されます。

![コード スタイルのオプション](~/ide/media/code-style-quick-actions-dialog.png)

各行のドロップダウン リストを使って、項目ごとに **[優先順位]** と **[重要度]** を設定できます。  重要度は **[なし]**、**[提案事項]**、**[警告]**、または **[エラー]** に設定でき、Visual Studio は適切に動作します。  これらのコード スタイルで[クイック アクション](quick-actions.md)を使ってコードを優先スタイルに自動的に書き直す場合は、非優先スタイルが使われたときに電球アイコン ![小さい電球アイコン](~/ide/media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") が表示されるように、**[なし]** 以外に設定する必要があります。  これらの優先順位は、電球アイコンをクリックして、または適切なコード行にカーソルを置いて **Ctrl + .** キーを押すと 適用できます。

.NET のコード スタイルの設定は、[EditorConfig](editorconfig-code-style-settings-reference.md) ファイルで管理することもできます。  この場合、[オプション] ウィンドウで選んだ設定はフォールバック設定になり、EditorConfig ファイルが優先されます。  このファイルを使って、リポジトリまたはチーム全体のコーディング スタイルを適用および構成できます。

# <a name="see-also"></a>関連項目
* [クイック アクション](quick-actions.md)
