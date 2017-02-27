---
title: "IEnumDebugPropertyInfo2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPropertyInfo2::Next"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2::Next"
ms.assetid: 4eb8c7c3-aadf-4187-abee-c0620308a3eb
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugPropertyInfo2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

列挙体の要素のセットを返します。  
  
## 構文  
  
```cpp#  
HRESULT Next(  
   ULONG                 celt,  
   DEBUG_PROPERTY_INFO** rgelt,  
   ULONG*                pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                  celt,  
   DEBUG_PROPERTY_INFO[] rgelt,  
   ref uint              pceltFetched  
);  
```  
  
#### パラメーター  
 `celt`  
 \[入力\] 取得する要素の数。  または `rgelt` の配列の最大サイズを指定します。  
  
 `rgelt`  
 \[入力出力\] 入力する [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) の要素の配列。  
  
 `pceltFetched`  
 \[出力\] 実際に `rgelt` で返される要素の数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` 要求された要素の数より少ない数を返す場合はを返します `S_FALSE` ; それ以外の場合はエラー コード。  
  
## 参照  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)