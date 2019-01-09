---
title: -DebugExe (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 99f256b47125f4e07ca5dc148c4351871389a94b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889411"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
指定したデバッグ対象の実行可能ファイルを開きます。

## <a name="syntax"></a>構文

```cmd
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>引数
 `ExecutableFile`

 必須です。 .exe ファイルのパスとファイル名。

 .exe ファイルが見つからない場合、または存在しない場合、警告やエラーは表示されず、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は通常どおり起動します。

## <a name="remarks"></a>コメント
 `ExecutableFile` パラメーターに続くどの文字列もそのファイルに引数として渡されます。

## <a name="example"></a>例
 次の例では、デバッグするために `MyApplication.exe` ファイルを開きます。

```cmd
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>「

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)