---
title: '[オプション]、[テキスト エディター]、[C#]、[書式設定]'
ms.date: 02/09/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 534460d0ad6b7290190a88b3714c7f1eb0972723
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="options-text-editor-c-formatting"></a>[オプション]、[テキスト エディター]、[C#]、[書式設定]

**[書式設定]** オプション ページを使って、コード エディターでのコード書式オプションを設定します。 このオプション ページにアクセスするには、**[ツール]** > **[オプション]** を選び、さらに **[テキスト エディター]** > **[C#]** > **[コード スタイル]** > **[書式設定]** の順に選びます。

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

## <a name="general-settings"></a>全般設定

全般設定は、コード エディターがどのように書式オプションをコードに適用するかに影響します。

## <a name="uielement-list"></a>UIElement の一覧

|group1|説明|
|-----------|-----------------|
|**入力時にオートフォーマットする**|オフにすると、**[; でステートメントをオートフォーマットする]** および **[} でブロックをオートフォーマットする]** オプションが無効になります。|
|**; でステートメントをオートフォーマットする**|オンにすると、入力時に、ステートメントがエディター用に選択された書式オプションに従って書式設定されます。|
|**} でブロックをオートフォーマットする**|オンにすると、エディター用に選択した書式オプションに従って、コード ブロックの記述後すぐにコード ブロックへ書式が適用されます。|
|**戻り時にオートフォーマットする**|オンにすると、**Enter** キーを押したときに、テキストがエディター用に選択された書式オプションに合わせて書式設定されます。|
|**貼り付け時にオートフォーマットする**|オンにすると、エディターに貼り付けされたテキストが、エディター用に選択された書式オプションに合わせて書式設定されます。|

## <a name="preview-window"></a>プレビュー ウィンドウ

**[行間]**、**[改行]**、**[行間]**、および **[折り返し]** オプションのウィンドウでは、プレビュー ウィンドウを表示できます。 プレビュー ウィンドウでは、オプション適用時の状態が表示されます。 プレビュー ウィンドウを使用するには、書式オプションを選択します。 プレビュー ウィンドウに、選択したオプションを適用した例が表示されます。 ラジオ ボタンまたはチェック ボックスを選んで設定を変更すると、プレビュー ウィンドウが更新され、新しい設定が反映されます。

## <a name="remarks"></a>コメント

各言語の **[タブ]** ページのインデント オプションでは、行の最後で **Enter** キーを押した後に、コード エディターでカーソルがどこに配置されるかということだけを決定します。 **[書式設定]** のインデント オプションは、たとえば、**[貼り付け時にオート フォーマットする]** チェック ボックスがオンになっている間にコードをファイルに貼り付けるときなど、コードが自動的に書式設定される場合に適用されます。また、フォーマットされるブロックを手動で入力する場合にも適用されます。

## <a name="see-also"></a>関連項目

- [[全般]、[環境]、[オプション] ダイアログ ボックス](../../ide/reference/general-environment-options-dialog-box.md)
