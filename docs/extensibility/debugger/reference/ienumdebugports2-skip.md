---
title: "IEnumDebugPorts2::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPorts2::Skip"
helpviewer_keywords: 
  - "IEnumDebugPorts2::Skip"
ms.assetid: a837383f-7b39-4e06-b336-f1715b073dbe
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugPorts2::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定した数の要素をスキップします。  
  
## 構文  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### パラメーター  
 `celt`  
 \[入力\] スキップする要素の数。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` `celt` の残りの要素の数を超える場合はを返します `S_FALSE` ; それ以外の場合はエラー コード。  
  
## 解説  
 `celt` の残りの要素数を超える値を指定する列挙体が最後に`S_FALSE` が返されます。  
  
## 参照  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)