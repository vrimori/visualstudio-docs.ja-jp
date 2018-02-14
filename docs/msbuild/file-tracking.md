---
title: "ファイルの追跡 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 98bf98493d6f45be31ef98ae0b4a98bfbd66e402
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="file-tracking"></a>ファイルの追跡
ファイルの追跡では、特定のプロセスとその子プロセスについて、Windows ファイル システムの呼び出しをログに記録します。 下記の関数を呼び出すことで、このログ記録のオンとオフを切り替えるタイミングを制御したり、使用するログ ファイルを指定したりできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 現在のコンテキストの追跡を停止します。  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 [SuspendTracking](../msbuild/suspendtracking.md) の呼び出し後に追跡を再開します。  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 追跡に使用するスレッドの数を設定します。  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 新しい追跡コンテキストを開始します。  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 指定されたルートで新しい追跡コンテキストを開始します。  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 追跡を終了し、使用されているリソースを解放します。  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 追跡を一時的に中断します。  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 すべてのコンテキストに対する追跡ログを書き出します。  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 現在のコンテキストに対する追跡ログを書き出します。