---
title: -UseEnv (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4c48e9f22322cd5ebebeff0d987c32d369f98d03
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Visual Studio を起動し、**[VC++ ディレクトリ]** ダイアログ ボックスに環境変数を読み込みます。

> [!NOTE]
> このスイッチは、**C++ によるデスクトップ開発**ワークロードと共にインストールされます。

## <a name="syntax"></a>構文

```shell
Devenv /useenv
```

## <a name="example"></a>例

Visual Studio を起動し、**[VC++ ディレクトリ]** ダイアログ ボックスに環境変数を読み込む例を以下に示します。

```shell
Devenv.exe /useenv
```

## <a name="see-also"></a>関連項目

* [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)