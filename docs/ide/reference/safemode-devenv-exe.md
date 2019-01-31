---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b794c80768990a3abac85d3ea3b93699f3b220dd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970436"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Visual Studio をセーフ モードで起動し、既定の環境とサービスのみを読み込みます。

## <a name="syntax"></a>構文

```shell
devenv /SafeMode
```

## <a name="remarks"></a>コメント

このスイッチでは、Visual Studio が起動したときに、すべてのサード パーティ VSPackage を読み込まないようにするため、実行が安定したものになります。

## <a name="example"></a>例

次の例では、Visual Studio をセーフ モードで起動します。

```shell
devenv /safemode
```

## <a name="see-also"></a>関連項目

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)