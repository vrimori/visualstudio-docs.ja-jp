---
title: ブレークポイントに関連するメソッド |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e7e823c5fef66077ba03d4cb9eec4367b79038db
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152145"
---
# <a name="breakpoint-related-methods"></a>ブレークポイントに関連するメソッド
デバッグ エンジン (DE) には、ブレークポイントの設定をサポートする必要があります。 Visual Studio のデバッグには、次の種類のブレークポイントのサポートされています。  
  
-   バインドされています。  
  
     UI 経由で要求し、指定したコードの場所に正常にバインドされています。  
  
-   保留  
  
     UI が実際にまだバインドされていません手順を通じて要求  
  
## <a name="discussion"></a>説明  
 たとえば、保留中のブレークポイントは、手順がまだ読み込まれていないときに発生します。 コードが読み込まれるときに、保留中のコードで中断命令を挿入する、つまり所定の場所にあるコードにバインドするブレークポイントお試しください。 イベントは、バインド エラーがあったことを通知するかをバインドに成功を示すために、セッション デバッグ マネージャー (SDM) に送信されます。  
  
 保留中のブレークポイントは、対応するバインドされたブレークポイントの内部リストにも管理します。 コードのいずれかの保留中のブレークポイント、多くのブレークポイントの挿入を可能性があります。 Visual Studio の UI のデバッグは保留中のブレークポイントのツリー ビューを示し、それに対応するブレークポイントをバインドします。  
  
 作成と保留中のブレークポイントの使用の実装が必要、 [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)メソッドと、次のメソッドの[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)インターフェイス。  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|指定したかどうかを判断します。 保留中のブレークポイントをコードの場所にバインドできます。|  
|[バインド](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|指定した保留中のブレークポイントが 1 つまたは複数のコードの場所にバインドします。|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|保留中のブレークポイントの状態を取得します。|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|保留中のブレークポイントの作成に使用されるブレークポイント要求を取得します。|  
|[有効にします。](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|保留中のブレークポイントの有効な状態を切り替えます。|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|保留中のブレークポイントからバインドされているすべてのブレークポイントを列挙します。|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|保留中のブレークポイントに起因するすべてのエラー ブレークポイントを列挙します。|  
|[削除](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|保留中のブレークポイントとそこからバインドされているすべてのブレークポイントを削除します。|  
  
 バインドされたブレークポイントとブレークポイントのエラーを列挙するには、すべてのメソッドを実装する必要があります[IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)の[IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)します。  
  
 保留中のブレークポイントをコードにバインドする場所は、次の実装を必要と[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)メソッド。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|ブレークポイントがある保留中のブレークポイントを取得します。|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|バインドされたブレークポイントの状態を取得します。|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|ブレークポイントを表すブレークポイント解像度を取得します。|  
|[有効にします。](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|有効または、ブレークポイントを無効にします。|  
|[削除](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|バインドされたブレークポイントを削除します。|  
  
 解像度と要求については、次の実装が必要に[IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)メソッド。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|解像度によって表されるブレークポイントの種類を取得します。|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|ブレークポイントを表すブレークポイント解像度の情報を取得します。|  
  
 バインド中に発生する可能性のあるエラーの解決には、次の実装が必要です[IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)メソッド。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|エラーのブレークポイントを含む保留中のブレークポイントを取得します。|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|エラーのブレークポイントを表すブレークポイントのエラーの解決を取得します。|  
  
 バインド中に発生する可能性のあるエラーの解決は、の次のメソッドも必要があります。 [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|ブレークポイントの種類を取得します。|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|ブレークポイントの解決の情報を取得します。|  
  
 メソッドを実装する必要がありますのブレークポイントのソース コードを表示[IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)のメソッドや[IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)します。  
  
## <a name="see-also"></a>関連項目  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)