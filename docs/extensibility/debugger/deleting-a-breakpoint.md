---
title: "ブレークポイントを削除します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ブレークポイントを削除します。"
  - "[デバッグの SDK] のデバッグ、ブレークポイントを削除します。"
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# ブレークポイントを削除します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次に保留中のブレークポイントを削除するときにプロセスを示しています :  
  
## 削除する手順  
 デバッグ セッションのマネージャーは \(SDM\)バインドされているコントロールから保留中のブレークポイントとすべてのバインド ブレークポイントを削除するに [IDebugPendingBreakpoint2:: 削除](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) のメソッドを呼び出します。  
  
> [!NOTE]
>  単一のバインド ブレークポイントは[IDebugBoundBreakpoint2:: 削除](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md) の呼び出しによって削除できます。  
  
## 参照  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)