---
title: "JsCreateDataView 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 161e59eb-d429-46f7-9a38-bbf2149ccf44
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsCreateDataView 関数
Javascript `DataView` オブジェクトを作成します。  
  
## 構文  
  
```  
JsErrorCode  JsCreateDataView(  
   _In_ JsValueRef arrayBuffer,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int byteLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### パラメーター  
 `arrayBuffer`  
 結果の `DataView` オブジェクトのストレージとして使用する既存の `ArrayBuffer` オブジェクト。  
  
 `byteOffset`  
 参照する結果 `DataView` の `arrayBuffer` の先頭からのオフセット \(バイト単位\)。  
  
 `byteLength`  
 参照する結果 DataView の ArrayBuffer のバイト数。  
  
 `result`  
 新しい DataView オブジェクト。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 アクティブ スクリプトのコンテキストが必要です。  
  
 この API は、エッジ モードでのみサポートされます。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)