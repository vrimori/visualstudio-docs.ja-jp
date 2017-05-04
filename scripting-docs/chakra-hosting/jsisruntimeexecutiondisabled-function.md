---
title: "JsIsRuntimeExecutionDisabled 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIsRuntimeExecutionDisabled"
helpviewer_keywords: 
  - "JsIsRuntimeExecutionDisabled 関数"
ms.assetid: 77490280-fb84-4614-a1f0-6ac31e3bd607
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsIsRuntimeExecutionDisabled 関数
ランタイムでスクリプト実行が無効であるかどうかを示す値を返します。  
  
## 構文  
  
```vb  
STDAPI_(JsErrorCode) JsIsRuntimeExecutionDisabled(  
    _In_ JsRuntimeHandle runtime,  
    _Out_ bool *isDisabled  
);  
```  
  
#### パラメーター  
 `runtime`  
 実行が無効であるかどうかをチェックするようにランタイムに指示します。  
  
 `isDisabled`  
 実行が無効な場合は `true`、それ以外の場合は `false`。  
  
## 戻り値  
 操作が成功した場合は `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)