---
title: "IDebugDisassemblyStream2::GetCodeContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::GetCodeContext"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetCodeContext"
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::GetCodeContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

コード識別子の指定位置に対応するコード コンテキスト オブジェクトを返します。  
  
## 構文  
  
```cpp#  
HRESULT GetCodeContext(   
   UINT64               uCodeLocationId,  
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```c#  
int GetCodeContext(   
   ulong                  uCodeLocationId,  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### パラメーター  
 `uCodeLocationId`  
 \[入力\] コード位置の識別子を指定します。  コード位置の識別子について [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) のメソッドについては" 解説 " を参照してください。  
  
 `ppCodeContext`  
 \[入力\] 関連付けられたコード [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) のコンテキストを表すオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 コード位置の識別子は呼び出しから [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md) のメソッドに戻り[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) の構造で表示できます。  
  
 コード位置の識別子にコード コンテキストを変換するには[GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) のメソッドを呼び出します。  
  
## 参照  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)   
 [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)