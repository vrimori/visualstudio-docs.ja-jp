---
title: デバッガー イベントの呼び出し |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86c48d072baa53cf3f8ba0a6d903021e6c396afa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538159"
---
# <a name="calling-debugger-events"></a>デバッガーのイベントの呼び出し
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[デバッガー イベントの呼び出し](https://docs.microsoft.com/visualstudio/extensibility/debugger/calling-debugger-events)します。  
  
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
 [カスタム デバッグ エンジンの作成](../../extensibility/debugger/creating-a-custom-debug-engine.md)

