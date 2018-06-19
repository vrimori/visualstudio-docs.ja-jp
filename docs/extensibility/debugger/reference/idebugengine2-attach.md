---
title: IDebugEngine2::Attach |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 264ef65472bf3d003852f2f7efc0fe21ee45d2a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107921"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
デバッグ エンジン (DE) をプログラムまたはプログラムにアタッチします。 DE、SDM をインプロセスで実行中は、するときに、セッションのデバッグ マネージャー (SDM) によって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pProgram`  
 [in]配列[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)にアタッチされているプログラムを表すオブジェクト。 これらは、ポート プログラムです。  
  
 `rgpProgramNodes`  
 [in]配列[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)プログラムごとに 1 つずつプログラム ノードを表すオブジェクト。 この配列内のプログラムのノードを表すようにして、同じプログラム`pProgram`です。 プログラムのノードには、デにアタッチするプログラムを識別できるようにが与えられます。  
  
 `celtPrograms`  
 [in]プログラムやプログラムのノードの数、`pProgram`と`rgpProgramNodes`配列。  
  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM にデバッグ イベントを送信するために使用するオブジェクト。  
  
 `dwReason`  
 [in]値、 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)これらのプログラムをアタッチする理由を指定する列挙です。 詳細については、「解説」を参照してください。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 次のように、プログラムにアタッチするための 3 つの理由があります。  
  
-   `ATTACH_REASON_LAUNCH` ユーザーが含まれるプロセスを起動するため、プログラムを DE がアタッチすることを示します。  
  
-   `ATTACH_REASON_USER` ユーザーがプログラム (またはプログラムを含むプロセス) にアタッチする DE を明示的に要求することを示します。  
  
-   `ATTACH_REASON_AUTO` 既に特定のプロセスでは、他のプログラムをデバッグするため、DE が特定のプログラムにアタッチすることを示します。 これとも呼ばれますのオート アタッチします。  
  
 このメソッドが呼び出されたときに、DE はシーケンス内のこれらのイベントを送信する必要があります。  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (かどうかは、既に送信されていないデバッグ エンジンの特定のインスタンス用)  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 さらに、アタッチする理由は、する場合`ATTACH_REASON_LAUNCH`、送信する必要があります、DE、 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)イベント。  
  
 DE 取得 1 回、 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)オブジェクトのデバッグ中のプログラムに対応する、任意のプライベート インターフェイスのクエリを実行できます。  
  
 によって指定された配列で、[プログラム] ノードのメソッドを呼び出す前に`pProgram`または`rgpProgramNodes`、権限借用、必要な場合で有効にする、`IDebugProgram2`プログラム ノードを表すインターフェイス。 通常、ただし、この手順は必要ではありません。 詳細については、次を参照してください。[セキュリティの問題](../../../extensibility/debugger/security-issues.md)です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)