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
ms.openlocfilehash: eaf137b699b7a02a0ee79099e937767262fce4e9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] をセーフ モードで起動し、既定の環境とサービスのみを読み込みます。

## <a name="syntax"></a>構文

```
devenv /SafeMode
```

## <a name="remarks"></a>コメント
 このスイッチでは、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] が起動したときに、すべてのサード パーティ VSPackage を読み込まないようにするため、実行が安定したものになります。

## <a name="description"></a>説明
 次の例では、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] をセーフ モードで起動します。

## <a name="code"></a>コード

```
Devenv.exe /SafeMode
```

## <a name="see-also"></a>参照

- [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)