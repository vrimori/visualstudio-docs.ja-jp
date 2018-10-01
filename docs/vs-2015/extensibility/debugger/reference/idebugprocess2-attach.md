---
title: IDebugProcess2::Attach |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90ff2520a64ca338cb703c5e22f8a0c021b52540
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537843"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugProcess2::Attach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess2-attach)します。  
  
セッション デバッグ マネージャー (SDM) をプロセスにアタッチします。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]プロセスで実行するプログラムのデバッグに使用するデバッグ エンジンの Guid の配列。 このパラメーターは、null 値を指定できます。 詳細については、「解説」を参照してください。  
  
 `celtSpecificEngines`  
 [in]エンジンでのデバッグの数、`rgguidSpecificEngines`配列とのサイズ、`rghrEngineAttach`配列。  
  
 `rghrEngineAttach`  
 [入力、出力]デバッグ エンジンによって返される HRESULT コードの配列。 この配列のサイズがで指定された、`celtSpecificEngines`パラメーター。 各コードは、いずれかで、通常`S_OK`または`S_ATTACH_DEFERRED`します。 後者の場合は、DE がプログラムに現在接続されていることを示しません。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 次の表では、使用可能なその他の値を示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定されたプロセスがデバッガーに既に結び付けられています。|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|アタッチ時にセキュリティ違反が発生しました。|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|デスクトップのプロセスをデバッガーにアタッチできません。|  
  
## <a name="remarks"></a>Remarks  
 指定されたデバッグ エンジン (DE) でデバッグできるプロセスで実行されているすべてのプログラム、SDM をアタッチするプロセスにアタッチ、`rgguidSpecificEngines`配列。 設定、`rgguidSpecificEngines`パラメーターを null に値を含めたり`GUID_NULL`プロセス内のすべてのプログラムにアタッチする配列。  
  
 プロセスで発生するすべてのデバッグ イベントに送信される、指定された[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)オブジェクト。 これは、 `IDebugEventCallback2` SDM は、このメソッドを呼び出すときにオブジェクトが提供されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

