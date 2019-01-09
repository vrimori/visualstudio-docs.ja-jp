---
title: -UseEnv (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b597eae42eb36c8d034ca9a4038b6823c1121349
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846335"
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

* [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)