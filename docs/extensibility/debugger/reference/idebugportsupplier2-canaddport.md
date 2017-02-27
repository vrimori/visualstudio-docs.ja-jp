---
title: "IDebugPortSupplier2::CanAddPort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::CanAddPort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::CanAddPort"
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortSupplier2::CanAddPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ポートのサプライヤーが新しいポートを追加できるようにします。  
  
## 構文  
  
```cpp#  
HRESULT CanAddPort(   
   void   
);  
```  
  
```c#  
int CanAddPort();  
```  
  
## 戻り値  
 ポートを追加できる場合はを返します `S_OK`; それ以外のポートを示す戻り `S_FALSE` はこのポートのサプライヤーに追加できます。  
  
## 解説  
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) のメソッドを呼び出す前にこのメソッドを呼び出した後のメソッドがポートを作成しまた時間のかかる操作で使用できる追加します。  
  
## 参照  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)