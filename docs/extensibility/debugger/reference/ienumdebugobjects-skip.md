---
title: "IEnumDebugObjects::Skip | Microsoft Docs"
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
  - "IEnumDebugObjects::Skip"
helpviewer_keywords: 
  - "IEnumDebugObjects::Skip メソッド"
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugObjects::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドは指定された数の要素がスキップされます。  
  
## 構文  
  
```cpp#  
HRESULT Skip(  
   [in] ULONG celt  
);  
```  
  
```c#  
int Skip(  
   [In] uint celt  
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
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)