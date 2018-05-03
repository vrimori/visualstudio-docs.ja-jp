---
title: Alias コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e72c848ff9a0234040e60391be8baa05e23791a5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="alias-command"></a>Alias コマンド
完全なコマンド、完全なコマンドと引数、または他のエイリアスに対して新しいエイリアスを作成します。

> [!TIP]
> 引数を指定せずに「`>alias`」と入力すると、現在のエイリアスとその定義が一覧表示されます。


## <a name="syntax"></a>構文

```
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>引数
 `aliasname` 省略可能。 新しいエイリアスの名前。 `aliasname` の値を指定しない場合は、現在のエイリアス一覧とその定義が表示されます。

 `aliasstring` 省略可能。 完全なコマンド名または既存のエイリアスと、エイリアスとして作成する任意のパラメーター。 `aliasstring` の値を指定しない場合は、指定したエイリアスの名前と文字列が表示されます。

## <a name="switches"></a>スイッチ
 /delete または /del または /d 省略可能。 指定したエイリアスを削除し、オート コンプリートから除外します。

 /reset 省略可能。 定義済みエイリアスの一覧を元の設定に戻します。 つまり、定義済みエイリアスをすべて復元し、ユーザー定義のエイリアスをすべて削除します。

## <a name="remarks"></a>コメント
 エイリアスはコマンドを表すため、コマンド ラインの先頭に指定する必要があります。

 このコマンドを実行するときは、エイリアスの後ではなく、コマンドの直後にスイッチを置く必要があります。そうしないと、スイッチ自体がエイリアスの文字列の一部として取り込まれます。

 `/reset` スイッチを指定すると、エイリアスを復元する前に確認メッセージが表示されます。 `/reset` には省略形はありません。

## <a name="examples"></a>使用例
 次の例では、Edit.MakeUpperCase という完全なコマンドに対し、`upper` という新しいエイリアスを作成します。

```
>Tools.Alias upper Edit.MakeUpperCase
```

 エイリアス `upper` を削除するコードは次のとおりです。

```
>Tools.alias /delete upper
```

 現在のすべてのエイリアスの一覧とその定義を表示するコードは次のとおりです。

```
>Tools.Alias
```

## <a name="see-also"></a>参照

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)