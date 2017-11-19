---
title: "ブレークポイントに関連するメソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0d743c98fd9e311f7f118c152e579178b07513d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="breakpoint-related-methods"></a>ブレークポイントに関連するメソッド
デバッグ エンジン (DE) は、ブレークポイントの設定をサポートする必要があります。 Visual Studio のデバッグには、次の種類のブレークポイントはサポートします。  
  
-   バインド  
  
     UI から要求され、指定されたコードの場所に正常にバインドされています。  
  
-   保留  
  
     UI が実際にはまだバインドされていません手順を通じて要求  
  
## <a name="discussion"></a>説明  
 たとえば、保留中のブレークポイントは、手順がまだ読み込まれていないときに発生します。 コードが読み込まれるときに、保留中のブレークポイント試用し、命令を挿入中断、コードでは、所定の場所にあるコードにバインドします。 イベントは、バインドに成功を示すために、またはバインド エラーがあったことを通知する、セッションのデバッグ マネージャー (SDM) に送信されます。  
  
 保留中のブレークポイントは、対応するバインドされたブレークポイントの内部リストも管理します。 保留中のブレークポイントを引き起こすことが多くのブレークポイントの挿入のコードにします。 ブレークポイントがバインドされている対応して、Visual Studio の UI のデバッグが保留中のブレークポイントのツリー ビューを示します。  
  
 作成と使用保留中のブレークポイントの実装が必要、 [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)メソッドだけでなく、次の方法の[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)インターフェイスです。  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|指定したかどうかを決定する保留中のブレークポイントをコードの場所にバインドできます。|  
|[バインド](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|指定された保留中のブレークポイントをバインド コードの 1 つまたは複数の場所。|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|保留中のブレークポイントの状態を取得します。|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|保留中のブレークポイントを作成するために使用するブレークポイントの要求を取得します。|  
|[有効にします。](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|保留中のブレークポイントの有効な状態を切り替えます。|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|すべてのブレークポイントの保留中のブレークポイントからバインドを列挙します。|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|保留中のブレークポイントに起因するすべてのエラー ブレークポイントを列挙します。|  
|[削除](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|保留中のブレークポイントとそこからバインドされているすべてのブレークポイントを削除します。|  
  
 バインドされたブレークポイントとブレークポイントのエラーを列挙するには、すべてのメソッドを実装する必要があります[IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)および[IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)です。  
  
 保留中のブレークポイントをコードにバインドする場所は、次の実装を必要と[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)メソッドです。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|ブレークポイントに保留中のブレークポイントを取得します。|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|バインドされたブレークポイントの状態を取得します。|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|ブレークポイントを説明するブレークポイントの解像度を取得します。|  
|[有効にします。](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|有効またはブレークポイントを無効にします。|  
|[削除](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|バインドされたブレークポイントを削除します。|  
  
 解像度と情報には、次の実装が必要となる要求[IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)メソッドです。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|解像度によって表されるブレークポイントの種類を取得します。|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|ブレークポイントを表すブレークポイント解決情報を取得します。|  
  
 バインド中に発生する可能性があるエラーの解決は、次の実装を必要[IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)メソッドです。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|エラー ブレークポイントを含む保留中のブレークポイントを取得します。|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|エラー ブレークポイントを説明するブレークポイントのエラーの解決を取得します。|  
  
 バインド中に発生する可能性があるエラーの解決は、次のメソッドもが必要です。 [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)です。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|ブレークポイントの種類を取得します。|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|ブレークポイントの解決に関する情報を取得します。|  
  
 ブレークポイントの位置のソース コードを表示する必要がありますのメソッドを実装する[IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)のメソッドや[IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)です。  
  
## <a name="see-also"></a>関連項目  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)