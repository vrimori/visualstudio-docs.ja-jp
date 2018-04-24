---
title: 一般的なプロジェクト プロパティ (Android C++ メイクファイル) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.ConfigurationType
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: cfc1655adbd9377f1aeeec60afc799f342b4498d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="general-project-properties-android-c-makefile"></a>一般的なプロジェクト プロパティ (Android C++ メイクファイル)

プロパティ | 説明 | オプション
--- | ---| ---
出力ディレクトリ | 出力ファイル ディレクトリへの相対パスを指定します。環境変数を含めることができます。
中間ディレクトリ | 中間ファイル ディレクトリへの相対パスを指定します。環境変数を含めることができます。
ビルド ログ ファイル | ビルドのログが有効になっている場合、書き込むビルド ログ ファイルを指定します。
構成の種類 | この構成が生成する出力の種類を指定します。 | **ダイナミック ライブラリ (.so)** - ダイナミック ライブラリ (.so)<br>**スタティック ライブラリ (.a)** - スタティック ライブラリ (.a)<br>**ユーティリティ** - ユーティリティ<br>**メイクファイル** - メイクファイル<br>
