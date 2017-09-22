---
title: "外部ツールの管理 | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 1d273749cc41eb975dc9f93329edf9a57aaae09a
ms.contentlocale: ja-jp
ms.lasthandoff: 05/24/2017

---
# <a name="manage-external-tools"></a>外部ツールの管理
Visual Studio から **[ツール]** メニューを使用して外部ツールを呼び出すことができます。 いくつかの既定ツールは **[ツール]** メニューで使用できますが、他の実行可能ファイルを独自に追加することもできます。  

## <a name="tools-available-on-the-visual-studio-tools-menu"></a>[Visual Studio ツール] メニューで使用できるツール
 **[ツール]** メニューには、次のように組み込みコマンドがいくつか表示されます。

*  [Visual Studio 拡張機能を管理する](finding-and-using-visual-studio-extensions.md) **[拡張機能と更新プログラム]**
*  [コード スニペットを整理する](code-snippets.md#code-snippet-manager) **[コード スニペット マネージャー]**
*  [Dotfuscator Community Edition (CE)](dotfuscator/index.md) が[インストール](dotfuscator/install.md)されている場合に起動する **[PreEmptive Protection - Dotfuscator]**
*  [メニューとツールバーをカスタマイズする](how-to-customize-menus-and-toolbars-in-visual-studio.md) **[カスタマイズ]**
*  [Visual Studio IDE と他のツールの多様なオプションを設定する](reference/options-dialog-box-visual-studio.md) **[オプション]**

## <a name="add-new-tools-to-the-tools-menu"></a>[ツール] メニューに新しいツールを追加する 
 **[ツール]** メニューに外部ツールを追加することができます。 **[外部ツール]** ダイアログ ボックスを開き、**[追加]** をクリックして、情報を入力します。 たとえば、次のエントリを指定すると、Visual Studio で現在開いているファイルのディレクトリでエクスプローラーが開きます。  
  
1.  タイトル: *開いているファイルの場所*
  
2.  コマンド: `explorer.exe`  
  
3.  引数: `/root, "$(ItemDir)"`  
  
 外部ツールの定義時に使用できる引数の一覧を次に示します。
  
> [!NOTE]
>  IDE のステータス バーに、アクティブなコード エディターの挿入位置を示す、Current Line 変数および Current Column 変数が表示されます。 Current Text 変数は、その場所で選択されているテキストまたはコードを返します。  
  
|名前|引数|説明|  
|----------|--------------|-----------------|  
|項目のパス|$(ItemPath)|現在のファイルの完全なファイル名 (ドライブ + パス + ファイル名)。|  
|項目のディレクトリ|$(ItemDir)|現在のファイルのディレクトリ (ドライブ + パス)。|  
|項目のファイル名|$(ItemFilename)|現在のファイルのファイル名 (ファイル名)。|  
|項目の拡張子|$(ItemExt)|現在のファイルのファイル名拡張子。|  
|カレント行|$(CurLine)|コード ウィンドウ内のカーソルの現在の行位置。|  
|カレント列|$(CurCol)|コード ウィンドウ内のカーソルの現在の列位置。|  
|カレント テキスト|$(CurText)|選択されているテキスト。|  
|ターゲット パス|$(TargetPath)|作成するアイテムの完全なファイル名 (ドライブ + パス + ファイル名)。|  
|ターゲット ディレクトリ|$(TargetDir)|作成するアイテムのディレクトリ。|  
|ターゲット名|$(TargetName)|作成するアイテムのファイル名。|  
|ターゲットの拡張子|$(TargetExt)|作成するアイテムのファイル名拡張子。|  
|バイナリ ディレクトリ|$(BinDir)|作成中のバイナリの最終的な場所 (ドライブ + パスとして定義されます)。 例: **\\...\My Documents\Visual Studio \<Version>\\<ProjectName\>\bin\debug**|  
|プロジェクト ディレクトリ|$(ProjDir)|現在のプロジェクトのディレクトリ (ドライブ + パス)。|  
|プロジェクト ファイル名|$(ProjFileName)|現在のプロジェクトのファイル名 (ドライブ + パス + ファイル名)。|  
|ソリューション ディレクトリ|$(SolutionDir)|現在のソリューションのディレクトリ (ドライブ + パス)。|  
|ソリューション ファイル名|$(SolutionFileName)|現在のソリューションのファイル名 (ドライブ + パス + ファイル名)。|  

## <a name="see-also"></a>関連項目  
 [C と C++ のビルド ツール](/cpp/build/reference/c-cpp-build-tools)

