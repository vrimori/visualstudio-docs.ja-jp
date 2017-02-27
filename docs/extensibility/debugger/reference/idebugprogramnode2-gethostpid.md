---
title: "IDebugProgramNode2::GetHostPid | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::GetHostPid"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetHostPid"
ms.assetid: e65b4b15-46d8-4ca7-9456-2b4c078f7cf9
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgramNode2::GetHostPid
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プロセスホスティングのシステム プロセス識別子にプログラムを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetHostPid (   
   AD_PROCESS_ID * pdwHostPid  
);  
```  
  
```c#  
int GetHostPid (   
   out AD_PROCESS_ID pdwHostPid  
);  
```  
  
#### パラメーター  
 `pdwHostPid`  
 \[入力\] ホスティングプロセスのシステム プロセス識別子を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 使用例  
 次の例に `CProgram` の単純なオブジェクトに対してこのメソッドを実装する方法を実装するインターフェイスの [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 示します。  
  
```cpp#  
HRESULT CProgram::GetHostPid(DWORD* pdwHostPid) {    
    // Check for valid argument.    
   if (pdwHostPid)    
    {    
        // Get the process identifier of the calling process.    
      *pdwHostPid = GetCurrentProcessId();    
  
        return S_OK;    
    }    
  
    return E_INVALIDARG;    
}    
```  
  
## 参照  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)