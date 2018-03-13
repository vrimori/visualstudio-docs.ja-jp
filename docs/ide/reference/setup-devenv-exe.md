---
title: "devenv.exe の setup スイッチ | Microsoft Docs"
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e37fe50eefc36e7b5396f396d2b614851a0bd9cb
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
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

[Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)