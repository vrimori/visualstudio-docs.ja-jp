---
title: "JsRunSerializedScript 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsRunSerializedScript"
helpviewer_keywords: 
  - "JsRunSerializedScript 関数"
ms.assetid: 3fd3f6f1-eb3e-4751-92a5-c93b1035f3b2
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsRunSerializedScript 関数
シリアル化されたスクリプトを実行します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScript(  
   _In_z_ const wchar_t *script,  
   _In_ BYTE *buffer,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### パラメーター  
 `script`  
 シリアル化されたスクリプトのソース コード。  
  
 `buffer`  
 シリアル化されたスクリプト。  
  
 `sourceContext`  
 デバッグ可能なスクリプト コンテキストで使用できるスクリプトを識別するクッキー。  
  
 `sourceUrl`  
 スクリプトの元の場所。  
  
 `result`  
 スクリプトを実行した結果 \(存在する場合\)。  このパラメーターには、null を指定できます。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 アクティブ スクリプトのコンテキストが必要です。  
  
 バッファーはスクリプト エンジンによってメモリ内に保持されません。スクリプトの実行に使用される可能性がある限り、コードはバッファーを維持する必要があります。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)