---
title: "スレッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f611284584b091fca390f660b3e840f6cebe048c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="threads"></a>スレッド
デバッガーのアーキテクチャの観点から、**スレッド**:  
  
-   計算の基本単位です。 スレッドは、順番に、1 回の呼び出し履歴は、次に、1 つのコードのコンテキストから移動のコンテキスト内では、その手順を実行します。  
  
-   それ自体で実行されているとという名前、中断して再開プログラムを識別できます。 スレッドはまた、その関連付けられているスタック フレームを列挙し、いくつかの条件下では、別のスタック フレームに移動できます。 スタック フレームのコンテキストを指定するには、スレッド返すことができます、関連付けられた論理スレッド存在する場合。 スレッドは中断カウント、IDE の [スレッド] ウィンドウで表示できるなどのプロパティを持ちます。  
  
-   によって表される、 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)インターフェイス、通常、デバッグ エンジン (DE) またはプログラムの実行の結果としての仮想マシンによって作成します。  
  
## <a name="see-also"></a>参照  
 [プログラム](../../extensibility/debugger/programs.md)   
 [スタック フレーム](../../extensibility/debugger/stack-frames.md)   
 [デバッグ エンジン](../../extensibility/debugger/debug-engine.md)   
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)   
 [セッション デバッグ マネージャー](../../extensibility/debugger/session-debug-manager.md)