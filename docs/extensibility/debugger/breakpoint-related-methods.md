---
title: "ブレークポイントに関連するメソッド | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグ SDK] ブレークポイントのデバッグ方法"
  - "ブレークポイント、メソッド"
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# ブレークポイントに関連するメソッド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッグ エンジンはブレークポイント \(DE\) の設定をサポートする必要があります。  Visual Studio のデバッグ ブレークポイントのサポート型 :  
  
-   バインド  
  
     UI によって要求されたコード指定位置にバインドする  
  
-   保留  
  
     UI で要求できますが実効命令にバインドされていません  
  
## 説明  
 たとえば保留中のブレークポイントは命令がまだ読み込まれていない場合に発生します。  コードが読み込まれるとブレークポイントはコードの挿入\] 中断命令に所定の位置にコードにバインドしてください。  イベントはデバッグ セッションのマネージャー \(SDM\) に正常な束縛を表示したり結合のエラーが発生したことを通知するために送信されます。  
  
 保留中のブレークポイントは対応するバインド ブレークポイントの内部リストを管理します。  保留中のブレークポイントの 1 はコードに多くのブレークポイントの挿入が発生する場合があります。  Visual Studio のデバッグ UI は保留中のブレークポイントおよび対応するバインド ブレークポイントのツリー ビューが表示されます。  
  
 保留中のブレークポイントの作成と使用に [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) のインターフェイス [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) のメソッドは次のメソッドの実装が必要です。  
  
|メソッド|Description|  
|----------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|保留中のブレークポイント位置指定されたコードにバインドできるかどうかを判定します。|  
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|保留中のブレークポイントを指定する一つ以上のコード位置にバインドします。|  
|[GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)|保留中のブレークポイントの状態を取得します。|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|ブレークポイントの要求を保留中のブレークポイントの作成に使用するを取得します。|  
|[&#91;有効化&#93;](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|保留中のブレークポイントの有効状態を切り替えます。|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|保留中のブレークポイントからバインドされたすべてのブレークポイントを列挙します。|  
|[EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)|保留中のブレークポイントに発生するすべてのエラーのブレークポイントを列挙します。|  
|[&#91;削除&#93;](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|これからバインドされた保留中のブレークポイントとすべてのブレークポイントを削除します。|  
  
 バインドされたブレークポイントとエラーのブレークポイントを列挙するには[IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) と [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) のすべてのメソッドを実装する必要があります。  
  
 コード位置にバインドする保留中のブレークポイント [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) の次のメソッドの実装を必要とします。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetPendingBreakpoint](../Topic/IDebugBoundBreakpoint2::GetPendingBreakpoint.md)|ブレークポイントを含む保留中のブレークポイントを取得します。|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|バインドされたブレークポイントの状態を取得します。|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|ブレークポイントを記述するブレークポイントの解決を取得します。|  
|[&#91;有効化&#93;](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|ブレークポイントを有効または無効にします。|  
|[&#91;削除&#93;](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|バインド ブレークポイントを削除します。|  
  
 解決および要求情報は [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) の次のメソッドの実装が必要です。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|解決によって表されるブレークポイントの種類を取得します。|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|ブレークポイントを記述するブレークポイントの解決方法を取得します。|  
  
 バインディング中に発生する可能性のあるエラーを解決するには [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) の次のメソッドの実装が必要です。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|エラーのブレークポイントを含む保留中のブレークポイントを取得します。|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|エラーのブレークポイントを記述するブレークポイントのエラーの解決を取得します。|  
  
 またはバインディング中に発生する可能性のあるエラーを解決するには [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) の次のメソッドが必要です。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|ブレークポイントの種類を取得します。|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|ブレークポイントの解決方法を取得します。|  
  
 ブレークポイントのソース・コードを表示するには [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) のメソッドや [IDebugStackFrame2:: GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md) のメソッドを実装する必要があります。  
  
## 参照  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)