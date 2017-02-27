---
title: "IDebugPendingBreakpoint2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2"
helpviewer_keywords: 
  - "IDebugPendingBreakpoint2 インターフェイス"
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPendingBreakpoint2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはコード位置にバインドする準備が整ったブレークポイントを表します。  
  
## 構文  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンはブレークポイント \(DE\) のサポートの一部としてこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) の呼び出しは [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) のインターフェイスから保留中のブレークポイントを作成します。  [バインド](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) の呼び出しはプログラムのバインド ブレークポイントを表す `IDebugBreakpoint2` のインターフェイスを作成します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugPendingBreakpoint2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|この保留中のブレークポイントがコード位置にバインドできるかどうかを判定します。|  
|[バインド](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|一つ以上のコード位置にこの保留中のブレークポイントをバインドします。|  
|[GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)|この保留中のブレークポイントの状態を取得します。|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|この保留中のブレークポイントの作成に使用されたブレークポイントの要求を取得します。|  
|[仮想化します。](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|この保留中のブレークポイントの仮想化された状態を切り替えます。|  
|[\[有効化\]](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|この保留中のブレークポイントの有効状態を切り替えます。|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|この条件が保留中のブレークポイントに関連付けられている変更または設定します。|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|パスの数がこの保留中のブレークポイントに関連付けられている変更または設定します。|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|この保留中のブレークポイントからバインドされたすべてのブレークポイントを列挙します。|  
|[EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)|この保留中のブレークポイントに発生したすべてのエラーのブレークポイントを列挙します。|  
|[削除](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|これからバインドされたこの保留中のブレークポイントとすべてのブレークポイントを削除します。|  
  
## 解説  
 `IDebugPendingBreakpoint2` は必要なすべての必要な情報プロバイダーとして扱うコードに 1 一つまたは複数のプログラムに適用できるブレークポイントのバインドが考えることができます。  
  
 保留中のブレークポイントには複数のバインド ブレークポイントを生成できます。  たとえばC. のスタイルとテンプレートのブレークポイントはそのテンプレートの固有のインスタンスにバインドされたブレークポイントを生成できます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../Topic/IDebugBoundBreakpoint2::GetPendingBreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)