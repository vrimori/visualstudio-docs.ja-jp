---
title: Visual Studio のメニューの Guid および Id |Microsoft Docs
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
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72ba04f5f33b3b9ef5030326fddb69d83e0a8f9d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762693"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Visual Studio メニューの GUID および ID
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックでは、メニューおよび Visual Studio のメニュー バーでのグループの GUID と ID の値を列挙します。 これらの値は、Visual Studio SDK の一部としてインストールされている .vsct ファイルで定義されます。 詳細については、次を参照してください。 [IDE-Defined コマンド、メニュー、およびグループ](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)します。  
  
 .Vsct ファイルで定義されている統合開発環境 (IDE) のオブジェクトを操作する方法の詳細については、次を参照してください。[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)します。  
  
 メニューおよび Visual Studio のメニュー バーでのグループは、GUID を使用して`guidSHLMainMenu`します。 メニュー バー自体の ID を持つ`IDM_VS_TOOL_MAINMENU`します。  
  
## <a name="groups-on-the-visual-studio-menu-bar"></a>Visual Studio のメニュー バー上のグループ  
 メニュー バーにメニューを追加するには、親としてこれらのグループのいずれかを設定します。  
  
|グループ化|ID|  
|-----------|--------|  
|ファイル/編集/表示|IDG_VS_MM_FILEEDITVIEW|  
|リファクタリング|IDG_VS_MM_REFACTORING:|  
|プロジェクト|IDG_VS_MM_PROJECT|  
|ビルド|IDG_VS_MM_BUILDDEBUGRUN|  
|形式/ツール|IDG_VS_MM_TOOLSADDINS|  
|ウィンドウ、構造体、コミュニティのヘルプ|IDG_VS_MM_WINDOWHELP|  
|Addins|IDG_VS_MM_MACROS|  
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|  
  
## <a name="menus-on-the-visual-studio-menu-bar"></a>Visual Studio のメニュー バーのメニュー  
 既存の Visual Studio のメニューには、グループを追加するには、親として、次のメニューのいずれかを設定します。 サブメニューは、この一覧には含まれません。  
  
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
|[Window]|IDM_VS_MENU_WINDOW|  
|Addins|IDM_VS_MENU_ADDINS|  
|コミュニティ|IDM_VS_MENU_COMMUNITY|  
|ヘルプ|IDM_VS_MENU_HELP|  
  
## <a name="groups-on-visual-studio-menus"></a>Visual Studio のメニュー上のグループ  
 次の表では、Visual Studio のメニュー バーにあるメニューから直接探索するグループを示します。 Visual Studio のメニューにコマンドを追加する最も簡単な方法では、これらのグループのいずれかを親として設定します。 サブメニューから派生したグループは、このセクションでは表示されません。  
  
### <a name="file-menu-groups"></a>ファイル メニュー グループ  
  
|グループ化|ID|  
|-----------|--------|  
|新しい/オープン|IDG_VS_FILE_FILE|  
|追加|IDG_VS_FILE_ADD|  
|ソリューション|IDG_VS_FILE_SOLUTION|  
|[その他]|IDG_VS_FILE_MISC|  
|保存|IDG_VS_FILE_SAVE|  
|名前の変更|IDG_VS_FILE_RENAME|  
|ブラウザー|IDG_VS_FILE_BROWSER|  
|の|IDG_VS_FILE_PRINT|  
|最近使用されました。|IDG_VS_FILE_MRU|  
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
  
### <a name="refactor-menu-groups"></a>メニュー グループをリファクタリングします。  
  
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
|Windows の開発|IDG_VS_VIEW_DEV_WINDOWS|  
|ツールバー|IDG_VS_VIEW_TOOLBARS|  
|シンボル|IDG_VS_VIEW_SYMBOLNAVIGATE|  
|移動|IDG_VS_VIEW_NAVIGATE|  
|小規模に移動します|IDG_VS_VIEW_SMALLNAVIGATE|  
|オブジェクト ブラウザー|IDG_VS_VIEW_OBJBRWSR|  
|コマンドします。|IDG_VS_VIEW_COMMANDWELL|  
|プロパティ ページ|IDG_VS_VIEW_PROPPAGES|  
|最新の情報に更新|IDG_VS_VIEW_REFRESH|  
  
### <a name="project-menu-groups"></a>プロジェクト メニュー グループ  
  
|グループ化|ID|  
|-----------|--------|  
|その他の追加|IDG_VS_PROJ_MISCADD|  
|追加|IDG_VS_PROJ_ADD|  
|フォルダー|IDG_VS_PROJ_FOLDER|  
|アンロード/リロード|IDG_VS_PROJ_UNLOADRELOAD|  
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
  
### <a name="tools-menu-groups"></a>ツールのメニュー グループ  
  
|グループ化|ID|  
|-----------|--------|  
|コマンド ライン|IDG_VS_TOOLS_CMDLINE|  
|スニペット|IDG_VS_TOOLS_SNIPPETS|  
|オブジェクトのサブセット|IDG_VS_TOOLS_OBJSUBSET|  
|オプション|IDG_VS_TOOLS_OPTIONS|  
|その他の 2|IDG_VS_TOOLS_OTHER2|  
|外部ツール|IDG_VS_TOOLS_EXT_TOOLS|  
|外部のカスタマイズ|IDG_VS_TOOLS_EXT_CUST|  
  
### <a name="window-menu-groups"></a>ウィンドウのメニュー グループ  
  
|グループ化|ID|  
|-----------|--------|  
|新規作成|IDG_VS_WINDOW_NEW|  
|Dock/閉じる|IDG_VS_DOCKCLOSE|  
|Dock/非表示|IDG_VS_DOCKHIDE|  
|配置します。|IDG_VS_WINDOW_ARRANGE|  
|ナビゲーション|IDG_VS_WINDOW_NAVIGATION|  
|リスト|IDG_VS_WINDOW_LIST|  
  
### <a name="help-menu-groups"></a>ヘルプ メニューのグループ  
  
|グループ化|ID|  
|-----------|--------|  
|サンプル|IDG_VS_HELP_SAMPLES|  
|サポート|IDG_VS_HELP_SUPPORT|  
|バージョン情報|IDG_VS_HELP_ABOUT|  
  
## <a name="submenus-of-visual-studio-menus"></a>Visual Studio のメニューのサブメニュー  
 次の階層には、Visual Studio のメニュー バーのメニューに関連付けられているサブメニューが表示されます。 グループのみがその親としてのメニューを持てないためすべてサブメニューで開く必要があります降下グループから、メニューの代わりに、メニューから直接。 メニューのグループ、およびサブメニューの間のリレーションシップの詳細については、次を参照してください。[サブメニューのメニューに追加](../../extensibility/adding-a-submenu-to-a-menu.md)します。  
  
> [!NOTE]
>  Visual Studio のメニュー バーのメニューの名前は個別に表示されませんこの階層では次のように IDE では、グループの名前付け規則から推論できるため、: IDG_VS_*メニュー名*_*のグループ名*.  
  
|親グループ|サブメニューで開く|子グループ|  
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
|||IDG_VS_WNDO_OTRWNDWS1.6|  
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
  
## <a name="see-also"></a>関連項目  
 [Visual Studio ツールバーの Guid および Id](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [Visual Studio のコマンドの Guid および Id](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Visual Studio Command Table (.Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

