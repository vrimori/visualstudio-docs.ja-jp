---
title: IDebugBreakpointRequest2 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72434216c2f2d8a5403e1babb169b9da651d0daf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201813"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、作成し、任意の種類のブレークポイントをバインドするために必要な情報を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 セッション デバッグ マネージャー (SDM) は、通常、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デバッグ エンジン (DE) を呼び出すことによってこのインターフェイスの受信[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)保留中のブレークポイントを作成するためにします。 呼び出し[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) DE からこのインターフェイスを取得することができます。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugBreakpointRequest2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|このブレークポイント要求のブレークポイントの場所の種類を取得します。|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|このブレークポイントの要求を記述するブレークポイント要求情報を取得します。|  
  
## <a name="remarks"></a>Remarks  
 プログラムの後にデバッグ対象が読み込まれたへの呼び出し[バインド](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)保留中のブレークポイントをプログラムで要求された場所にバインドします。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

