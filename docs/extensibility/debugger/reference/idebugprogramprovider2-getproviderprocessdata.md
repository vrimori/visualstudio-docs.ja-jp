---
title: "IDebugProgramProvider2::GetProviderProcessData |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e94e0606256eda3fb8cdcade90979342d078e125
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
指定されたプロセスから実行しているプログラムの一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```csharp  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `Flags`  
 [in]フラグの組み合わせ、 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)列挙します。 次のフラグがこの呼び出しに一般的です。  
  
|フラグ|説明|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|呼び出し元は、リモート マシンで実行されています。|  
|`PFLAG_DEBUGGEE`|呼び出し元は現在デバッグされている (ノードごとにマーシャ リングに関する追加情報が返されます)。|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|呼び出し元にアタッチされているが、デバッガーによって起動されません。|  
|`PFLAG_GET_PROGRAM_NODES`|呼び出し元は、返されるプログラム ノードのリストが求めています。|  
  
 `pPort`  
 [in]ポートが呼び出しプロセスが行われています。  
  
 `processId`  
 [in][AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)対象のプログラムを含むプロセスの ID を保持する構造体。  
  
 `EngineFilter`  
 [in]このプロセスを (それらが使用されますに基づいて指定されたエンジンのサポート。 エンジンが指定されていない場合、すべてのプログラムが返されますが、実際に返されるプログラムをフィルター処理する) をデバッグに割り当てられているデバッグ エンジンの Guid の配列。  
  
 `pProcess`  
 [out]A [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)構造を要求された情報が入力されます。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは通常、そのプロセスで実行するプログラムの一覧を取得するプロセスによって呼び出されます。 返される情報の一覧は、 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)オブジェクト。  
  
## <a name="see-also"></a>参照  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)