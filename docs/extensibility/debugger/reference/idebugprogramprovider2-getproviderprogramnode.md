---
title: "IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramProvider2::GetProviderProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

特定のプログラムのプログラムのノードを取得します。  
  
## 構文  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```c#  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### パラメーター  
 `Flags`  
 \[入力\] [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) の列挙体のフラグの組み合わせ。  次のフラグはこの呼び出しのために一般的です :  
  
|フラグ|Description|  
|---------|-----------------|  
|`PFLAG_REMOTE_PORT`|呼び出し元はリモート コンピューターで実行されています。|  
|`PFLAG_DEBUGGEE`|呼び出し元が現在デバッグ中 \(配置に関する追加情報は各ノードに対してを返します\)。|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|呼び出し元がにアタッチされているデバッガーによって呼び出されます。|  
  
 `pPort`  
 \[入力\] 呼び出しプロセスが実行されているポート。  
  
 `processId`  
 \[入力\] 対象のプログラムを含むプロセスの ID を保持 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) の構造体。  
  
 `guidEngine`  
 \[入力\] プログラムがアタッチされているデバッグ エンジンの GUID \(存在する場合\)。  
  
 `programId`  
 \[入力\] プログラムのノードを取得するプログラム ID。  
  
 `ppProgramNode`  
 \[入力\] [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) に要求されたプログラムのノード。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)