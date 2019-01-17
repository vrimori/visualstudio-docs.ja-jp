---
title: SetCurrentProcess
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c01c399dc76d1b328443edef27edd9a921b1b9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855284"
---
# <a name="set-current-process"></a>SetCurrentProcess
指定されたプロセスをデバッガーでアクティブなプロセスとして設定します。

## <a name="syntax"></a>構文

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>引数
 `index`

 必須です。 プロセスのインデックスです。

## <a name="remarks"></a>コメント
 デバッグ中には複数のプロセスにアタッチできますが、デバッガーでアクティブになっているプロセスは常に 1 つだけです。 `SetCurrentProcess` コマンドを使用すると、アクティブなプロセスを設定できます。

## <a name="example"></a>例

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>「

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)