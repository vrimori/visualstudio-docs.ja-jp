---
title: "IEnumDebugReferenceInfo2::Next | Microsoft Docs"
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
  - "IEnumDebugReferenceInfo2::Next"
helpviewer_keywords: 
  - "IEnumDebugReferenceInfo2::Next"
ms.assetid: 70b31a57-1701-4757-9e7e-63ec60a71b3c
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugReferenceInfo2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

列挙体の要素のセットを返します。  
  
## 構文  
  
```cpp#  
HRESULT Next(  
   ULONG                   celt,  
   DEBUG_REFERENCE_INFO ** rgelt,  
   ULONG*                  pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                   celt,  
   DEBUG_REFERENCE_INFO[] rgelt,  
   ref uint               pceltFetched  
);  
```  
  
#### パラメーター  
 `celt`  
 \[入力\] 取得する要素の数。  または `rgelt` の配列の最大サイズを指定します。  
  
 `rgelt`  
 \[入力出力\] 入力する [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) の要素の配列。  
  
 `pceltFetched`  
 \[出力\] 実際に `rgelt` で返される要素の数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` 要求された要素の数より少ない数を返す場合はを返します `S_FALSE` ; それ以外の場合はエラー コード。  
  
## 参照  
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)