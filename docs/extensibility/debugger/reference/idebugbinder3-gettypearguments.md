---
title: "IDebugBinder3::GetTypeArguments | Microsoft Docs"
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
  - "IDebugBinder3::GetTypeArguments"
helpviewer_keywords: 
  - "IDebugBinder3::GetTypeArguments メソッド"
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::GetTypeArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはこのオブジェクトに関連付けられている引数型リストを取得します。  
  
## 構文  
  
```cpp  
HRESULT GetTypeArguments(  
   UINT          skip,  
   UINT          count,  
   IDebugField** ppFields,  
   UINT*         pFetched  
);  
```  
  
```c#  
int GetTypeArguments(  
   uint          skip,  
   uint          count,  
   IDebugField[] ppFields,  
   out uint      pFetched  
);  
```  
  
#### パラメーター  
 `skip`  
 \[入力\] 引数の型を取得する前にこのフィールドの数。  
  
 `count`  
 \[入力\] 引数の数が戻るにはフィールド \(または `ppFields` のサイズを指定します。  
  
 `ppFields`  
 \[入力出力\] このメソッドで入力されるフィールドの配列。  
  
 `pFetched`  
 \[入力\] \(オプション\) 引数の型のフィールド数に実際に返される。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 型引数の数は [GetTypeArgumentCount](../Topic/IDebugBinder3::GetTypeArgumentCount.md) と取得できます。  
  
## 参照  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArgumentCount](../Topic/IDebugBinder3::GetTypeArgumentCount.md)