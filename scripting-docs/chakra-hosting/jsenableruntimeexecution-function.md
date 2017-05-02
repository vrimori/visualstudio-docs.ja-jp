---
title: "JsEnableRuntimeExecution 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsEnableRuntimeExecution"
helpviewer_keywords: 
  - "JsEnableRuntimeExecution 関数"
ms.assetid: daa2036b-aef6-497d-a8ce-5a006b6ed13f
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsEnableRuntimeExecution 関数
ランタイムのスクリプトの実行を有効にします。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsEnableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### パラメーター  
 `runtime`  
 有効にするランタイム。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 スクリプト実行が既に有効であるランタイム内でスクリプト実行を有効にしても、何も行われません。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)