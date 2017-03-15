---
title: "[オプション]、[テキスト エディター]、[全般] | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages.General"
  - "VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL.General"
  - "vs.toolsoptionspages.text_editor"
  - "VS.ToolsOptionsPages.Text_Editor.XML.General"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL80.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSS"
  - "VS.ToolsOptionsPages.Text_Editor.Plain_Text.General"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL_Script.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.General"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL7.General"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.General"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL.General"
  - "vs.toolsoptionspages.text_editor.visual_jsharp"
  - "VS.ToolsOptionsPages.Text_Editor.F#.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.F#"
  - "VS.ToolsOptionsPages.Text_Editor.PL/SQL.General"
  - "VS.ToolsOptionsPages.Text_Editor.C/C++.General"
  - "VS.ToolsOptionsPages.Text_Editor.Plain_Text"
  - "VS.ToolsOptionsPages.Text_Editor.HTML"
  - "VS.ToolsOptionsPages.Text_Editor.XAML.General"
  - "VS.ToolsOptionsPages.Text_Editor"
  - "VS.ToolsOptionsPages.Text_Editor.F#.General"
  - "VS.ToolsOptionsPages.Text_Editor.XOML.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL"
  - "vs.toolsoptionspages.text_editor.c/c++"
  - "VS.ToolsOptionsPages.Text_Editor.SQL_Script"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL90.General"
  - "VS.ToolsOptionsPages.Text_Editor.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp"
helpviewer_keywords: 
  - "[テキスト エディター] ([オプション] ダイアログ ボックス)"
  - "コード エディター"
  - "テキスト エディター [Visual Studio]"
  - "エディター、グローバル設定"
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# [オプション]、[テキスト エディター]、[全般]
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

このダイアログ ボックスを使用すると、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のコード エディターとテキスト エディターのグローバル設定を変更できます。  このダイアログ ボックスを表示するには、**\[ツール\]** メニューの **\[オプション\]** をクリックし、**\[テキスト エディター\]** フォルダーを展開し、**\[全般\]** をクリックします。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 設定  
 \[ドラッグ アンド ドロップ編集\]  
 選択した場合、テキストをマウスで選択し、別の位置にドラッグすることにより、テキストを現在のドキュメントまたは別の開いているドキュメントに移動できるようになります。  
  
 \[区切り記号を自動強調表示する\]  
 選択した場合、パラメーターまたは項目と値のペアの区切り文字、および対応する中かっこが強調表示されます。  
  
 \[変更履歴を記録する\]  
 コード エディターを選択すると最も新しいファイルが保存されてから変更されたコードを示す、垂直方向の黄色い行が選択余白に表示されます。  変更を保存すると、縦線は緑色になります。  
  
 \[シグネチャ \(BOM\) なしの UTF\-8 エンコードを自動検出\]  
 既定では、エディターがバイト順マークまたは文字セット タグを検索することにより、エンコーディングが検出されます。  いずれも現在のドキュメントに見つからなかった場合、コード エディターはバイト シーケンスをスキャンすることによって、UTF\-8 エンコーディングの自動検出を試みます。  エンコーディングの自動検出を無効にするには、このオプションを解除します。  
  
## 表示  
 マージン  
 選択した場合、エディターのテキスト領域の左端に沿って縦方向のマージンが表示されます。  このマージンをクリックしてテキストの 1 行全体を選択したり、クリック アンド ドラッグで連続する行を選択したりできます。  
  
|\[マージン\] がオンの場合|\[マージン\] がオフの場合|  
|---------------------|---------------------|  
|![HTMLpageSelectionMarginOn スクリーンショット](../../ide/reference/media/vxselmaron.png "vxSelmaron")|![HTMLpageSelectionMarginOff スクリーンショット](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|  
  
 インジケーター マージン  
 選択した場合、エディターのテキスト領域の左端の外側に縦方向のマージンが表示されます。  マージンをクリックすると、テキストに関連するアイコンとツールヒントが表示されます。  たとえば、ブレークポイントやタスク一覧のショートカットがインジケーター マージンに表示されます。  インジケーター マージンの情報は印刷されません。  
  
 \[垂直スクロール バー\]  
 オンにすると、縦方向のスクロール バーが表示されます。このスクロール バーで上下にスクロールして、エディターの表示領域外にある要素を表示できます。  縦方向のスクロール バーが利用できない場合は、PageUp キー、PageDown キー、および方向キーを使ってスクロールできます。  
  
 \[水平スクロール バー\]  
 オンにすると、横方向のスクロール バーが表示されます。このスクロール バーを使って左右にスクロールして、エディターの表示領域外にある要素を表示できます。  水平スクロール バーが利用できない場合は、方向キーを使ってスクロールできます。  
  
 現在の行を強調表示する  
 は、灰色のボックスにカーソルがあるコード行を囲むように選択した場合。  
  
## 参照  
 [\[オプション\]、\[テキスト エディター\]、\[すべての言語\]](../../ide/reference/options-text-editor-all-languages.md)   
 [\[オプション\]、\[テキスト エディター\]、\[すべての言語\]、\[タブ\]](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [\[オプション\]、\[テキスト エディター\]、\[ファイル拡張子\]](../../ide/reference/options-text-editor-file-extension.md)   
 [キーボード ショートカットの識別とカスタマイズ](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)   
 [エディターのカスタマイズ](../../ide/customizing-the-editor.md)   
 [IntelliSense の使用方法](../../ide/using-intellisense.md)