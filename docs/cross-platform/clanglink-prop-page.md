---
title: "Clang のリンカーのプロパティ (Android C++) | Microsoft Docs"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.IncrementalLink
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
- VC.Project.VCLinkerTool.LibraryDependencies
ms.workload: xplat-cplusplus
ms.openlocfilehash: f74ad5934d48c941195da30d9228c35483479f69
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="clang-linker-properties-android-c"></a>Clang のリンカーのプロパティ (Android C++)

プロパティ | 説明 | オプション
--- | ---| ---
出力ファイル | このオプションは、リンカーによって作成されるプログラムの既定の名前と場所をオーバーライドします。 (-o)
進行状況の表示 | リンカーの進行状況メッセージを出力します。
Version | -version オプションは、実行ファイルのヘッダーにバージョン番号を付けるようにリンカーを設定します。
詳細出力の有効にする | -verbose オプションは、デバッグ用に詳細メッセージを出力するようにリンカーを設定します。
インクリメンタル リンクを有効にする | このオプションは、インクリメンタル リンクを有効にするようにリンカーを設定します。
共有ライブラリの検索パス | 共有ライブラリの検索パスをユーザーが設定できるようにします。
追加のライブラリ ディレクトリ | 環境のライブラリ パスをユーザーがオーバーライドできるようにします。 (-L フォルダー)。
未解決のシンボル参照の報告 | このオプションを有効にすると未解決のシンボル参照が報告されます。
メモリ使用量の最適化 | 必要に応じてシンボル テーブルを再度読み取ることでメモリの使用量を最適化します。
特定の既定のライブラリの無視 | 無視する既定のライブラリの名前を 1 つ以上指定します。
シンボル参照の強制 | 出力ファイルに未定義のシンボルとしてシンボルを入力するように強制します。
デバッガー シンボル情報 | 出力ファイルのデバッガー シンボル情報。 | **すべて含む**<br>**再配置処理に不要なシンボルを除外**<br>**デバッガー シンボル情報のみを除外**<br>**すべてのシンボル情報を除外**<br>
デバッガー シンボル情報のパッケージ化 | パッケージ化の前にデバッガー シンボル情報を削除してください。  元のバイナリのコピーがデバッグに使用されます。
マップ ファイル名 | マップ オプションは、ユーザーが指定した名前を使用してマップ ファイルを作成するようにリンカーを設定します。
再配置後に変数を読み取り専用としてマーク | このオプションは、再配置後に変数を読み取り専用としてマークします。
即時関数バインディングの有効化 | このオプションは、即時関数バインディング用にオブジェクトをマークします。
実行可能スタックの要求 | このオプションは、実行可能スタックを必要としないものとして出力をマークします。
アーカイブ全体 | アーカイブ全体は、ソースおよびその他の依存関係のすべてのコードを使用します。
その他のオプション | その他のオプションです。
追加の依存ファイル | リンク コマンド ラインに追加する項目を指定します。
ライブラリの依存ファイル | このオプションでは、リンカー コマンド ラインに追加する追加ライブラリを指定できます。 追加ライブラリは、"lib" で始まって拡張子 ".a" または ".so" で終わり、リンカー コマンド ラインの最後に追加されます。  (-lFILE)
