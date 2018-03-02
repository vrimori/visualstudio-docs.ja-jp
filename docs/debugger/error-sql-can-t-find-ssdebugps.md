---
title: "エラー: SQL できます &#39; t 検索 SSDEBUGPS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
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
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 69a82222fe1a4a2cd643f9f84127c3674f8078fd
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="error-sql-can39t-find-ssdebugps"></a>T 検索 SSDEBUGPS SQL できます &#39; エラー:

SSDEBUGPS.dll は、SQL Server のデバッグ ホスト コンポーネントです。

このエラーはデバッグの開始時に発生し、指定されたファイルが [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] コンピューターに存在しないことを示します。 リモート デバッグのセットアップが実行されていない、または何らかの理由でこのファイルが削除されていることが原因として考えられます。

このエラーを解決するのには 2 つの方法: リモート デバッグのセットアップを再実行して、ファイルをコピーして、[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]マシンです。

リモート デバッグのセットアップを再実行する手順についてで[リモート デバッグ](../debugger/remote-debugging.md)です。

Ssdebugps.dll のコピーを見つけるには場合、は、上にそれをコピー、[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]マシンです。 このファイルが存在する場合は、\Program Files\ Common Files\Microsoft Shared\SQL Debugging にあります。 した方が別の[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]コンピューターや Visual Studio 2005 がインストールされているコンピューターでします。

SSDEBUGPS.dll を SQL Server 2005 のコンピューターにコピー。

1. 同じ名前とパスがディレクトリにファイルをコピー、[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]マシンです。

2. 開くことで登録、**コマンド プロンプト**と、次のコマンドを実行します。

    ```
    regsrv32 ssdebugps.dll
    ```