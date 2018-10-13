---
title: プロセス |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 218f6aa05bebfe0d35776b64e6a42e4fbea4e72f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296466"
---
# <a name="processes"></a>プロセス
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

デバッガーのアーキテクチャの観点から、**プロセス**:  
  
-   プログラムの一連のコンテナーです。 Windows プロセス、スレッドのセットのコンテナーであると密接に似ています。  
  
-   名前、識別子、または物理的な識別子で自身を識別できます。  
  
-   実行中のすべてのプログラム (とそのスレッド) を列挙できます。  
  
-   自体では、実行されているポートとそれを含んでいるマシンを記述できます。  
  
-   1 つを作成したり、他のプログラムの作成、プログラムを終了またはプログラムを停止します。  
  
-   によって表される、 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)インターフェイスで、プロセスを起動するときに作成されます。 いずれかのセッション デバッグ マネージャー (SDM) プロセスの起動時または[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)します。  
  
 パッケージのデバッグは呼び出すことによって、プロセスにデバッグ エンジン (DE) をアタッチすることができます[アタッチ](../../extensibility/debugger/reference/idebugprocess2-attach.md)します。 つまり、DE が処理できるプロセスで実行されているすべての可能なプログラムにアタッチします。 たとえば場合、DE、共通言語ランタイムは、プロセスにアタッチして、マネージ コードが実行されているプログラムのみにアタッチします。  
  
## <a name="see-also"></a>関連項目  
 [プログラム](../../extensibility/debugger/programs.md)   
 [スレッド](../../extensibility/debugger/threads.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [パッケージをデバッグします。](../../extensibility/debugger/debug-package.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [添付](../../extensibility/debugger/reference/idebugprocess2-attach.md)

