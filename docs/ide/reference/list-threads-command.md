---
title: ListThreads コマンド | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 094ba1b16f208d1af0ba9426daba67aed604f0c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="list-threads-command"></a>ListThreads コマンド
現在のプログラムのスレッド一覧を表示します。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>引数  
 `index`  
 任意。 スレッドをインデックスで選択して、現在のスレッドにします。  
  
## <a name="remarks"></a>コメント  
 指定した場合、`index` 引数により、示されたスレッドが現在のスレッドとしてマークされます。 一覧の現在のスレッドの横にはアスタリスク (*) が表示されます。  
  
## <a name="example"></a>例  
  
```  
>Debug.ListThreads   
```  
  
## <a name="see-also"></a>参照  
 [ListCallStack コマンド](../../ide/reference/list-call-stack-command.md)   
 [逆アセンブリの一覧表示コマンド](../../ide/reference/list-disassembly-command.md)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)