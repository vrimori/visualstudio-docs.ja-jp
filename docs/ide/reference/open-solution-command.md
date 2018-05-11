---
title: OpenSolution コマンド
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 576146e8bcbc20babff10f2a55d561f532a80723
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="open-solution-command"></a>OpenSolution コマンド
開いている他のソリューションを閉じ、既存のソリューションを開きます。

## <a name="syntax"></a>構文

```cmd
File.OpenSolution filename
```

## <a name="arguments"></a>引数
 `Filename`

 必須。 開くソリューションの完全パスとファイル名。

 `filename` 引数の構文の場合、空白を含むパスで引用符を使用する必要があります。

## <a name="remarks"></a>コメント
 オート コンプリートでは、入力された正しいパスとファイル名の検索を試みます。

## <a name="example"></a>例
 この例では、Test1.sln というソリューションを開きます。

```cmd
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"
```

## <a name="see-also"></a>参照

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)