---
title: "IDebugProcess3::GetEngineFilter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetEngineFilter"
  - "IDebugProcess3::GetEngineFilter"
ms.assetid: ccb7ecb0-f189-4e80-b5b2-221a095e01f5
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProcess3::GetEngineFilter
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

使用可能なデバッグ エンジンの一意の識別子の配列を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetEngineFilter(  
   GUID_ARRAY *pEngineArray  
);  
```  
  
```c#  
public int GetEngineFilter(  
   out GUID_ARRAY[] pEngineArray  
);  
```  
  
#### パラメーター  
 `pEngineArray`  
 \[入力\] デバッグ エンジンの一意の識別子を格納する構造体への参照。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [GUID\_ARRAY](../../../extensibility/debugger/reference/guid-array.md)