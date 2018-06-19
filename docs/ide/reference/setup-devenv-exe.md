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
ms.openlocfilehash: 0f3d78ebb63434df38735bdf24e9d4fcba8f172c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942950"
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

- [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)