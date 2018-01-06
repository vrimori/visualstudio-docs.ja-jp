---
title: "IDebugProcess2::Attach |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::Attach
helpviewer_keywords: IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 47b14c3de6b5b9980e2ad420596a1243e84c8882
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)