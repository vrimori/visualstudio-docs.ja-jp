---
title: Symbol Path コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3debe7c0a193cc0dc2c07875ebb32ac45a7741fb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949260"
---
# <a name="symbol-path-command"></a>Symbol Path コマンド
デバッガーによってシンボルが検索されるディレクトリの一覧を設定します。

## <a name="syntax"></a>構文

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>引数
 `pathname`

 任意。 デバッガーによってシンボルが検索されるパスを、セミコロンで区切った一覧です。

## <a name="remarks"></a>コメント
 `pathname` を指定しない場合、シンボル用の現在のパスがコマンドによって一覧表示されます。

## <a name="example"></a>例
 次の例では、シンボル ディレクトリの一覧に 2 つのパスを追加します。

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>例
 次の例では、シンボル用の現在のパスをセミコロンで区切った一覧が表示されます。

```
Debug.SymbolPath
```

## <a name="see-also"></a>「

- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)