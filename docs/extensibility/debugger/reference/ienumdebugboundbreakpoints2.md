---
title: "IEnumDebugBoundBreakpoints2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugBoundBreakpoints2"
helpviewer_keywords: 
  - "IEnumDebugBoundBreakpoints2"
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugBoundBreakpoints2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは保留中のブレークポイントやブレークポイントのバインド イベントに関連付けられたバインド ブレークポイントを列挙します。  
  
## 構文  
  
```  
IEnumDebugBoundBreakpoints2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンはブレークポイント \(DE\) のサポートの一部としてこのインターフェイスを実装します。  このインターフェイスはブレークポイントがサポートされている場合実行する必要があります。  
  
## 呼び出し元のメモ  
 Visual Studio では :  
  
-   トリガーされたすべてのブレークポイントの一覧を表すこのインターフェイスを取得 [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)。  
  
-   バインドされたすべてのブレークポイントの一覧を表すこのインターフェイスを取得 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)。  
  
-   すべてのブレークポイントの一覧を表すこのインターフェイスを取得 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) は保留中のブレークポイントにバインドされました。  
  
## Vtable の順序でメソッド  
 次の表は `IEnumDebugBoundBreakpoints2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|列挙体シーケンスのバインド ブレークポイントの指定した数を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|列挙体シーケンスのバインド ブレークポイントの指定した数の要素をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|現在の列挙子と同じ列挙状態を含む列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|列挙子のバインド ブレークポイントの数を取得します。|  
  
## 解説  
 Visual Studio IDE でのブレークポイントの表示を更新するにはこのインターフェイスで表されるバインド ブレークポイントを使用します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)