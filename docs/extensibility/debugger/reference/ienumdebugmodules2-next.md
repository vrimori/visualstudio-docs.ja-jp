---
title: "IEnumDebugModules2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugModules2::Next"
helpviewer_keywords: 
  - "IEnumDebugModules2::Next"
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugModules2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

列挙体の要素のセットを返します。  
  
## 構文  
  
```cpp#  
HRESULT Next(  
   ULONG           celt,  
   IDebugModule2** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint            celt,  
   IDebugModule2[] rgelt,  
   ref uint        pceltFetched  
);  
```  
  
#### パラメーター  
 `celt`  
 \[入力\] 取得する要素の数。  または `rgelt` の配列の最大サイズを指定します。  
  
 `rgelt`  
 \[入力出力\] 入力する [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) の要素の配列。  
  
 `pceltFetched`  
 \[出力\] 実際に `rgelt` で返される要素の数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` 要求された要素の数より少ない数を返す場合はを返します `S_FALSE` ; それ以外の場合はエラー コード。  
  
## 参照  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)