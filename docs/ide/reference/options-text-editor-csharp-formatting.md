---
title: "[オプション]、[テキスト エディター]、[C#]、[書式設定] | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting"
helpviewer_keywords: 
  - "書式指定 [C#]"
  - "書式指定 [J#]"
  - "[テキスト エディター] の [オプション] ダイアログ ボックス、書式設定"
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# [オプション]、[テキスト エディター]、[C#]、[書式設定]
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**\[書式設定\]** プロパティ ページのダイアログ ボックスでコード エディターでのコード書式オプションを設定します。  このダイアログ ボックスを表示するには、**\[ツール\]** メニューの **\[オプション\]** をクリックし、**\[テキスト エディター\]**、**\[C\#\]** を順に展開し、**\[書式設定\]** をクリックします。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## \[全般設定\]  
 全般設定は、コード エディターがどのように書式オプションをコードに適用するかに影響します。  
  
## UIElement の一覧  
  
|ラベル|説明|  
|---------|--------|  
|**\[; の入力時にステートメントをオート フォーマットする\]**|このチェック ボックスがオンになっていると、入力時に、ステートメントがコード エディター用に選択された書式オプションに従って書式設定されます。  コード エディターでステートメントを変更しない場合は、このチェック ボックスをオフにします。|  
|**\[} の入力時にブロックをオート フォーマットする\]**|このチェック ボックスがオンになっていると、コード エディター用に選択した書式オプションに従って、コード ブロックの記述後すぐにコード ブロックへ書式が適用されます。  コード エディターでコード ブロックを変更しない場合は、このチェック ボックスをオフにします。|  
|**\[貼り付け時にインデントを調整する\]**|このチェック ボックスがオンになっていると、コード エディターに貼り付けされたテキストが、コード エディター用に選択された書式オプションに合わせて書式設定されます。  貼り付けしたテキストを変更しない場合は、このチェック ボックスをオフにします。|  
  
## プレビュー ウィンドウ  
 **\[行間\]**、**\[改行\]**、**\[行間\]**、および **\[折り返し\]** オプションのペインでは、プレビュー ウィンドウを表示できます。  プレビュー ウィンドウでは、オプション適用時の状態が表示されます。  プレビュー ウィンドウを使用するには、書式オプションを選択します。  プレビュー ウィンドウに、選択したオプションを適用した例が表示されます。  設定を変更すると \(たとえばチェック ボックスをオンまたはオフにすると\)、プレビュー ウィンドウが更新され、新しい設定が反映されます。  
  
## 解説  
 各言語の **\[タブ\]** ページのインデント オプションでは、行の最後で Enter キーを押した後に、コード エディターでカーソルがどこに配置されるかということだけを決定します。  **\[書式設定\]** のインデント オプションは、たとえば、**\[貼り付け時にインデントを調整する\]** チェック ボックスがオンになっている間にコードをファイルに貼り付けるときなど、コードが自動的に書式設定される場合に適用されます。また、フォーマットされるブロックを手動で入力する場合にも適用されます。  
  
## 参照  
 [\[全般\] \(\[オプション\] ダイアログ ボックス \- \[環境\]\)](../Topic/General,%20Environment,%20Options%20Dialog%20Box.md)