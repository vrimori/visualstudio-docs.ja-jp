---
title: 'エラー: SQL できます&#39;t が SSDEBUGPS を見つける |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1782412ded2c4edff0da29b13160107664170d20
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546834"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>エラー: SQL できます&#39;t が SSDEBUGPS を見つける
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[エラー: SQL できます&#39;t SSDEBUGPS を見つける](https://docs.microsoft.com/visualstudio/debugger/error-sql-can-t-find-ssdebugps)します。  
  
SSDEBUGPS.dll は、SQL Server のデバッグ ホスト コンポーネントです。  
  
 このエラーはデバッグの開始時に発生し、指定されたファイルが [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] コンピューターに存在しないことを示します。 リモート デバッグのセットアップが実行されていない、または何らかの理由でこのファイルが削除されていることが原因として考えられます。  
  
 このエラーを解決するのには 2 つの方法: リモート デバッグのセットアップを再実行し、ファイルをコピーして、[!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]マシン。  
  
 リモート デバッグのセットアップを再実行する」の手順に従います[リモート デバッグ](../debugger/remote-debugging.md)します。  
  
 Ssdebugps.dll のファイルのコピーを見つけるには場合に、コピーできます、[!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]マシン。 このファイルが存在する場合は、\Program Files\ Common Files\Microsoft Shared\SQL Debugging にあります。 別のあります[!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]コンピューターやコンピューターとは[!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]インストールします。  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>SSDEBUGPS.dll を SQL Server 2005 コンピューターにコピーするには  
  
1.  ファイルを同じ名前とパスを使用してディレクトリにコピー、[!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]マシン。  
  
2.  登録を開いて、**コマンド プロンプト**、次のコマンドを実行しています。  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```



