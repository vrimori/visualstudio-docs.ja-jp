---
title: "デバッガーのイベントを呼び出す |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3acccf7233e62ca45d450a5e33c21a286ca4a204
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="calling-debugger-events"></a>呼び出し元のデバッガー イベント
デバッグ セッションのイベントは、特定の順序で発生します。  
  
## <a name="discussion"></a>説明  
 デバッグ エンジン (DE) と、セッション デバッグ マネージャー (SDM) 間の呼び出しのパターンを理解するには、次は、一般的なデバッグ セッションで発生するイベントの呼び出しの順序を表します。  
  
1.  [アタッチおよびデタッチのプログラムへ](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [デバッガーを起動します。](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [プログラムの終了](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [ブレークポイントの作成](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [ブレークポイントがバインドされてときかになるバインド解除されました](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [ブレークポイントのエラー](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [ブレークポイントにヒット](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [ブレークポイントの削除](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [中断モード](../../extensibility/debugger/entering-break-mode.md)  
  
10. [中断モードでのステップ実行](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [中断モードでの式の評価](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [例外処理](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>関連項目  
 [カスタム デバッグ エンジンの作成](../../extensibility/debugger/creating-a-custom-debug-engine.md)