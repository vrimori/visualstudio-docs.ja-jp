---
title: "IDebugField::Equal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::Equal"
helpviewer_keywords: 
  - "IDebugField::Equal メソッド"
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::Equal
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはで指定されたフィールドにこのフィールドを比較します。  
  
## 構文  
  
```cpp#  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```c#  
int Equal(  
   IDebugField pField  
);  
```  
  
#### パラメーター  
 `pField`  
 \[出力\] この 1 と比較するフィールド。  
  
## 戻り値  
 フィールドが同じである場合戻り `S_OK`。  フィールドが異なる場合はそれ以外の場合はエラー コードを返します `S_FALSE.`。  
  
## 参照  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)