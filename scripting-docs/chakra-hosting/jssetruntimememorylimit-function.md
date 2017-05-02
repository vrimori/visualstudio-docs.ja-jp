---
title: "JsSetRuntimeMemoryLimit 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeMemoryLimit"
helpviewer_keywords: 
  - "JsSetRuntimeMemoryLimit 関数"
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetRuntimeMemoryLimit 関数
ランタイムの現在のメモリ制限を設定します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### パラメーター  
 `runtime`  
 メモリ制限を設定するランタイム。  
  
 `memoryLimit`  
 新しいランタイム メモリ制限 \(バイト\)、またはメモリ制限がない場合は \-1。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 メモリ制限により、該当する制限を超えるすべての操作が「メモリ不足」エラーにより失敗します。  ランタイムのメモリ制限に \-1 を設定すると、ランタイムにメモリ制限がないことを示します。  既定では新しいランタイムにメモリ制限はありません。  新しいメモリ制限が現在の使用量を上回る場合、呼び出しは成功します。以降このランタイムの割り当ては、ランタイムのメモリ使用量が制限以下に低下するまで失敗します。  
  
 ランタイムのメモリ制限は、別のスレッドでランタイムがアクティブであるかどうかにかかわらず、常に設定できます。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)