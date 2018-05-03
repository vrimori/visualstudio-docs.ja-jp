---
title: -DebugExe (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 065648588b51ad6c71ae1a10235da4f096470abe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
指定したデバッグ対象の実行可能ファイルを開きます。

## <a name="syntax"></a>構文

```
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>引数
 `ExecutableFile`

 必須。 .exe ファイルのパスとファイル名。

 .exe ファイルが見つからない場合、または存在しない場合、警告やエラーは表示されず、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は通常どおり起動します。

## <a name="remarks"></a>コメント
 `ExecutableFile` パラメーターに続くどの文字列もそのファイルに引数として渡されます。

## <a name="example"></a>例
 次の例では、デバッグするために `MyApplication.exe` ファイルを開きます。

```
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>参照

- [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)