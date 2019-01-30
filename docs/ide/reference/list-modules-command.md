---
title: List Modules コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9bf23375f4be979c8cd5ea5dd44913746840ce6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972889"
---
# <a name="list-modules-command"></a>List Modules コマンド
現在のプロセスのモジュールが一覧表示されます。

## <a name="syntax"></a>構文

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>パラメーター
 /Address:`yes|no`

 任意。 モジュールのメモリ アドレスを表示するかどうかを指定します。 既定値は `yes`にする必要があります。

 /Name:`yes|no`

 任意。 モジュールの名前を表示するかどうかを指定します。 既定値は `yes`にする必要があります。

 /Order:`yes|no`

 任意。 モジュールの順序を表示するかどうかを指定します。 既定値は `no`にする必要があります。

 /Path:`yes|no`

 任意。 モジュールのパスを表示するかどうかを指定します。 既定値は `yes`にする必要があります。

 /Process:`yes|no`

 任意。 モジュールのプロセスを表示するかどうかを指定します。 既定値は `no`にする必要があります。

 /SymbolFile:`yes|no`

 任意。 モジュールのシンボル ファイルを表示するかどうかを指定します。 既定値は `no`にする必要があります。

 /SymbolStatus:`yes|no`

 任意。 モジュールのシンボル ステータスを表示するかどうかを指定します。 既定値は `yes`にする必要があります。

 /Timestamp:`yes|no`

 任意。 モジュールのタイムスタンプを表示するかどうかを指定します。 既定値は `no`にする必要があります。

 /Version:`yes|no`

 任意。 モジュールのバージョンを表示するかどうかを指定します。 既定値は `no`にする必要があります。

## <a name="example"></a>例
 次の例では、現在のプロセスのモジュール名、アドレス、およびタイムスタンプを一覧表示します。

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>「

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [方法: [モジュール] ウィンドウを使用する](../../debugger/how-to-use-the-modules-window.md)