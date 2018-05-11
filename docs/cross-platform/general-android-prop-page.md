---
title: 一般的なプロジェクト プロパティ (Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 6e4f7da0c8d1727446c23ad25db2bf64228cbc9a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="general-project-properties-android-c"></a>一般的なプロジェクト プロパティ (Android C++)

プロパティ | 説明 | オプション
--- | ---| ---
出力ディレクトリ | 出力ファイル ディレクトリへの相対パスを指定します。環境変数を含めることができます。
中間ディレクトリ | 中間ファイル ディレクトリへの相対パスを指定します。環境変数を含めることができます。
ターゲット名 | このプロジェクトにより生成されるファイル名を指定します。
ターゲットの拡張子 | このプロジェクトにより生成されるファイル拡張子を指定します。 (例: .exe または .dll)
消去時に削除する拡張子 | クリーンまたはリビルドの実行時に中間ディレクトリから削除するファイルをセミコロンで区切って指定します。ワイルドカードを指定できます。
ビルド ログ ファイル | ビルドのログが有効になっている場合、書き込むビルド ログ ファイルを指定します。
プラットフォームのツールセット | 現在の構成の作成に使用するツールセットを指定します。設定しない場合は、既定のツールセットが使用されます。
構成の種類 | この構成が生成する出力の種類を指定します。 | **ダイナミック ライブラリ (.so)** - ダイナミック ライブラリ (.so)<br>**スタティック ライブラリ (.a)** - スタティック ライブラリ (.a)<br>**ユーティリティ** - ユーティリティ<br>**メイクファイル** - メイクファイル<br>
ターゲット API レベル | この構成が対象としている Android NDK API レベルです。
STL の使用 | この構成で使用する C++ 標準ライブラリを指定します。 | **最小 C++ ランタイム ライブラリ (system)**<br>**C++ ランタイム スタティック ライブラリ (gabi++_static)**<br>**C++ ランタイム共有ライブラリ (gabi++_shared)**<br>**STLport ランタイム スタティック ライブラリ (stlport_static)**<br>**STLport ランタイム共有ライブラリ (stlport_shared)**<br>**GNU STL スタティック ライブラリ (gnustl_static)**<br>**GNU STL 共有ライブラリ (gnustl_shared)**<br>**LLVM libc++ スタティック ライブラリ (c++_static)**<br>**LLVM libc++ 共有ライブラリ (c++_shared)**<br>
Thumb モード | Thumb マイクロアーキテクチャを実行するコードを生成します。 これは、arm アーキテクチャにのみ適用されます。 | **Thumb**<br>**Arm**<br>**無効**<br>
