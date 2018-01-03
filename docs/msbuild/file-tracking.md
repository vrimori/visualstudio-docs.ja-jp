---
title: "ファイルの追跡 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ea3972ae1ce268a85a41be47b81f1abb76d7d409
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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