---
title: "JsMemoryAllocationCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# JsMemoryAllocationCallback Typedef
メモリ割り当てイベントに対してユーザーによって実装されたコールバック ルーチン。  
  
## 構文  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### パラメーター  
 callbackState  
 JsSetRuntimeMemoryAllocationCallback に渡される状態。  
  
 allocationEvent  
 型割り当てイベントの種類。  
  
 allocationSize  
 割り当てのサイズ。  
  
## プロパティ値\/戻り値  
 JsMemoryAllocate イベントでは、true を返すことにより、ランタイムの割り当てを続行できます。  false を返すと、割り当て要求が拒否されることを示します。  戻り値は、他の割り当てイベントでは無視されます。  
  
## 解説  
 このコールバックを登録するには、JsSetRuntimeMemoryAllocationCallback を使用します。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)