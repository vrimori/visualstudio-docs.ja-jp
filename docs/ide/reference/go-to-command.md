---
title: GoTo コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e583ee3bcb764d09bed9907710454dd6c39c6b8d
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704279"
---
# <a name="go-to-command"></a>GoTo コマンド
指定した行にカーソルを移動します。

## <a name="syntax"></a>構文

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>引数
 `linenumber`

 任意。 移動先の行番号を表す整数。

## <a name="remarks"></a>コメント
 行番号は 1 から始まります。 `linenumber` の値が 1 未満の場合は、最初の行が表示されます。 `linenumber` の値が最終行の値より大きい場合は、最後の行が表示されます。

 `linenumber` の値が指定されていない場合は、**[指定行へ移動]** ダイアログ ボックスが表示されます。

 このコマンドのエイリアスは GoToLn です。

## <a name="example"></a>例

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>参照

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)