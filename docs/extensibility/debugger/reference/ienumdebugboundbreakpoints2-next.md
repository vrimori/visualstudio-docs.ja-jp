---
title: "IEnumDebugBoundBreakpoints2::Next | Microsoft Docs"
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
  - "IEnumDebugBoundBreakpoints2::Next"
helpviewer_keywords: 
  - "IEnumDebugBoundBreakpoints2::Next"
ms.assetid: cb3a249f-2282-4bdc-b6d8-a4ee4bfb8365
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugBoundBreakpoints2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

列挙体の要素のセットを返します。  
  
## 構文  
  
```cpp#  
HRESULT Next(  
   ULONG                    celt,  
   IDebugBoundBreakpoint2** rgelt,  
   ULONG*                   pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                     celt,  
   IDebugBoundBreakpoint2[] rgelt,  
   ref uint                 pceltFetched  
);  
```  
  
#### パラメーター  
 `celt`  
 \[入力\] 取得する要素の数。  または `rgelt` の配列の最大サイズを指定します。  
  
 `rgelt`  
 \[入力出力\] 入力する [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) の要素の配列。  
  
 `pceltFetched`  
 \[出力\] 実際に `rgelt` で返される要素の数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` 要求された要素の数より少ない数を返す場合はを返します `S_FALSE` ; それ以外の場合はエラー コード。  
  
## 参照  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)