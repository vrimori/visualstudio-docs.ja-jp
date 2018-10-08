---
title: IDebugProgramProvider2::GetProviderProcessData |Microsoft Docs
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
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8099cdd85b4cba52c6f009a7fea3e91811c8c94f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537084"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugProgramProvider2::GetProviderProcessData](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata)します。  
  
指定されたプロセスからプログラムを実行の一覧を取得します。  
  
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
 [in]フラグの組み合わせ、 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)列挙体。 次のフラグは、この呼び出しの一般的なものは。  
  
|フラグ|説明|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|呼び出し元は、リモート マシンで実行されています。|  
|`PFLAG_DEBUGGEE`|現在デバッグ中の呼び出し元 (ノードごとにマーシャ リングに関する追加情報が返される)。|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|呼び出し元に接続されているが、デバッガーによって起動されません。|  
|`PFLAG_GET_PROGRAM_NODES`|呼び出し元が返される、プログラムのノードの一覧を求めています。|  
  
 `pPort`  
 [in]呼び出し元のプロセス、ポートがで実行されています。  
  
 `processId`  
 [in][AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)対象のプログラムを含むプロセスの ID を保持する構造体。  
  
 `EngineFilter`  
 [in] (これらが使用されますが実際に返されるすべてのプログラムが返されますエンジンが指定されていない場合、指定されたエンジンのサポート; に基づくプログラムをフィルター処理する)、このプロセスのデバッグに割り当てられているデバッグ エンジンの Guid の配列。  
  
 `pProcess`  
 [out]A [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)構造体に必要な情報が入力されます。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは通常、そのプロセスで実行されているプログラムの一覧を取得するプロセスによって呼び出されます。 返される情報の一覧は、 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)オブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

