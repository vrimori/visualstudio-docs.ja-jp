---
title: "IDebugCoreServer2::GetPortSupplier | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2::GetPortSupplier"
helpviewer_keywords: 
  - "IDebugCoreServer2::GetPortSupplier"
ms.assetid: acf181d4-ef42-4aa5-86f9-95fd5467ea31
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCoreServer2::GetPortSupplier
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

特定のポートの業者を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetPortSupplier(   
   REFGUID               guidPortSupplier,  
   IDebugPortSupplier2** ppPortSupplier  
);  
```  
  
```c#  
int GetPortSupplier(   
   ref Guid                guidPortSupplier,  
   out IDebugPortSupplier2 ppPortSupplier  
);  
```  
  
#### パラメーター  
 `guidPortSupplier`  
 \[出力\] 取得されたポートのサプライヤーの GUID。  
  
 `ppPortSupplier`  
 \[入力\] [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) に目的のポートのサプライヤーを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)