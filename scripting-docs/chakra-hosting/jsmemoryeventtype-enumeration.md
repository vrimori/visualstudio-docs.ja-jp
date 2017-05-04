---
title: "JsMemoryEventType 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsMemoryEventType"
helpviewer_keywords: 
  - "JsMemoryEventType 列挙型"
ms.assetid: b4b176b6-b536-472e-8999-95b681a1df55
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsMemoryEventType 列挙型
割り当てコールバックのイベントの種類。  
  
## 構文  
  
```  
enum JsMemoryEventType;  
```  
  
## メンバー  
  
### 値  
  
|名前|説明|  
|--------|--------|  
|`JsMemoryAllocate`|メモリ割り当ての要求を示します。|  
|`JsMemoryFailure`|失敗した割り当てイベントを示します。|  
|`JsMemoryFree`|メモリ解放イベントを示します。|  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)