---
title: "Guid と Visual Studio ツールバーの Id | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visual studio のグループ"
  - "ツール バー"
  - "visual studio ツールバー"
  - "ID"
  - "toolgar グループ"
  - "ツール ウィンドウのツールバー"
  - "guid"
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Guid と Visual Studio ツールバーの Id
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

このトピックではグループの Visual Studio 統合開発環境に含まれるツール \(IDE\) バーの GUID と ID 値を列挙します。  これらの値はVisual Studio SDK の一部としてインストール .vsct ファイルで定義されます。  詳細については、「[IDE 定義コマンド、メニューのおよびグループ](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)」を参照してください。  
  
> [!NOTE]
>  Visual Studio に Visual Studio で使用できるツール バーの多くは定義されずGUIDID の値は public ではありません。  このトピックではVisual Studio SDK .vsct ファイルで定義されているツール バーのみが表示されます。  
  
 .vsct ファイルで定義されている IDE オブジェクトを使用する方法の詳細については[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md) を参照してください。  
  
 Visual Studio IDE によって提供される既定のツール バーはGUID を使用すると別の方法で指定された場所以外GUID `guidSHLMainMenu` を使用して : ID の構文。  
  
## IDE のツール バー  
 次のツール バーはVisual Studio IDE によって提供されます。  ツール バーは ENT1ENT \[入力\] メニューの \[\] ENT0ENT サブメニューで選択して表示できます。  ツール ウィンドウではこのセクションに含まれていません。  
  
 グループをツール バーから直接の子であることができます。  グループを追加するにはツール バーの GUID と ID に親を設定します。  ツール バーにボタンを追加するにはツール バーのグループに親を設定します。  
  
|ツール バー|ID|  
|------------|--------|  
|\[標準\]|IDM\_VS\_TOOL\_STANDARD|  
|Build|IDM\_VS\_TOOL\_BUILD|  
|\[テキスト エディター\]|IDM\_VS\_TOOL\_TEXTEDITOR|  
|デバッグ|guidVSDebugGroup: IDM\_DEBUG\_TOOLBAR|  
|デバッグの場所|guidVSDebugGroup: IDM\_DEBUG\_CONTEXT\_TOOLBAR|  
  
### 特殊なツール バー  
 これらのツール バーはVisual Studio IDE によって定義されますが専用の関数を実行しコマンド グループが用意されています。  
  
|ツール バー|ID|  
|------------|--------|  
|追加のコマンド|IDM\_VS\_TOOL\_ADDCOMMAND|  
|未定義|IDM\_VS\_TOOL\_UNDEFINED|  
|XML スキーマ|IDM\_VS\_TOOL\_SCHEMA|  
|XML データ|IDM\_VS\_TOOL\_DATA|  
  
## IDE のツール バーのグループ  
 \[標準\] ツール バーにボタンを追加するには親として次のグループのいずれかを 1 に設定します。  グループが親ツール バーに並べ替えられます。  
  
### \[標準\] ツール バーのグループ  
  
|名前|ID|  
|--------|--------|  
|保存して開きます。|IDG\_VS\_TOOLSB\_SAVEOPEN|  
|切り取りまたはコピー|IDG\_VS\_TOOLSB\_CUTCOPY|  
|元に戻す \/ やり直し|IDG\_VS\_TOOLSB\_UNDOREDO|  
|ビルドと実行|IDG\_VS\_TOOLSB\_RUNBUILD|  
|\[検索\]|IDG\_VS\_TOOLSB\_SEARCH|  
|ウィンドウ|IDG\_VS\_TOOLSB\_WINDOWS|  
|新しいウィンドウ|IDG\_VS\_TOOLSB\_NEWWINDOWS|  
|読み込みと保存|IDG\_VS\_WINDOWUI\_LOADSAVE|  
|ゲージ|IDG\_VS\_TOOLSB\_GAUGE|  
  
### ビルド ツール バーのグループ  
  
