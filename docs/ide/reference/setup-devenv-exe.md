---
title: devenv.exe の setup スイッチ
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: eca577c0e4646821262c953cf48256937eed386c
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948376"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

/Setup を指定すると Visual Studio は、使用できるすべての VSPackage から、メニュー、ツール バー、コマンド グループが記述されているリソース メタデータを強制的にマージします。

## <a name="syntax"></a>構文

```shell
devenv /setup
```

## <a name="remarks"></a>コメント

このスイッチは引数を取りません。 `devenv /setup` コマンドは、一般的にインストール処理の最後の手順として提示されます。 `/setup` スイッチを使っても、Visual Studio は起動しません。

> [!NOTE]
> `/setup` スイッチを使用するには、管理者として `devenv` を実行する必要があります。

## <a name="example"></a>例

この例は、VSPackage が含まれるバージョンの Visual Studio のインストールの最後の手順を示しています。

```shell
devenv /setup
```

## <a name="see-also"></a>関連項目

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)