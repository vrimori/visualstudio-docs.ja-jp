---
title: エラー :SQL できます&#39;t が SSDEBUGPS を見つける |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b4bd8ed846ab4f3d461a29f152db0b83232ec8e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972249"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>エラー :SQL できます&#39;t が SSDEBUGPS を見つける

SSDEBUGPS.dll は、SQL Server のデバッグ ホスト コンポーネントです。

このエラーはデバッグの開始時に発生し、指定されたファイルが [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] コンピューターに存在しないことを示します。 リモート デバッグのセットアップが実行されていない、または何らかの理由でこのファイルが削除されていることが原因として考えられます。

このエラーの解決方法は 2 つあります。1 つは、リモート デバッグのセットアップを再実行する方法です。もう 1 つは、このファイルを [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] コンピューターにコピーする方法です。

リモート デバッグのセットアップを再実行する」の手順に従います[リモート デバッグ](../debugger/remote-debugging.md)します。

ssdebugps.dll のファイルを見つけることができる場合は、これを [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] コンピューターにコピーします。 このファイルが存在する場合は、\Program Files\ Common Files\Microsoft Shared\SQL Debugging にあります。 別のあります[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]コンピューターや Visual Studio 2005 がインストールされているコンピューター。

SSDEBUGPS.dll を SQL Server 2005 コンピューターにコピーするには: 

1. [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] コンピューターの上記の名前とパスを持つディレクトリにファイルをコピーします。

2. **コマンド プロンプト**を開き、次のコマンドを実行してファイルを登録します。

    ```cmd
    regsvr32 ssdebugps.dll
    ```
