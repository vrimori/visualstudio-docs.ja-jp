---
title: IDebugEngine2::Attach |Microsoft Docs
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
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 260d3fcbe58b9db1b1f465c249a44a5ee6d9a6aa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781981"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

デバッグ エンジン (DE) をプログラムまたはプログラムにアタッチします。 DE、SDM をインプロセスで実行されているときに、セッション デバッグ マネージャー (SDM) によって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pProgram`  
 [in]配列の[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)に接続するプログラムを表すオブジェクト。 これらは、ポート プログラムです。  
  
 `rgpProgramNodes`  
 [in]配列の[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)プログラム ノードは、各プログラムのいずれかを表すオブジェクト。 この配列内のプログラムのノードで同じプログラムを表す`pProgram`します。 デにアタッチするプログラムを識別できるように、プログラムのノードが提供されます。  
  
 `celtPrograms`  
 [in]プログラムやプログラムのノードの数、`pProgram`と`rgpProgramNodes`配列。  
  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM にデバッグ イベントを送信に使用するオブジェクト。  
  
 `dwReason`  
 [in]値、 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)これらのプログラムをアタッチするための理由を指定する列挙体。 詳細については、「解説」を参照してください。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 次のように、プログラムにアタッチするための 3 つの理由があります。  
  
- `ATTACH_REASON_LAUNCH` ユーザーにそれを含んでいるプロセスが起動されるので、DE がプログラムに添付することを示します。  
  
- `ATTACH_REASON_USER` ユーザーがプログラム (または、プロセス、プログラムを含む) にアタッチする DE を明示的に要求することを示します。  
  
- `ATTACH_REASON_AUTO` 既に特定のプロセスでは、他のプログラムのデバッグのために、特定のプログラムに、DE をアタッチすることを示します。 これもと呼ばれる自動アタッチします。  
  
  このメソッドが呼び出されたときに、DE はシーケンス内のこれらのイベントを送信する必要があります。  
  
1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (かどうかそれが既に送信されていません、デバッグ エンジンの特定のインスタンスの)  
  
2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
   さらに、アタッチするための理由である場合`ATTACH_REASON_LAUNCH`、送信する必要があります、DE、 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)イベント。  
  
   DE 取得 1 回、 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)オブジェクトのデバッグ中のプログラムに対応する、任意のプライベート インターフェイスのクエリを実行できます。  
  
   指定された配列で、[プログラム] ノードのメソッドを呼び出す前に`pProgram`または`rgpProgramNodes`、権限借用では、必要な場合、する必要がありますで有効にする、`IDebugProgram2`プログラム ノードを表すインターフェイスです。 通常、ただし、この手順は必要ではありません。 詳細については、次を参照してください。[セキュリティの問題](../../../extensibility/debugger/security-issues.md)します。  
  
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

