---
title: "IDebugPointerObject3::GetPointerAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetPointerAddress"
  - "IDebugPointerObject3::GetPointerAddress"
ms.assetid: 4cc5af04-9e70-420d-8230-ef3108df6d51
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPointerObject3::GetPointerAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ポインター アドレスを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetPointerAddress (  
   UINT64* puAddress  
);  
```  
  
```c#  
int GetPointerAddress (  
   out ulong puAddress  
);  
```  
  
#### パラメーター  
 `puAddress`  
 \[出力\] ポインターのアドレスを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)