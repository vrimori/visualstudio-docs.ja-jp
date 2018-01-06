---
title: "Visual Studio のメニューの Guid と Id |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 69ad8f62931b628582c73a3e370a86611795caa6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Visual Studio のメニューの Guid と Id
このトピックでは、メニューや Visual Studio のメニュー バー上のグループの GUID と ID の値を列挙します。 これらの値は、Visual Studio SDK の一部としてインストールされている .vsct ファイルで定義されます。 詳細については、次を参照してください。 [IDE-Defined コマンド、メニュー、およびグループ](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)です。  
  
 .Vsct ファイルで定義されている統合開発環境 (IDE) オブジェクトを操作する方法の詳細については、次を参照してください。[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)です。  
  
 メニューと Visual Studio のメニュー バー上のグループは、GUID を使用して`guidSHLMainMenu`です。 メニュー バー自体が、ID の`IDM_VS_TOOL_MAINMENU`します。  
  
## <a name="groups-on-the-visual-studio-menu-bar"></a>Visual Studio のメニュー バー上のグループ  
 メニュー バーにメニューを追加するには、その親としてこれらのグループのいずれかを設定します。  
  
|グループ化|ID|  
|-----------|--------|  
|ファイル/編集/表示|IDG_VS_MM_FILEEDITVIEW|  
|リファクタリング|IDG_VS_MM_REFACTORING:|  
|プロジェクト|IDG_VS_MM_PROJECT|  
|ビルド|IDG_VS_MM_BUILDDEBUGRUN|  
|形式/ツール|IDG_VS_MM_TOOLSADDINS|  
|ウィンドウまたはヘルプ/コミュニティ|IDG_VS_MM_WINDOWHELP|  
|Addins|IDG_VS_MM_MACROS|  
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|  
  
## <a name="menus-on-the-visual-studio-menu-bar"></a>Visual Studio のメニュー バーのメニュー  
 グループを追加するには、既存の Visual Studio メニューに、その親として、次のメニューのいずれかを設定します。 この一覧には、サブメニューは含まれません。  
  
|メニュー|ID|  
|----------|--------|  
|ファイル|IDM_VS_MENU_FILE|  
|編集|IDM_VS_MENU_EDIT|  
|表示|IDM_VS_MENU_VIEW|  
|リファクター|IDM_VS_MENU_REFACTORING|  
|プロジェクト|IDM_VS_MENU_PROJECT|  
|ビルド|IDM_VS_MENU_BUILD|  
|形式|IDM_VS_MENU_FORMAT|  
|ツール|IDM_VS_MENU_TOOLS|  
|ウィンドウ|IDM_VS_MENU_WINDOW|  
|Addins|IDM_VS_MENU_ADDINS|  
|コミュニティ|IDM_VS_MENU_COMMUNITY|  
|ヘルプ|IDM_VS_MENU_HELP|  
  
## <a name="groups-on-visual-studio-menus"></a>Visual Studio のメニュー上のグループ  
 次の表は、Visual Studio メニュー バーで、メニューから直接派生したグループを示します。 Visual Studio のメニューにコマンドを追加する最も簡単な方法では、これらのグループのいずれかを親として設定します。 サブメニューから派生したグループは、このセクションでは表示されません。  
  
### <a name="file-menu-groups"></a>ファイル メニュー グループ  
  
|グループ化|ID|  
|-----------|--------|  
|新しいオープン/|IDG_VS_FILE_FILE|  
|追加|IDG_VS_FILE_ADD|  
|ソリューション|IDG_VS_FILE_SOLUTION|  
|[その他]|IDG_VS_FILE_MISC|  
|保存|IDG_VS_FILE_SAVE|  
|名前の変更|IDG_VS_FILE_RENAME|  
|ブラウザー|IDG_VS_FILE_BROWSER|  
|の|IDG_VS_FILE_PRINT|  
|最近使った|IDG_VS_FILE_MRU|  
|移動|IDG_VS_FILE_MOVE|  
|終了|IDG_VS_FILE_EXIT|  
  
### <a name="edit-menu-groups"></a>メニュー グループを編集します。  
  
|グループ化|ID|  
|-----------|--------|  
|元に戻す/やり直し|IDG_VS_EDIT_UNDOREDO|  
|切り取り/コピー/貼り付け|IDG_VS_EDIT_CUTCOPY|  
|選択|IDG_VS_EDIT_SELECT|  
|GoTo|IDG_VS_EDIT_GOTO|  
|[検索]|IDG_VS_EDIT_FIND|  
|オブジェクト|IDG_VS_EDIT_OBJECTS|  
|OLE の動作|IDG_VS_EDIT_OLEVERBS|  
|コマンドします。|IDG_VS_EDIT_COMMANDWELL|  
  
### <a name="refactor-menu-groups"></a>メニュー グループをリファクターします。  
  
|グループ化|ID|  
|-----------|--------|  
|Common|IDG_REFACTORING_COMMON|  
|詳細設定|IDG_REFACTORING_ADVANCED|  
  
### <a name="view-menu-groups"></a>メニュー グループの表示  
  
