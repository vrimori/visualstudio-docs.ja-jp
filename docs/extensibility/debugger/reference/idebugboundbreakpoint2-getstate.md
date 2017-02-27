---
title: "IDebugBoundBreakpoint2::GetState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::GetState"
helpviewer_keywords: 
  - "GetState メソッド"
  - "IDebugBoundBreakpoint2::GetState メソッド"
ms.assetid: a40a8382-295e-4916-aae6-ffe3a9cd3f2d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBoundBreakpoint2::GetState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このの状態を割り当てられたブレークポイントを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetState(   
   BP_STATE* pState  
);  
```  
  
```c#  
int GetState(   
   out enum_BP_STATE pState  
);  
```  
  
#### パラメーター  
 `pState`  
 \[出力\] ブレークポイントの状態を示す [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) の列挙型の値を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 使用例  
 次の例に [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) インターフェイスを公開する `CBoundBreakpoint` の単純なオブジェクトに対してこのメソッドを実装する方法を示します。  
  
```  
HRESULT CBoundBreakpoint::GetState(BP_STATE* pState)    
{    
   HRESULT hr;    
  
   // Check for a valid pointer to pState and assign the local state variable.    
   if (pState)    
   {    
      *pState = m_state;    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## 参照  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)