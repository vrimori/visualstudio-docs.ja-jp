---
title: '[オプション]、[テキスト エディター]、[C#]、[書式設定] | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting
helpviewer_keywords:
- formatting [C#]
- formatting [J#]
- Text Editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 97699f8b4e9eaf0082cadecb584f9a8133a76424
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548832"
---
# <a name="options-text-editor-c-formatting"></a>[オプション]、[テキスト エディター]、[C#]、[書式設定]
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[オプション、テキスト エディターでは、c#、書式設定](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-csharp-formatting)します。  
  
  
**[書式設定]** プロパティ ページのダイアログ ボックスでコード エディターでのコード書式オプションを設定します。 このダイアログ ボックスを表示するには、**[ツール]** メニューの **[オプション]** をクリックし、**[テキスト エディター]**、**[C#]** を順に展開し、**[書式設定]** をクリックします。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="general-settings"></a>[全般設定]  
 全般設定は、コード エディターがどのように書式オプションをコードに適用するかに影響します。  
  
## <a name="uielement-list"></a>UIElement の一覧  
  
|group1|説明|  
|-----------|-----------------|  
|**[; を入力しステートメントを終了したときにオート フォーマットする]**|このチェック ボックスがオンになっていると、入力時に、ステートメントがコード エディター用に選択された書式オプションに従って書式設定されます。 コード エディターでステートメントを変更しない場合は、このチェック ボックスをオフにします。|  
|**[} の入力時にブロックをオート フォーマットする]**|このチェック ボックスがオンになっていると、コード エディター用に選択した書式オプションに従って、コード ブロックの記述後すぐにコード ブロックへ書式が適用されます。 コード エディターでコード ブロックを変更しない場合は、このチェック ボックスをオフにします。|  
|**[貼り付け時にインデントを調整する]**|このチェック ボックスがオンになっていると、コード エディターに貼り付けされたテキストが、コード エディター用に選択された書式オプションに合わせて書式設定されます。 貼り付けしたテキストを変更しない場合は、このチェック ボックスをオフにします。|  
  
## <a name="preview-window"></a>プレビュー ウィンドウ  
 **[行間]**、**[改行]**、**[行間]**、および **[折り返し]** オプションのウィンドウでは、プレビュー ウィンドウを表示できます。 プレビュー ウィンドウでは、オプション適用時の状態が表示されます。 プレビュー ウィンドウを使用するには、書式オプションを選択します。 プレビュー ウィンドウに、選択したオプションを適用した例が表示されます。 設定を変更すると (たとえばチェック ボックスをオンまたはオフにすると)、プレビュー ウィンドウが更新され、新しい設定が反映されます。  
  
## <a name="remarks"></a>Remarks  
 各言語の **[タブ]** ページのインデント オプションでは、行の最後で Enter キーを押した後に、コード エディターでカーソルがどこに配置されるかということだけを決定します。 **[書式設定]** のインデント オプションは、たとえば、**[貼り付け時にインデントを調整する]** チェック ボックスがオンになっている間にコードをファイルに貼り付けるときなど、コードが自動的に書式設定される場合に適用されます。また、フォーマットされるブロックを手動で入力する場合にも適用されます。  
  
## <a name="see-also"></a>関連項目  
 [[全般]、[環境]、[オプション] ダイアログ ボックス](../../ide/reference/general-environment-options-dialog-box.md)



