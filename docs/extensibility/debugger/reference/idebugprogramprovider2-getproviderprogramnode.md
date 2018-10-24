---
title: IDebugProgramProvider2::GetProviderProgramNode |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d26b74928985feefda3acdc8594c35096fc4e0b4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821325"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
特定のプログラムの [プログラム] ノードを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```csharp  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `Flags`  
 [in]フラグの組み合わせ、 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)列挙体。 次のフラグは、この呼び出しの一般的なものは。  
  
|フラグ|説明|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|呼び出し元は、リモート マシンで実行されています。|  
|`PFLAG_DEBUGGEE`|現在デバッグ中の呼び出し元 (ノードごとにマーシャ リングに関する追加情報が返される)。|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|呼び出し元に接続されているが、デバッガーによって起動されません。|  
  
 `pPort`  
 [in]呼び出し元のプロセス、ポートがで実行されています。  
  
 `processId`  
 [in][AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)対象のプログラムを含むプロセスの ID を保持する構造体。  
  
 `guidEngine`  
 [in]プログラムは、(ある場合) に接続されているデバッグ エンジンの GUID です。  
  
 `programId`  
 [in]プログラム ノードを取得する対象のプログラムの ID。  
  
 `ppProgramNode`  
 [out][IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)要求されたプログラム ノードを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)