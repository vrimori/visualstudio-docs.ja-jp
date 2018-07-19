---
title: 'エラー: SQL できます&#39;t が SSDEBUGPS を見つける |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1498a287bdb474751dfaa5b4b23c30bc302544e7
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058257"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>エラー: SQL できます&#39;t が SSDEBUGPS を見つける

SSDEBUGPS.dll は、SQL Server のデバッグ ホスト コンポーネントです。

このエラーはデバッグの開始時に発生し、指定されたファイルが [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] コンピューターに存在しないことを示します。 リモート デバッグのセットアップが実行されていない、または何らかの理由でこのファイルが削除されていることが原因として考えられます。

このエラーを解決するのには 2 つの方法: リモート デバッグのセットアップを再実行し、ファイルをコピーして、[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]マシン。

リモート デバッグのセットアップを再実行する」の手順に従います[リモート デバッグ](../debugger/remote-debugging.md)します。

Ssdebugps.dll のファイルのコピーを見つけるには場合に、コピーできます、[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]マシン。 このファイルが存在する場合は、\Program Files\ Common Files\Microsoft Shared\SQL Debugging にあります。 別のあります[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]コンピューターや Visual Studio 2005 がインストールされているコンピューター。

SSDEBUGPS.dll を SQL Server 2005 コンピューターにコピー。

1. ファイルを同じ名前とパスを使用してディレクトリにコピー、[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]マシン。

2. 登録を開いて、**コマンド プロンプト**、次のコマンドを実行しています。

    ```cmd
    regsrv32 ssdebugps.dll
    ```
