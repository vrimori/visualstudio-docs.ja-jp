---
title: U-SQL エディターの書式設定オプション
ms.date: 01/17/2019
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.General
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d206d6e5a559550e874769a0dc01af907501882
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042856"
---
# <a name="options-text-editor-u-sql-formatting"></a>[オプション]、[テキスト エディター]、[U-SQL]、[書式設定]

**[書式設定]** オプション ページを使って、コード エディターでのコード書式設定オプションを設定します。 このオプション ページにアクセスするには、**[ツール]** > **[オプション]** の順に選択します。 **[オプション]** ダイアログ ボックスで、**[テキスト エディター]** > **[U-SQL]** > **[書式設定]** の順に選択します。

## <a name="general-page"></a>[全般] ページ

### <a name="general-settings"></a>全般設定

これらの設定は、コード エディターで書式設定オプションがコードに適用される*タイミング* に影響します。

- **セミコロン入力時に、完成したステートメントをオート フォーマットする**

   選択した場合、セミコロン キーの選択時に、ステートメントがエディター用に選択された書式オプションに従って書式設定されます。

- **貼り付け時にオートフォーマットする**

   オンにすると、エディターに貼り付けされたテキストが、エディター用に選択された書式オプションに合わせて書式設定されます。

## <a name="preview-windows"></a>プレビュー ウィンドウ

**[インデント]**、**[改行]**、および **[行間]** の各サブページには、下部にプレビュー ウィンドウが表示されます。 プレビュー ウィンドウでは、オプション適用時の状態が表示されます。 プレビュー ウィンドウを使用するには、書式オプションを選択します。 プレビュー ウィンドウに、選択したオプションを適用した例が表示されます。 チェック ボックスを選んで設定を変更すると、プレビュー ウィンドウが更新され、新しい設定が反映されます。

### <a name="indentation-remarks"></a>インデントに関するコメント

各言語の **[タブ]** ページのインデント オプションでは、行の最後で **Enter** キーを押したときにコード エディターでカーソルがどこに配置されるかということだけを決定します。 **[書式設定]** の下にあるインデント オプションは、コードが自動的に書式設定されるときに適用されます。例:

- **[貼り付け時にオートフォーマットする]** を選択した状態でファイルにコードを張り付けたとき
- 書式設定されているブロックが手動で入力されたとき

## <a name="see-also"></a>関連項目

- [[全般] ([オプション] ダイアログ ボックス - [環境])](../../ide/reference/general-environment-options-dialog-box.md)