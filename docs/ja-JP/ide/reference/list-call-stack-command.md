---
title: ListCallStack コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e5fb8bd8b0f0f550e6fa1253f778895af0472be
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="list-call-stack-command"></a>ListCallStack コマンド
現在の呼び出し履歴を表示します。

## <a name="syntax"></a>構文

```
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>引数
 `index` 省略可能。 現在のスタック フレームを設定し、出力は表示しません。

## <a name="switches"></a>スイッチ
 各スイッチは、完全な形式または短い形式を使用して、呼び出すことができます。

 /Count:`number` または /C:`number`

 任意。 表示する呼び出し履歴の最大数。 既定値は無制限です。

 /ShowTypes:`yes`&#124;`no` または /T:`yes`&#124;`no`

 任意。 パラメーターの型を表示するかどうかを指定します。 既定値は `yes`にする必要があります。

 /ShowNames:`yes`&#124;`no` または /N:`yes`&#124;`no`

 任意。 パラメーターの名前を表示するかどうかを指定します。 既定値は `yes`にする必要があります。

 /ShowValues:`yes`&#124;`no` または /V:`yes`&#124;`no`

 任意。 パラメーターの値を表示するかどうかを指定します。 既定値は `yes`にする必要があります。

 /ShowModule:`yes`&#124;`no` または /M:`yes`&#124;`no`

 任意。 モジュールの名前を表示するかどうかを指定します。 既定値は `yes`にする必要があります。

 /ShowLineOffset:`yes`&#124;`no` または /#:`yes`&#124;`no`

 任意。 行オフセットを表示するかどうかを指定します。 既定値は `no`にする必要があります。

 /ShowByteOffset:`yes`&#124;`no` または /B:`yes`&#124;`no`

 任意。 バイト オフセットを表示するかどうかを指定します。 既定値は `no`にする必要があります。

 /ShowLanguage:`yes`&#124;`no` または /L:`yes`&#124;`no`

 任意。 言語を表示するかどうかを指定します。 既定値は `no`にする必要があります。

 /IncludeCallsAcrossThreads:`yes`&#124;`no` または /I:`yes`&#124;`no`

 任意。 他のスレッドとの間の呼び出しを含めるかどうかを指定します。 既定値は `no`にする必要があります。

 /ShowExternalCode:`yes`&#124;`no`

 任意。 呼び出し履歴で [マイ コードのみ] を表示するかどうかを指定します。 [マイ コードのみ] がオフの場合は、すべての非ユーザー コードが表示されます。 [マイ コードのみ] がオンの場合、非ユーザー コードは呼び出し履歴の出力で `[external]` として表示されます。

 Thread:`n`

 任意。 スレッド `n` の呼び出し履歴を表示します。 スレッドが指定されていない場合、現在のスレッドの呼び出し履歴が表示されます。

## <a name="remarks"></a>コメント
 引数やスイッチに加えられた変更は、以降のコマンドの呼び出しに適用されます。 Debug.ListCallStackby を単独で実行すると、呼び出し履歴全体が表示されます。 たとえば、次のようなインデックスを指定します。

```
Debug.ListCallStack 2
```

 この場合、現在のスタック フレームは対象のフレーム (この例では、2 つ目のフレーム) に設定されます。

 このコマンドは、定義済みのエイリアス kb を使用して記述することもできます。 たとえば、次のように入力できます。

```
kb 2
```

 この場合、現在のスタック フレームが 2 つ目のフレームに設定されます。

## <a name="example"></a>例

```
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>参照

- [ListDisassembly コマンド](../../ide/reference/list-disassembly-command.md)
- [ListThreads コマンド](../../ide/reference/list-threads-command.md)
- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)