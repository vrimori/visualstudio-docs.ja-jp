---
title: プロセス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c07a9cb6c16f09f2f55b543087e25d85bc300c0
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251778"
---
# <a name="processes"></a>プロセス
デバッガーのアーキテクチャで、*プロセス*:  
  
-   プログラムの一連のコンテナーです。 Windows プロセス、スレッドのセットのコンテナーであると密接に似ています。  
  
-   名前、識別子、または物理的な識別子で自身を識別できます。  
  
-   実行中のすべてのプログラム (とそのスレッド) を列挙できます。  
  
-   自体では、実行されているポートとそれを含んでいるマシンを記述できます。  
  
-   1 つを作成したり、他のプログラムの作成、プログラムを終了またはプログラムを停止します。  
  
-   によって表される、 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)インターフェイスで、プロセスを起動するときに作成されます。 いずれかのセッション デバッグ マネージャー (SDM) プロセスの起動時または[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)します。  
  
 パッケージのデバッグは呼び出すことによって、プロセスにデバッグ エンジン (DE) をアタッチすることができます[アタッチ](../../extensibility/debugger/reference/idebugprocess2-attach.md)デが処理できるプロセスで実行されているすべての可能なプログラムにアタッチすることを意味します。 たとえば場合、DE、共通言語ランタイムは、プロセスにアタッチして、マネージ コードが実行されているプログラムのみにアタッチします。  
  
## <a name="see-also"></a>関連項目  
 [プログラム](../../extensibility/debugger/programs.md)   
 [スレッド](../../extensibility/debugger/threads.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [パッケージをデバッグします。](../../extensibility/debugger/debug-package.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [添付](../../extensibility/debugger/reference/idebugprocess2-attach.md)