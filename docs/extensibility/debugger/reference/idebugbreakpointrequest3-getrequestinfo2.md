---
title: "IDebugBreakpointRequest3::GetRequestInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest3::GetRequestInfo2"
helpviewer_keywords: 
  - "IDebugBreakpointRequest3::GetRequestInfo2"
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugBreakpointRequest3::GetRequestInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはブレークポイントの要求を記述したブレークポイントの要求された情報を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetRequestInfo2(  
   BPREQI_FIELDS      dwFields,  
   BP_REQUEST_INFO2*  bBPRequestInfo  
);  
```  
  
```c#  
int GetRequestInfo2(  
   enum_BPREQI_FIELDS  dwFields,   
   BP_REQUEST_INFO2[]  bBPRequestInfo  
);  
```  
  
#### パラメーター  
 `dwFields`  
 \[入力\] `pBPRequestInfo` のフィールドが設定する方法を決定 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) の列挙体のフラグの組み合わせ。  
  
 `bBPRequestInfo`  
 \[入力\] 入力する [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) の構造体。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) のメソッドから返されるこの要求に詳細があります。  
  
## 参照  
 [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)