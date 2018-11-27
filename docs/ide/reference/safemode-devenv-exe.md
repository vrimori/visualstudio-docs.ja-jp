---
title: -SafeMode (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6df78ec4be1fc94951634b84a98e80dc1403a41b
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948739"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] をセーフ モードで起動し、既定の環境とサービスのみを読み込みます。

## <a name="syntax"></a>構文

```cmd
devenv /SafeMode
```

## <a name="remarks"></a>コメント
 このスイッチでは、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] が起動したときに、すべてのサード パーティ VSPackage を読み込まないようにするため、実行が安定したものになります。

## <a name="description"></a>説明
 次の例では、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] をセーフ モードで起動します。

## <a name="code"></a>コード

```cmd
Devenv.exe /SafeMode
```

## <a name="see-also"></a>参照

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)