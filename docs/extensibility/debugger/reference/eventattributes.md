---
title: "複数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EVENTATTRIBUTES
helpviewer_keywords: EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 097a61ff6c96fd4901265ad960169fd5ec7244c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="eventattributes"></a>複数
イベント属性を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```csharp  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## <a name="members"></a>メンバー  
 EVENT_ASYNCHRONOUS  
 イベントは、非同期イベントに応答が必要ないことを示します。  
  
 EVENT_SYNCHRONOUS  
 イベントが同期的です。により返信[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)です。  
  
 EVENT_STOPPING  
 停止イベントであることを示します。 いずれかと組み合わせることは`EVENT_ASYNCHRONOUS`または`EVENT_SYNCHRONOUS`です。  
  
 EVENT_ASYNC_STOP  
 非同期の停止イベントを示します。 現在、このようなイベントはありません。 このフラグは、プレース ホルダーにすぎません。  
  
 EVENT_SYNC_STOP  
 同期の停止イベントを示します (の組み合わせ`EVENT_SYNCHRONOUS`と`EVENT_STOPPING`)。 この値は、停止イベントを送信するときにデバッグ エンジン (DE) によって使用されます。 呼び出しを使用して、返信があった[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)、[ステップ](../../../extensibility/debugger/reference/idebugprogram2-step.md)、または[続行](../../../extensibility/debugger/reference/idebugprogram2-continue.md)です。  
  
 EVENT_IMMEDIATE  
 IDE に即座に同期的に送信されるイベントを示します。 このフラグはその他のフラグと同様に`EVENT_ASYNCHRONOUS`、 `EVENT_SYNCHRONOUS`、または`EVENT_SYNC_STOP`イベントとその返信メカニズム (存在する場合) が呼びますファクトの種類を指定します。  
  
 EVENT_EXPRESSION_EVALUATION  
 イベントは、式の評価の結果です。  
  
## <a name="remarks"></a>コメント  
 これらの値が渡された、`dwAttrib`のパラメーター、[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)メソッドです。  
  
 これらの値は、ビットごとと組み合わせること`OR`です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)