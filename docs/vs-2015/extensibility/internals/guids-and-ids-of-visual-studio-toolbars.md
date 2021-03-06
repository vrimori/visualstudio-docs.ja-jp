---
title: Visual Studio ツールバーの Guid および Id |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3cc4319699316df1166372b43e7db1aa1b4f496
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807550"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Visual Studio ツール バーの GUID および ID
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックでは、Visual Studio 統合開発環境 (IDE) に含まれているツールバーの GUID と ID の値を列挙し、含まれているグループのします。 これらの値は、Visual Studio SDK の一部としてインストールされている .vsct ファイルで定義されます。 詳細については、次を参照してください。 [IDE-Defined コマンド、メニュー、およびグループ](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)します。  
  
> [!NOTE]
>  Visual Studio を使用できるツールバーの多くが Visual Studio、およびその GUID によって定義されていないと、ID 値がパブリックではありません。 このトピックでは、Visual Studio SDK .vsct ファイルで定義されているツールバーだけを使用します。  
  
 .Vsct ファイルで定義されている IDE オブジェクトを操作する方法の詳細については、次を参照してください。[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)します。  
  
 Visual Studio IDE によって提供される既定のツールバーは、GUID を使用して`guidSHLMainMenu`GUID:ID の構文を使用して、それ以外の場合に指定されている場合を除きします。  
  
## <a name="ide-toolbars"></a>IDE ツールバー  
 次のツールバーは、Visual Studio IDE によって提供されます。 選択してツールバーを表示することができます、**ツールバー**のサブメニューで開く、**ツール**メニュー。 このセクションでは、ツール ウィンドウのツールバーは含まれません。  
  
 ツールバーから直接グループのみが探索できます。 グループを追加するには、GUID と、ツールバーの ID をその親を設定します。 ツールバーにボタンを追加するには、ツールバーの親をグループに設定します。  
  
|ツール バー|ID|  
|-------------|--------|  
|標準|IDM_VS_TOOL_STANDARD|  
|ビルド|IDM_VS_TOOL_BUILD|  
|[テキスト エディター]|IDM_VS_TOOL_TEXTEDITOR|  
|デバッグ|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|  
|デバッグの場所|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|  
  
### <a name="special-toolbars"></a>特別なツールバー  
 これらのツールバーは、Visual Studio IDE によって定義されますが、特殊な機能を果たす、コマンド グループをホストしていません。  
  
|ツール バー|ID|  
|-------------|--------|  
|コマンドの追加|IDM_VS_TOOL_ADDCOMMAND|  
|未定義|IDM_VS_TOOL_UNDEFINED|  
|XML スキーマ|IDM_VS_TOOL_SCHEMA|  
|XML データ|IDM_VS_TOOL_DATA|  
  
## <a name="groups-on-the-ide-toolbars"></a>IDE ツールバー上のグループ  
 標準ツールバーにボタンを追加するには、親としてグループは次のいずれかを設定します。 親ツールバーでは、グループが並べ替えられます。  
  
### <a name="standard-toolbar-groups"></a>標準ツールバーのグループ  
  
|名前|ID|  
|----------|--------|  
|保存/開く|IDG_VS_TOOLSB_SAVEOPEN|  
|切り取り/コピー|IDG_VS_TOOLSB_CUTCOPY|  
|元に戻す/やり直し|IDG_VS_TOOLSB_UNDOREDO|  
|実行/ビルド|IDG_VS_TOOLSB_RUNBUILD|  
|検索|IDG_VS_TOOLSB_SEARCH|  
|Windows|IDG_VS_TOOLSB_WINDOWS|  
|新しい Windows|IDG_VS_TOOLSB_NEWWINDOWS|  
|読み込みと保存|IDG_VS_WINDOWUI_LOADSAVE|  
|ゲージ|IDG_VS_TOOLSB_GAUGE|  
  
### <a name="build-toolbar-groups"></a>ツールバーのグループを作成します。  
  
|名前|ID|  
|----------|--------|  
|ビルドのバー|IDG_VS_BUILDBAR|  
|キャンセル|IDG_VS_BUILD_CANCEL|  
  
### <a name="text-editor-toolbar-groups"></a>テキスト エディター ツールバーのグループ  
  
|名前|ID|  
|----------|--------|  
|完了|IDM_VS_TOOL_TEXTEDITOR|  
|Indent|IDG_VS_EDITTOOLBAR_INDENT|  
|コメント|IDG_VS_EDITTOOLBAR_COMMENT|  
|ブックマーク|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|  
  
### <a name="debug-toolbar-groups"></a>デバッグ ツールバーのグループ  
  
|名前|ID|  
|----------|--------|  
|実行|IDM_DEBUG_TOOLBAR|  
|ステップ実行|IDG_DEBUG_TOOLBAR_STEPPING|  
|Watch|IDG_DEBUG_TOOLBAR_WATCH|  
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|  
  
### <a name="debug-location-toolbar-groups"></a>デバッグの場所 ツールバーのグループ  
  
|名前|ID|  
|----------|--------|  
|デバッグの場所|IDG_DEBUG_CONTEXT_TOOLBAR|  
  
## <a name="tool-window-toolbars"></a>ツール ウィンドウのツールバー  
 ツールバー表示できるツール ウィンドウまたは IDE で直接など**ソリューション エクスプ ローラー**します。 ツール ウィンドウが .vsct ファイルで定義されていないため、ツール ウィンドウのツールバーには定義済みの親はありません。 代わりに、コード内に配置されます。 次の表は、IDE では、ツール ウィンドウに表示されるツールバーおよび含まれるコマンド グループを示します。  
  
> [!NOTE]
>  ツールバーとグループは、GUID を使用して`guidSHLMainMenu`GUID:ID の構文を使用して、それ以外の場合に指定されている場合を除きします。 ツールバーの GUID が指定されているそのツールバーから派生したグループにも適用されます。  
  
|ツール ウィンドウ|ツール バー|グループ|  
|-----------------|-------------|------------|  
|ソリューション エクスプローラー|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1.5|  
|サーバー エクスプローラー|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|  
|プロパティ|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|  
|クラス ビュー|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|  
|クラス ビュー|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|  
|オブジェクト ブラウザー|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|  
|オブジェクト ブラウザー|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|  
|出力|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|  
|検索と置換|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|  
|検索結果 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|  
|検索結果 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|  
|スニペット|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|  
|ブックマーク|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|  
|タスク一覧|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|  
|ユーザー タスク|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|  
|エラー一覧|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|  
|呼び出しブラウザー|IDM_VS_TOOL_CALLBROWSER1.16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|  
|ブレークポイント|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|  
|逆アセンブリ|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|  
|1 ~ 4 のメモリ|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1.4|IDG_MEMORY_EXPRESSION1.4<br /><br /> IDG_MEMORY_COLUMNS1.4|  
|プロセス|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|  
  
## <a name="see-also"></a>関連項目  
 [ツールバーにメニュー コント ローラーの追加](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [ツール ウィンドウにツールバーを追加します。](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Visual Studio メニューの GUID および ID](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

