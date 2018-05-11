---
title: IDebugProcess2::Attach |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56f14b399a904c2584e81c2b6c8f344654b69a18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
セッションのデバッグ マネージャー (SDM) をプロセスにアタッチします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)デバッグ イベント通知のために使用されるオブジェクト。  
  
 `rgguidSpecificEngines`  
 [in]プロセスで実行されているプログラムのデバッグに使用するデバッグ エンジンの Guid の配列。 このパラメーターは、null 値を指定できます。 詳細については、「解説」を参照してください。  
  
 `celtSpecificEngines`  
 [in]エンジンでのデバッグの数、`rgguidSpecificEngines`配列とのサイズ、`rghrEngineAttach`配列。  
  
 `rghrEngineAttach`  
 [入力、出力].デバッグ エンジンによって返される HRESULT コードの配列。 この配列のサイズがで指定された、`celtSpecificEngines`パラメーター。 各コードは、いずれかで、通常`S_OK`または`S_ATTACH_DEFERRED`です。 後者は、DE がプログラムに現在アタッチされていることを示しません。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 次の表は、他の値を示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定されたプロセスは、デバッガーに既にアタッチされています。|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|接続処理中にセキュリティ違反が発生しました。|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|デスクトップのプロセスは、デバッガーをアタッチできません。|  
  
## <a name="remarks"></a>コメント  
 指定されたデバッグ エンジン (DE) でデバッグできるプロセスで実行されているすべてのプログラム、SDM をアタッチするプロセスにアタッチする、`rgguidSpecificEngines`配列。 設定、`rgguidSpecificEngines`パラメーターは null を値または含める`GUID_NULL`プロセス内のすべてのプログラムにアタッチする配列。  
  
 送信されるすべてのデバッグ イベント、プロセスで発生する、指定された[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)オブジェクト。 これは、 `IDebugEventCallback2` SDM は、このメソッドを呼び出すと、オブジェクトを指定します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)