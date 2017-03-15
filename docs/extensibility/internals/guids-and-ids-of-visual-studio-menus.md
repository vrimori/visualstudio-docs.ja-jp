---
title: "Guid と Visual Studio のメニューの Id | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visual studio のメニュー"
  - "visual studio のグループ"
  - "ID"
  - "既存のメニュー"
  - "guid"
  - "メニュー"
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Guid と Visual Studio のメニューの Id
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

このトピックでは、メニューおよび Visual Studio のメニュー バーでのグループの GUID と ID の値を列挙します。 これらの値は、Visual Studio SDK の一部としてインストールされている .vsct ファイルで定義されます。 詳細については、「[IDE 定義コマンド、メニューのおよびグループ](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)」を参照してください。  
  
 .Vsct ファイルで定義されている統合開発環境 \(IDE\) のオブジェクトを操作する方法の詳細については、次を参照してください。 [拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)します。  
  
 メニューと Visual Studio のメニュー バー上のグループは、GUID を使用して `guidSHLMainMenu`します。 メニュー バー自体の ID を持つ `IDM_VS_TOOL_MAINMENU`です。  
  
## Visual Studio のメニュー バー上のグループ  
 メニューをメニュー バーに追加するには、親とこれらのグループのいずれかを設定します。  
  
|グループ化|ID|  
|-----------|--------|  
|ファイル\/編集\/表示|IDG\_VS\_MM\_FILEEDITVIEW|  
|リファクタリング|IDG\_VS\_MM\_REFACTORING:|  
|プロジェクト|IDG\_VS\_MM\_PROJECT|  
|ビルド|IDG\_VS\_MM\_BUILDDEBUGRUN|  
|書式\/ツール|IDG\_VS\_MM\_TOOLSADDINS|  
|ウィンドウ\/ヘルプとコミュニティ|IDG\_VS\_MM\_WINDOWHELP|  
|アドイン|IDG\_VS\_MM\_MACROS|  
|FullScreenBar|IDG\_VS\_MM\_FULLSCREENBAR|  
  
## Visual Studio のメニュー バーのメニュー  
 グループを既存の Visual Studio のメニューを追加するには、親と次のメニュー項目のいずれかを設定します。 サブメニューは、この一覧には含まれません。  
  
|メニュー|ID|  
|----------|--------|  
|ファイル|IDM\_VS\_MENU\_FILE|  
|編集|IDM\_VS\_MENU\_EDIT|  
|表示|IDM\_VS\_MENU\_VIEW|  
|リファクター|IDM\_VS\_MENU\_REFACTORING|  
|プロジェクト|IDM\_VS\_MENU\_PROJECT|  
|ビルド|IDM\_VS\_MENU\_BUILD|  
|形式|IDM\_VS\_MENU\_FORMAT|  
|ツール|IDM\_VS\_MENU\_TOOLS|  
|ウィンドウ|IDM\_VS\_MENU\_WINDOW|  
|アドイン|IDM\_VS\_MENU\_ADDINS|  
|コミュニティ|IDM\_VS\_MENU\_COMMUNITY|  
|\[Help\]|IDM\_VS\_MENU\_HELP|  
  
## Visual Studio のメニュー上のグループ  
 次の一覧は、Visual Studio のメニュー バーで、メニューから直接派生したグループを示します。 Visual Studio のメニューにコマンドを追加する最も簡単な方法では、これらのグループを親として設定します。 サブメニューから派生したグループは、このセクションでは表示されません。  
  
### ファイル メニュー グループ  
  
|グループ化|ID|  
|-----------|--------|  
|新しい、または開く|IDG\_VS\_FILE\_FILE|  
|追加|IDG\_VS\_FILE\_ADD|  
|ソリューション|IDG\_VS\_FILE\_SOLUTION|  
|\[その他\]|IDG\_VS\_FILE\_MISC|  
|保存|IDG\_VS\_FILE\_SAVE|  
|名前の変更|IDG\_VS\_FILE\_RENAME|  
|ブラウザー|IDG\_VS\_FILE\_BROWSER|  
|印刷|IDG\_VS\_FILE\_PRINT|  
|最近使った|IDG\_VS\_FILE\_MRU|  
|移動|IDG\_VS\_FILE\_MOVE|  
|終了|IDG\_VS\_FILE\_EXIT|  
  
### メニュー グループを編集します。  
  
