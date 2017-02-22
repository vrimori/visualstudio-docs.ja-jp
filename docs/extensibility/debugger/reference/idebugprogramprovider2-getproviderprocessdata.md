---
title: "IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramProvider2::GetProviderProcessData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定したプロセスで実行中のプログラムの一覧を取得します。  
  
## 構文  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```c#  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
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
|`PFLAG_GET_PROGRAM_NODES`|呼び出し元はプログラムのノードの一覧を返すことを依頼します。|  
  
 `pPort`  
 \[入力\] 呼び出しプロセスが実行されているポート。  
  
 `processId`  
 \[入力\] 対象のプログラムを含むプロセスの ID を保持 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) の構造体。  
  
 `EngineFilter`  
 \[出力\] このプロセスのデバッグ用のデバッグ エンジンの GUID の配列 \(基づいて指定されたエンジンのサポートに実際に返されるフィルター処理にこれらのプログラムを使用します ; エンジンが指定されていない場合すべてのプログラムが返されます\)。  
  
 `pProcess`  
 \[入力\] 要求された情報が格納される [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md) の構造体。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドはプロセスによって通常プロセスで実行されているプログラムの一覧を取得します。  返された情報は [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) オブジェクトのリストです。  
  
## 参照  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)