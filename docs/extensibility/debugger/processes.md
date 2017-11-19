---
title: "プロセス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f295dd93580caee4b6288febf7e83c09736b6080
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="processes"></a>プロセス
デバッガーのアーキテクチャの観点から、**プロセス**:  
  
-   一連のプログラムのコンテナーです。 Windows プロセス、スレッドのセットのコンテナーに非常に似ています。  
  
-   名前、識別子、または物理的な識別子をそれ自体を特定できます。  
  
-   実行中のすべてのプログラム (とそれらのスレッド) を列挙できます。  
  
-   自体と、ポートで実行されていることが含まれるコンピューターを記述できます。  
  
-   1 つを作成したり、他のプログラムの作成、プログラムを終了またはプログラムを停止します。  
  
-   によって表される、 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)インターフェイスで、プロセスを起動するときに作成します。 いずれか、セッション デバッグ マネージャーによって (SDM) プロセスの起動時または[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)です。  
  
 デバッグ パッケージがデバッグ エンジン (DE) プロセスにアタッチするを呼び出して[アタッチ](../../extensibility/debugger/reference/idebugprocess2-attach.md)です。 これは、デに処理可能なプロセスで実行されているすべての可能なプログラムにアタッチすることを意味します。 たとえば、DE、共通言語ランタイムは、プロセスにアタッチする場合、マネージ コードを実行しているプログラムにのみアタッチします。  
  
## <a name="see-also"></a>関連項目  
 [プログラム](../../extensibility/debugger/programs.md)   
 [スレッド](../../extensibility/debugger/threads.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [パッケージをデバッグします。](../../extensibility/debugger/debug-package.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [添付](../../extensibility/debugger/reference/idebugprocess2-attach.md)