|グループ化|ID|  
|-----------|--------|  
|元に戻す\/やり直し|IDG\_VS\_EDIT\_UNDOREDO|  
|切り取り\/コピー\/貼り付け|IDG\_VS\_EDIT\_CUTCOPY|  
|選択|IDG\_VS\_EDIT\_SELECT|  
|GoTo|IDG\_VS\_EDIT\_GOTO|  
|\[検索\]|IDG\_VS\_EDIT\_FIND|  
|オブジェクト|IDG\_VS\_EDIT\_OBJECTS|  
|OLE の動作|IDG\_VS\_EDIT\_OLEVERBS|  
|コマンドします。|IDG\_VS\_EDIT\_COMMANDWELL|  
  
### メニュー グループをリファクタリングします。  
  
|グループ化|ID|  
|-----------|--------|  
|Common|IDG\_REFACTORING\_COMMON|  
|詳細設定|IDG\_REFACTORING\_ADVANCED|  
  
### メニュー グループを表示します。  
  
|グループ化|ID|  
|-----------|--------|  
|フォームのコード|IDG\_VS\_VIEW\_FORMCODE|  
|ブラウザー|IDG\_VS\_VIEW\_BROWSER|  
|ビューを定義します。|IDG\_VS\_VIEW\_DEFINEVIEWS|  
|Windows|IDG\_VS\_VIEW\_WINDOWS|  
|Windows を設計します。|IDG\_VS\_VIEW\_ARCH\_WINDOWS|  
|組織の Windows|IDG\_VS\_VIEW\_ORG\_WINDOWS|  
|コードのブラウザー|IDG\_VS\_VIEW\_CODEBROWSENAV\_WINDOWS|  
|開発用の Windows|IDG\_VS\_VIEW\_DEV\_WINDOWS|  
|ツールバー|IDG\_VS\_VIEW\_TOOLBARS|  
|シンボル|IDG\_VS\_VIEW\_SYMBOLNAVIGATE|  
|移動|IDG\_VS\_VIEW\_NAVIGATE|  
|小規模の移動します。|IDG\_VS\_VIEW\_SMALLNAVIGATE|  
|オブジェクト ブラウザー|IDG\_VS\_VIEW\_OBJBRWSR|  
|コマンドします。|IDG\_VS\_VIEW\_COMMANDWELL|  
|\[プロパティ ページ\]|IDG\_VS\_VIEW\_PROPPAGES|  
|最新の情報に更新|IDG\_VS\_VIEW\_REFRESH|  
  
### プロジェクトのメニュー グループ  
  
|グループ化|ID|  
|-----------|--------|  
|その他の追加|IDG\_VS\_PROJ\_MISCADD|  
|追加|IDG\_VS\_PROJ\_ADD|  
|フォルダー|IDG\_VS\_PROJ\_FOLDER|  
|アンロード\/再読み込み|IDG\_VS\_PROJ\_UNLOADRELOAD|  
|参照|IDG\_VS\_PROJ\_REFERENCE|  
|オプション|IDG\_VS\_PROJ\_OPTIONS|  
|設定|IDG\_VS\_PROJ\_SETTINGS|  
  
### メニュー グループを作成します。  
  
|グループ化|ID|  
|-----------|--------|  
|ソリューション|IDG\_VS\_BUILD\_SOLUTION|  
|選択ツール|IDG\_VS\_BUILD\_SELECTION|  
|ガイド付き最適化のプロファイル|IDG\_VS\_PGO\_SELECTION|  
|その他の指定|IDG\_VS\_BUILD\_MISC|  
|キャンセル|IDG\_VS\_BUILD\_CANCEL|  
  
### ツールのメニュー グループ  
  
|グループ化|ID|  
|-----------|--------|  
|コマンド ライン|IDG\_VS\_TOOLS\_CMDLINE|  
|スニペット|IDG\_VS\_TOOLS\_SNIPPETS|  
|オブジェクトのサブセット|IDG\_VS\_TOOLS\_OBJSUBSET|  
|オプション|IDG\_VS\_TOOLS\_OPTIONS|  
|その他の 2|IDG\_VS\_TOOLS\_OTHER2|  
|外部ツール|IDG\_VS\_TOOLS\_EXT\_TOOLS|  
|外部のカスタマイズ|IDG\_VS\_TOOLS\_EXT\_CUST|  
  
### ウィンドウのメニュー グループ  
  
|グループ化|ID|  
|-----------|--------|  
|新規作成|IDG\_VS\_WINDOW\_NEW|  
|ドッキング ステーション\/閉じる|IDG\_VS\_DOCKCLOSE|  
|ドッキング ステーション\/非表示|IDG\_VS\_DOCKHIDE|  
|配置|IDG\_VS\_WINDOW\_ARRANGE|  
|ナビゲーション|IDG\_VS\_WINDOW\_NAVIGATION|  
|リスト|IDG\_VS\_WINDOW\_LIST|  
  
