---
title: デバッガー イベントの呼び出し |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a24c661c986116d9966d2ca5785bd51e2726c6d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998405"
---
# <a name="call-debugger-events"></a>デバッガー イベントを呼び出す
デバッグ セッションでのイベントは、特定の順序で発生します。  
  
## <a name="discussion"></a>説明  
 デバッグ エンジン (DE) とセッション デバッグ マネージャー (SDM) 間の呼び出しのパターンを理解するには、次は、一般的なデバッグ セッションで発生するイベントの呼び出しの順序を表します。  
  
1.  [アタッチとデタッチをプログラムする](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [デバッガーを起動します。](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [プログラムの終了](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [ブレークポイントの作成](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [ときに、ブレークポイントがバインドまたはバインド解除になります。](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [ブレークポイント エラー](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [ブレークポイントのヒット](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [ブレークポイントの削除](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [中断モード](../../extensibility/debugger/entering-break-mode.md)  
  
10. [中断モードでのステップ実行](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [中断モードでの式の評価](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [例外処理](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>関連項目  
 [カスタム デバッグ エンジンを作成します。](../../extensibility/debugger/creating-a-custom-debug-engine.md)