---
title: SetCurrentProcess
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
ms.openlocfilehash: 64561db59cc089d9539ab396cf4e869e92fe1117
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705087"
---
# <a name="set-current-process"></a>SetCurrentProcess
指定されたプロセスをデバッガーでアクティブなプロセスとして設定します。

## <a name="syntax"></a>構文

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>引数
 `index`

 必須。 プロセスのインデックスです。

## <a name="remarks"></a>コメント
 デバッグ中には複数のプロセスにアタッチできますが、デバッガーでアクティブになっているプロセスは常に 1 つだけです。 `SetCurrentProcess` コマンドを使用すると、アクティブなプロセスを設定できます。

## <a name="example"></a>例

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>参照

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)