### ヘルプ メニュー グループ  
  
|グループ化|ID|  
|-----------|--------|  
|サンプル|IDG\_VS\_HELP\_SAMPLES|  
|Support|IDG\_VS\_HELP\_SUPPORT|  
|バージョン情報|IDG\_VS\_HELP\_ABOUT|  
  
## Visual Studio のメニューのサブメニュー  
 次の階層は、Visual Studio のメニュー バーのメニューに関連付けられているサブメニューを示しています。 グループのみがその親メニューを持てないためすべてサブメニュー必要がありますグループからに探索、メニューの代わりに、メニューから直接。 メニューのグループ、およびサブメニュー間のリレーションシップに関する詳細については、次を参照してください。 [メニューのサブメニューの追加](../../extensibility/adding-a-submenu-to-a-menu.md)します。  
  
> [!NOTE]
>  Visual Studio のメニュー バーのメニューの名前がいないとは別に表示されてこの階層にため次のように IDE では、グループの名前付け規則から推論できます: IDG\_VS\_*メニュー名*\_*グループ名*します。  
  
|親グループ|サブメニュー|子グループ|  
|-----------|------------|-----------|  
|IDG\_VS\_FILE\_FILE|IDM\_VS\_CSCD\_NEW|IDG\_VS\_FILE\_NEW\_CASCADE|  
||IDM\_VS\_CSCD\_OPEN|IDG\_VS\_FILE\_OPENP\_CASCADE|  
|||IDG\_VS\_FILE\_OPENF\_CASCADE|  
|IDG\_VS\_FILE\_ADD|IDM\_VS\_CSCD\_ADD|IDG\_VS\_FILE\_ADD\_PROJECT\_NEW|  
|||IDG\_VS\_FILE\_ADD\_PROJECT\_EXI|  
|IDG\_VS\_FILE\_MRU|IDM\_VS\_CSCD\_FILEMRU|IDG\_VS\_FILE\_FMRU\_CASCADE|  
||IDM\_VS\_CSCD\_PROJMRU|IDG\_VS\_FILE\_PMRU\_CASCADE|  
|IDG\_VS\_FILE\_MOVE|IDM\_VS\_CSCD\_MOVETOPRJ|IDG\_VS\_FILE\_MOVE\_CASCADE|  
|||IDG\_VS\_FILE\_MOVE\_PICKER|  
|IDG\_VS\_VIEW\_DEV\_WINDOWS|IDM\_VS\_CSCD\_FINDRESULTS|IDG\_VS\_WNDO\_FINDRESULTS|  
||IDM\_VS\_CSCD\_WINDOWS|IDG\_VS\_VIEW\_CALLBROWSER|  
|||IDG\_VS\_WNDO\_OTRWNDWS1.6|  
|||IDG\_VS\_WNDO\_WINDOWS2|  
|IDG\_VS\_VIEW\_TOOLBARS|IDM\_VS\_CSCD\_COMMANDBARS||  
|IDG\_VS\_EDIT\_GOTO|IDM\_VS\_EDITOR\_FIND\_MENU||  
|IDG\_VS\_EDIT\_OBJECTS|IDM\_VS\_CSCD\_MNUDES|IDG\_VS\_MNUDES\_INSERT|  
|||IDG\_VS\_MNUDES\_EDITNAMES|  
||IDM\_VS\_CSCD\_OLEVERBS|IDG\_VS\_EDIT\_OLEVERBS|  
|IDG\_VS\_BUILD\_SELECTION|IDM\_VS\_CSCD\_BUILD|IDG\_VS\_BUILD\_CASCADE|  
|||IDG\_VS\_BUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_REBUILD|IDG\_VS\_REBUILD\_CASCADE|  
|||IDG\_VS\_REBUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_PROJONLY|IDG\_VS\_PROJONLY\_CASCADE|  
||IDM\_VS\_CSCD\_CLEAN|IDG\_VS\_CLEAN\_CASCADE|  
|||IDG\_VS\_CLEAN\_PROJPICKER|  
||IDM\_VS\_CSCD\_DEPLOY|IDG\_VS\_DEPLOY\_CASCADE|  
|||IDG\_VS\_DEPLOY\_PROJPICKER|  
|IDG\_VS\_PGO\_SELECTION|IDM\_VS\_CSCD\_PGO\_BUILD|IDG\_VS\_PGO\_BUILD\_CASCADE\_BUILD|  
|||IDG\_VS\_PGO\_BUILD\_CASCADE\_RUN|  
  
## 参照  
 [Guid と Visual Studio ツールバーの Id](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [Guid と、Visual Studio コマンドの Id](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)