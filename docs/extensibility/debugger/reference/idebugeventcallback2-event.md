---
title: "IDebugEventCallback2::Event |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEventCallback2::Event
helpviewer_keywords: IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c1a69c3ce3a8b59c1cea7b9282d0169c3637729
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
デバッグ イベントの通知を送信します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```csharp  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pEngine`  
 [in][IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)をこのイベントを送信するデバッグ エンジン (DE) を表すオブジェクト。 このパラメーターを入力する、DE が必要です。  
  
 `pProcess`  
 [in][IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)イベントが発生したプロセスを表すオブジェクト。 このパラメーターは、セッション デバッグ マネージャー (SDM) に入力されます。 デは常にこのパラメーターに null 値を渡します。  
  
 `pProgram`  
 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)をこのイベントが発生するプログラムを表すオブジェクト。 ほとんどのイベントのこのパラメーターは、null 値ではありません。  
  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)をこのイベントが発生したスレッドを表すオブジェクト。 イベントを停止するには、このパラメーターは、スタック フレームがこのパラメーターから取得した null 値を指定できません。  
  
 `pEvent`  
 [in][IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)デバッグ イベントを表すオブジェクト。  
  
 `riidEvent`  
 [in]取得するには、どのイベント インターフェイスを識別する GUID を`pEvent`パラメーター。  
  
 `dwAttrib`  
 [in]フラグの組み合わせ、[複数](../../../extensibility/debugger/reference/eventattributes.md)列挙します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドを呼び出すときに、`dwAttrib`パラメーターはから返される値と一致する必要があります、 [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)に渡されたメソッド、イベント オブジェクトに対して呼び出されると、`pEvent`パラメーター。  
  
 すべてのデバッグ イベントは、かどうか、イベント自体が非同期かに関係なく、非同期的にポストされます。 デがこのメソッドを呼び出すと、戻り値は示しませんイベントが処理されたかどうか、イベントを受信したかどうか。 実際には、ほとんどの状況では、イベント処理されていないこのメソッドが戻るときにします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)