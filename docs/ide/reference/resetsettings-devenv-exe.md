---
title: -ResetSettings (devenv.exe)
ms.date: 11/16/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 160cbf93cee8ff778a4f84ee833c7fac3d7f26b1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830665"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Visual Studio の既定の設定を復元し、Visual Studio IDE を自動的に起動します。 指定の *vssettings* ファイルに準じた設定にリセットすることもできます。

既定の設定は、Visual Studio の初回起動時に選択したプロファイルによって決定されます。

> [!TIP]
> 統合開発環境 (IDE) を使用して設定をリセットする方法については、「[リセット設定](../environment-settings.md#reset-settings)」を参照してください。

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

## <a name="see-also"></a>関連項目

- [環境設定](../environment-settings.md)
- [Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)