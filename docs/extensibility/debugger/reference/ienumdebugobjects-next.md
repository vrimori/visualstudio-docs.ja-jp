---
title: "IEnumDebugObjects::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugObjects::Next"
helpviewer_keywords: 
  - "IEnumDebugObjects::Next メソッド"
ms.assetid: e54c3055-6030-4dc9-9f7a-5e3ce75f252f
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugObjects::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドは列挙体の要素のセット。  
  
## 構文  
  
```cpp#  
HRESULT Next(  
   ULONG          celt,  
   IDebugObject** rgelt,  
   ULONG*         pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint           celt,  
   IDebugObject[] rgelt,  
   ref uint       pceltFetched  
);  
```  
  
#### パラメーター  
 `celt`  
 \[入力\] 取得する要素の数。  または `rgelt` の配列の最大サイズを指定します。  
  
 `rgelt`  
 \[入力出力\] 入力する [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) の要素の配列。  
  
 `pceltFetched`  
 \[出力\] 実際に `rgelt` で返される要素の数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` 要求された要素の数より少ない数を返す場合はを返します `S_FALSE` ; それ以外の場合はエラー コード。  
  
## 参照  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)