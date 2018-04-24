---
title: 外部ツールの管理 | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea718d2170d058897db4bfa7a9a2cfc32da563a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="manage-external-tools"></a>外部ツールの管理

Visual Studio から **[ツール]** メニューを使用して外部ツールを呼び出すことができます。 **[ツール]** メニューではいくつかのツールを既定で使用できますが、このメニューは他の独自の実行可能ファイルを追加してカスタマイズできます。

## <a name="tools-available-on-the-tools-menu"></a>[ツール] メニューで使用できるツール

**[ツール]** メニューには、次のように組み込みコマンドがいくつか表示されます。

* [Visual Studio 拡張機能を管理する](finding-and-using-visual-studio-extensions.md) **[拡張機能と更新プログラム]**
* [コード スニペットを整理する](code-snippets.md) **[コード スニペット マネージャー]**
* [Dotfuscator Community Edition (CE)](dotfuscator/index.md) が[インストール](dotfuscator/install.md)されている場合に起動する **[PreEmptive Protection - Dotfuscator]**
* [メニューとツールバーをカスタマイズする](how-to-customize-menus-and-toolbars-in-visual-studio.md) **[カスタマイズ]**
* [Visual Studio IDE と他のツールの多様なオプションを設定する](reference/options-dialog-box-visual-studio.md) **[オプション]**

## <a name="add-new-tools-to-the-tools-menu"></a>[ツール] メニューに新しいツールを追加する

**[ツール]** メニューに表示する外部ツールを追加できます。

1. **[ツール]** > **[外部ツール]** の順に選んで、**[外部ツール]** ダイアログ ボックスを開きます。

1. **[追加]** をクリックして情報を入力します。 たとえば、次のエントリを指定すると、Visual Studio で現在開いているファイルのディレクトリでエクスプローラーが開きます。

   * タイトル: `Open File Location`

   * コマンド: `explorer.exe`

   * 引数: `/root, "$(ItemDir)"`

   ![[外部ツール] ダイアログ ボックス](media/external-tools-dialog.png)

外部ツールの定義時に使用できる引数の一覧を次に示します。

|name|引数|説明|  
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
|バイナリ ディレクトリ|$(BinDir)|作成中のバイナリの最終的な場所 (ドライブ + パスとして定義されます)。|  
|プロジェクト ディレクトリ|$(ProjDir)|現在のプロジェクトのディレクトリ (ドライブ + パス)。|  
|プロジェクト ファイル名|$(ProjFileName)|現在のプロジェクトのファイル名 (ドライブ + パス + ファイル名)。|  
|ソリューション ディレクトリ|$(SolutionDir)|現在のソリューションのディレクトリ (ドライブ + パス)。|  
|ソリューション ファイル名|$(SolutionFileName)|現在のソリューションのファイル名 (ドライブ + パス + ファイル名)。|

> [!NOTE]
> IDE のステータス バーに、アクティブなコード エディターの挿入位置を示す、Current Line 変数および Current Column 変数が表示されます。 Current Text 変数は、その場所で選択されているテキストまたはコードを返します。

## <a name="see-also"></a>関連項目

[C と C++ のビルド ツール](/cpp/build/reference/c-cpp-build-tools)
