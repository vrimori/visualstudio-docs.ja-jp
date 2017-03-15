---
title: "ブレークポイントの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ブレークポイントを作成します。"
  - "[デバッグの SDK] のデバッグ、ブレークポイントの作成"
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# ブレークポイントの作成
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次にブレークポイントを作成するプロセスについて説明します。  
  
## ブレークポイントの作成メソッド  
 ブレークポイントをバインドするために必要なモジュールが読み込まれるとデバッグ セッションの管理者は\(SDM\) 次のメソッドを呼び出しています :  
  
1.  [IDebugPendingBreakpoint2:: 有効化](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)  
  
2.  [IDebugPendingBreakpoint2:: 仮想化します。](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)  
  
3.  [IDebugPendingBreakpoint2:: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)  
  
    > [!NOTE]
    >  **CanBind** はユーザーが \[ブレークポイント\] ウィンドウからブレークポイントを設定する場合にのみ呼び出されます。  
  
4.  [IDebugPendingBreakpoint2:: バインド](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)  
  
5.  [IDebugPendingBreakpoint2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)  
  
## 参照  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)