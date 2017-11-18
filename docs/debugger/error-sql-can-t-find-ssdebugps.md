---
title: "エラー: SQL できます &#39; t 検索 SSDEBUGPS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43a437cfc4be1c9168b16e4b9d1a46e2eadcb2e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="error-sql-can39t-find-ssdebugps"></a>T 検索 SSDEBUGPS SQL できます &#39; エラー:
SSDEBUGPS.dll は、SQL Server のデバッグ ホスト コンポーネントです。  
  
 このエラーはデバッグの開始時に発生し、指定されたファイルが [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] コンピューターに存在しないことを示します。 リモート デバッグのセットアップが実行されていない、または何らかの理由でこのファイルが削除されていることが原因として考えられます。  
  
 このエラーを解決するのには 2 つの方法: リモート デバッグのセットアップを再実行して、ファイルをコピーして、[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]マシンです。  
  
 リモート デバッグのセットアップを再実行する手順についてで[リモート デバッグ](../debugger/remote-debugging.md)です。  
  
 Ssdebugps.dll のコピーを見つけるには場合、は、上にそれをコピー、[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]マシンです。 このファイルが存在する場合は、\Program Files\ Common Files\Microsoft Shared\SQL Debugging にあります。 した方が別の[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]コンピューターやがあるマシン[!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)]をインストールします。  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>SSDEBUGPS.dll を SQL Server 2005 コンピューターにコピーするには  
  
1.  同じ名前とパスがディレクトリにファイルをコピー、[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]マシンです。  
  
2.  開くことで登録、**コマンド プロンプト**と、次のコマンドを実行します。  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```