|グループ化|ID|  
|-----------|--------|  
|フォームのコード|IDG_VS_VIEW_FORMCODE|  
|ブラウザー|IDG_VS_VIEW_BROWSER|  
|ビューを定義します。|IDG_VS_VIEW_DEFINEVIEWS|  
|Windows|IDG_VS_VIEW_WINDOWS|  
|Windows を設計します。|IDG_VS_VIEW_ARCH_WINDOWS|  
|組織の Windows|IDG_VS_VIEW_ORG_WINDOWS|  
|コードのブラウザー|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|  
|開発用の Windows|IDG_VS_VIEW_DEV_WINDOWS|  
|ツールバー|IDG_VS_VIEW_TOOLBARS|  
|シンボル|IDG_VS_VIEW_SYMBOLNAVIGATE|  
|移動|IDG_VS_VIEW_NAVIGATE|  
|小規模の移動します。|IDG_VS_VIEW_SMALLNAVIGATE|  
|オブジェクト ブラウザー|IDG_VS_VIEW_OBJBRWSR|  
|コマンドします。|IDG_VS_VIEW_COMMANDWELL|  
|プロパティ ページ|IDG_VS_VIEW_PROPPAGES|  
|最新の情報に更新|IDG_VS_VIEW_REFRESH|  
  
### <a name="project-menu-groups"></a>プロジェクトのメニュー グループ  
  
|グループ化|ID|  
|-----------|--------|  
|その他の追加|IDG_VS_PROJ_MISCADD|  
|追加|IDG_VS_PROJ_ADD|  
|フォルダー|IDG_VS_PROJ_FOLDER|  
|アンロード/再読み込み|IDG_VS_PROJ_UNLOADRELOAD|  
|参照|IDG_VS_PROJ_REFERENCE|  
|オプション|IDG_VS_PROJ_OPTIONS|  
|設定|IDG_VS_PROJ_SETTINGS|  
  
### <a name="build-menu-groups"></a>メニュー グループを作成します。  
  
|グループ化|ID|  
|-----------|--------|  
|ソリューション|IDG_VS_BUILD_SOLUTION|  
|選択ツール|IDG_VS_BUILD_SELECTION|  
|ガイド付き最適化のプロファイル|IDG_VS_PGO_SELECTION|  
|その他|IDG_VS_BUILD_MISC|  
|キャンセル|IDG_VS_BUILD_CANCEL|  
  
### <a name="tools-menu-groups"></a>ツール メニュー グループ  
  
|グループ化|ID|  
|-----------|--------|  
|コマンド ライン|IDG_VS_TOOLS_CMDLINE|  
|スニペット|IDG_VS_TOOLS_SNIPPETS|  
|オブジェクトのサブセット|IDG_VS_TOOLS_OBJSUBSET|  
|オプション|IDG_VS_TOOLS_OPTIONS|  
|その他の 2|IDG_VS_TOOLS_OTHER2|  
|外部ツール|IDG_VS_TOOLS_EXT_TOOLS|  
|外部のカスタマイズ|IDG_VS_TOOLS_EXT_CUST|  
  
### <a name="window-menu-groups"></a>ウィンドウ メニュー グループ  
  
|グループ化|ID|  
|-----------|--------|  
|新規作成|IDG_VS_WINDOW_NEW|  
|ドッキング/閉じる|IDG_VS_DOCKCLOSE|  
|ドッキング ステーション/非表示|IDG_VS_DOCKHIDE|  
|配置します。|IDG_VS_WINDOW_ARRANGE|  
|ナビゲーション|IDG_VS_WINDOW_NAVIGATION|  
|リスト|IDG_VS_WINDOW_LIST|  
  
### <a name="help-menu-groups"></a>ヘルプ メニュー グループ  
  
|グループ化|ID|  
|-----------|--------|  
|サンプル|IDG_VS_HELP_SAMPLES|  
|サポート|IDG_VS_HELP_SUPPORT|  
|バージョン情報|IDG_VS_HELP_ABOUT|  
  
## <a name="submenus-of-visual-studio-menus"></a>Visual Studio のメニューのサブメニュー  
 次の階層は、Visual Studio のメニュー バーのメニューに関連付けられているサブメニューを示しています。 グループのみがその親としてのメニューを持てないためすべてのサブメニュー必要があります下りるグループから、メニューの代わりに、メニューから直接。 メニューのグループ、およびサブメニューの間のリレーションシップに関する詳細については、次を参照してください。[メニューにサブメニューを追加](../../extensibility/adding-a-submenu-to-a-menu.md)です。  
  
> [!NOTE]
>  Visual Studio のメニュー バーのメニューの名前は個別に表示されませんこの階層では次のように IDE では、グループの名前付け規則から推論できます: IDG_VS_*メニュー名*_*グループ名*.  
  
|親グループ|サブメニュー|子グループ|  
|------------------|-------------|------------------|  
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|  
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|  
|||IDG_VS_FILE_OPENF_CASCADE|  
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|  
|||IDG_VS_FILE_ADD_PROJECT_EXI|  
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|  
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|  
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|  
|||IDG_VS_FILE_MOVE_PICKER|  
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|  
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|  
|||IDG_VS_WNDO_OTRWNDWS1 しています.6|  
|||IDG_VS_WNDO_WINDOWS2|  
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||  
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||  
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|  
|||IDG_VS_MNUDES_EDITNAMES|  
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|  
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|  
|||IDG_VS_BUILD_PROJPICKER|  
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|  
|||IDG_VS_REBUILD_PROJPICKER|  
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|  
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|  
|||IDG_VS_CLEAN_PROJPICKER|  
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|  
|||IDG_VS_DEPLOY_PROJPICKER|  
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|  
|||IDG_VS_PGO_BUILD_CASCADE_RUN|  
  
## <a name="see-also"></a>参照  
 [Visual Studio ツールバーの Guid と Id](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [Visual Studio のコマンドの Guid と Id](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Visual Studio Command Table (.Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)