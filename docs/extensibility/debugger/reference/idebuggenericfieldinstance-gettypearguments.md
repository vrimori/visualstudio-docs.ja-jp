---
title: "IDebugGenericFieldInstance::GetTypeArguments | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetTypeArguments"
  - "IDebugGenericFieldInstance::GetTypeArguments"
ms.assetid: 6e7e0f95-181a-4805-adb3-c2407de0ab93
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugGenericFieldInstance::GetTypeArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインスタンスの型パラメーターの引数を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetTypeArguments(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   ULONG32*      pcArgs  
);  
```  
  
```c#  
int GetTypeArguments(  
   uint              cArgs,  
   out IDebugField[] ppArgs,  
   ref uint          pcArgs  
);  
```  
  
#### パラメーター  
 `cArgs`  
 \[入力\] 型パラメーターの数。  
  
 `ppArgs`  
 \[入力\] 型パラメーターの配列を返します。  
  
 `pcArgs`  
 \[入力出力\] `ppArgs` の配列のメンバーの数。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)