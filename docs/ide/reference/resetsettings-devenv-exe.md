---
title: -ResetSettings (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c3d3a6ef558b510cfde716716daf97a549fbba4
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Visual Studio の既定の設定を復元し、Visual Studio IDE を自動的に起動します。 指定の *vssettings* ファイルに準じた設定にリセットすることもできます。

既定の設定は、Visual Studio の初回起動時に選択したプロファイルによって決定されます。

## <a name="syntax"></a>構文

```cmd
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>引数

`SettingsFile`

Visual Studio に適用する *vssettings* ファイルの完全パスとファイル名です。

全般的な開発設定のプロファイルを復元するには、`General` を使用します。

## <a name="remarks"></a>コメント

`SettingsFile` が指定されていない場合、次回 Visual Studio を起動したときに、既定の設定のコレクションを選択するよう要求されます。

## <a name="example"></a>例

`MySettings.vssettings` ファイルに保存された設定を適用するコマンド ラインを次に示します。

```cmd
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>参照

- [Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)