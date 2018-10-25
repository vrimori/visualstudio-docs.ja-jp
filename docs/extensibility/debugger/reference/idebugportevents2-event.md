---
title: IDebugPortEvents2::Event |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5c8ae7eaf353b7d682368bf3694ee73087d6e47
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897070"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
このメソッドは、作成とプロセスと、ポート上のプログラムの破棄を示すイベントを送信します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Event(  
   IDebugCoreServer2* pServer,  
   IDebugPort2*       pPort,  
   IDebugProcess2*    pProcess,  
   IDebugProgram2*    pProgram,  
   IDebugEvent2*      pEvent,  
   REFIID             riidEvent  
);  
```  
  
```csharp  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pMachine`  
 [in][IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)デバッグ サーバーを表すオブジェクトを (1 つのすべてのインスタンスを使用する必要がある[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]) で、イベントが発生しました。  
  
 `pPort`  
 [in][IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)イベントが発生したポートを表すオブジェクト。  
  
 `pProcess`  
 [in][IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)イベントが発生したプロセスを表すオブジェクト。  
  
 `pProgram`  
 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)イベントが発生したプログラムを表すオブジェクト。  
  
 `pEvent`  
 [in][IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)イベントを識別するオブジェクト。 使用できるイベントは次のとおりです。  
  
- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
  `riidEvent`  
  [in]イベントの GUID です。 イベントにキャストされるので[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)このメソッドを呼び出す前にこの識別子しやすくイベントが送信されるかを判断します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)