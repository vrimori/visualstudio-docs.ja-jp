---
title: スレッド |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ac9293807f280efff21fb8e8a5f97ed2cf0f96a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937510"
---
# <a name="threads"></a>スレッド
デバッガーのアーキテクチャで、*スレッド*:  
  
-   計算の基本的な単位です。 スレッドには、その手順を次に、1 つのコード コンテキストから移動を単一の呼び出し履歴のコンテキスト内で順番に実行します。  
  
-   それ自体とで実行されているプログラムを識別できます。 スレッドは、という名前の中断、および再開できます。 スレッドはまた、関連付けられているスタック フレームを列挙し、いくつかの条件下では、別のスタック フレームに移動できます。 スタック フレームのコンテキストを指定するには、スレッドを返せるその関連付けられた論理スレッド存在する場合。 スレッドが中断カウントに表示されることがあるなどのプロパティ、**スレッド**IDE のウィンドウ。  
  
-   によって表される、 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)インターフェイス、通常、デバッグ エンジン (DE) またはプログラムを実行するための仮想マシンを作成します。  
  
## <a name="see-also"></a>関連項目  
 [プログラム](../../extensibility/debugger/programs.md)   
 [スタック フレーム](../../extensibility/debugger/stack-frames.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [セッション デバッグ マネージャー](../../extensibility/debugger/session-debug-manager.md)