|名前|ID|  
|--------|--------|  
|バーをビルド|IDG\_VS\_BUILDBAR|  
|\[キャンセル\]|IDG\_VS\_BUILD\_CANCEL|  
  
### テキスト エディター\] ツール バーのグループ  
  
|名前|ID|  
|--------|--------|  
|完了|IDM\_VS\_TOOL\_TEXTEDITOR|  
|インデント|IDG\_VS\_EDITTOOLBAR\_INDENT|  
|コメント|IDG\_VS\_EDITTOOLBAR\_COMMENT|  
|ブックマーク|IDG\_VS\_EDITTOOLBAR\_TEMPBOOKMARKS|  
  
### デバッグ ツール バーのグループ  
  
|名前|ID|  
|--------|--------|  
|実行|IDM\_DEBUG\_TOOLBAR|  
|ステップ実行|IDG\_DEBUG\_TOOLBAR\_STEPPING|  
|Watch|IDG\_DEBUG\_TOOLBAR\_WATCH|  
|ウィンドウ|IDG\_DEBUG\_TOOLBAR\_WINDOWS|  
  
### \[デバッグの場所\] ツール バーのグループ  
  
|名前|ID|  
|--------|--------|  
|デバッグの場所|IDG\_DEBUG\_CONTEXT\_TOOLBAR|  
  
## ツール ウィンドウのツール バー  
 ツール バーは IDE または  **ソリューション エクスプローラー**  などのツール ウィンドウで直接使用できます。  ツール ウィンドウに .vsct ファイルで定義されていないためツール ウィンドウのツール バーには親が定義されていません。  代わりにコードに配置されます。  次の表はIDE のツール ウィンドウに表示されるおよびコマンド グループを含むツール バーが表示されます。  
  
> [!NOTE]
>  GUID を使用して別の方法で指定された場所以外ツール バーおよびグループはGUID を使用します `guidSHLMainMenu`: ID の構文。  GUID はツール バーに指定した場合もそのツール バーの子グループに適用されます。  
  
|ツール ウィンドウ|ツール バー|グループ|  
|---------------|------------|----------|  
|ソリューション エクスプローラー|IDM\_VS\_TOOL\_PROJWIN|IDG\_VS\_PROJ\_TOOLBAR1..5|  
|サーバー エクスプローラー|guid\_SE\_MenuGroup: IDM\_SE\_TOOLBAR\_SERVEREXPLORER|IDG\_SE\_TOOLBAR\_REFRESH|  
|プロパティ|IDM\_VS\_TOOL\_PROPERTIES|IDG\_VS\_PROPERTIES\_SORT<br /><br /> IDG\_VS\_PROPERTIES\_PAGES|  
|クラス ビュー|IDM\_VS\_TOOL\_CLASSVIEW|IDG\_VS\_CLASSVIEW\_FOLDERS<br /><br /> IDG\_VS\_CLASSVIEW\_SEARCH<br /><br /> IDG\_VS\_CLASSVIEW\_SETTINGS|  
|クラス ビュー|IDM\_VS\_TOOL\_CLASSVIEW\_GO|IDG\_VS\_CLASSVIEW\_SEARCH2|  
|オブジェクト ブラウザー|IDM\_VS\_TOOL\_OBJBROWSER|IDG\_VS\_OBJBROWSER\_SUBSETS<br /><br /> IDG\_VS\_OBJBROWSER\_SEARCH<br /><br /> IDG\_VS\_OBJBROWSER\_ADDREFERENCE<br /><br /> IDG\_VS\_OBJBROWSER\_BROWSERSETTINGS|  
|オブジェクト ブラウザー|IDM\_VS\_TOOL\_OBJECT\_BROWSER\_GO|IDG\_VS\_OBJBROWSER\_SEARCH2|  
|出力|IDM\_VS\_TOOL\_OUTPUTWINDOW|IDG\_VS\_OUTPUTWINDOW\_SELECT<br /><br /> IDG\_VS\_OUTPUTWINDOW\_GOTO<br /><br /> IDG\_VS\_OUTPUTWINDOW\_NEXTPREV<br /><br /> IDG\_VS\_OUTPUTWINDOW\_CLEAR<br /><br /> IDG\_VS\_OUTPUTWINDOW\_WORDWRAP|  
|検索と置換|IDM\_VS\_TOOL\_UNIFIEDFIND|IDG\_VS\_FINDTAB<br /><br /> IDG\_VS\_REPLACETAB|  
|検索結果 1|IDM\_VS\_TOOL\_FINDRESULTS1|IDG\_VS\_FINDRESULTS1\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS1\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS1\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS1\_STOPFIND|  
|検索結果 2|IDM\_VS\_TOOL\_FINDRESULTS2|IDG\_VS\_FINDRESULTS2\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS2\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS2\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS2\_STOPFIND|  
|Snippet|IDM\_VS\_TOOL\_SNIPPETMENUS|IDG\_VS\_SNIPPET\_REPL<br /><br /> IDG\_VS\_SNIPPET\_REF<br /><br /> IDG\_VS\_SNIPPET\_PROP|  
|ブックマーク|IDM\_VS\_TOOL\_BOOKMARKWIND|IDG\_VS\_BWNEWFOLDER<br /><br /> IDG\_VS\_BWNEXTBM<br /><br /> IDG\_VS\_BWNEXTBMF<br /><br /> IDG\_VS\_BWENABLE<br /><br /> IDG\_VS\_BWDELETE|  
|タスク一覧|IDM\_VS\_TOOL\_TASKLIST|IDG\_VS\_TASKLIST\_PROVIDERLIST|  
|ユーザー タスク|IDM\_VS\_TOOL\_USERTASKS|IDG\_VS\_TASKLIST\_PROVIDERLIST<br /><br /> IDG\_VS\_USERTASKS\_EDIT|  
|エラー一覧|IDM\_VS\_TOOL\_ERRORLIST|IDG\_VS\_ERRORLIST\_ERRORGROUP<br /><br /> IDG\_VS\_ERRORLIST\_WARNINGGROUP<br /><br /> IDG\_VS\_ERRORLIST\_MESSAGEGROUP|  
|呼び出しブラウザー|IDM\_VS\_TOOL\_CALLBROWSER1..16|IDG\_VS\_TOOLBAR\_CALLBROWSER1\_ACTIONS<br /><br /> IDG\_VS\_TOOLBAR\_CALLBROWSER1\_TYPE<br /><br /> IDG\_VS\_TOOLBAR\_CALLBROWSER1\_CBSETTINGS|  
|ブレークポイント|guidVSDebugGroup: IDM\_BREAKPOINTS\_WINDOW\_TOOLBAR|IDG\_BREAKPOINTS\_WINDOW\_NEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_DELETE<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_ALL<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_VIEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_EDIT<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_COLUMNS|  
|逆アセンブル|guidVSDebugGroup: IDM\_DISASM\_WINDOW\_TOOLBAR|IDG\_DISASM\_WINDOW\_TOOLBAR|  
|メモリに書き込みません|guidVSDebugGroup: IDM\_MEMORY\_WINDOW\_TOOLBAR1 … 4|IDG\_MEMORY\_EXPRESSION1..4<br /><br /> IDG\_MEMORY\_COLUMNS1..4|  
|\[プロセス\]|guidVSDebugGroup: IDM\_ATTACHED\_PROCS\_TOOLBAR|IDG\_ATTACHED\_PROCS\_EXECCNTRL IDG\_ATTACHED\_PROCS\_STEPPING<br /><br /> IDG\_ATTACHED\_PROCS\_EXECCNTRL2<br /><br /> IDG\_ATTACHED\_PROCS\_ATTACH<br /><br /> IDG\_ATTACHED\_PROCS\_COLUMNS|  
  
## 参照  
 [ツールバー\] メニューの \[コント ローラーの追加](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [ツール ウィンドウに、ツールバーを追加します。](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Guid と Visual Studio のメニューの Id](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)