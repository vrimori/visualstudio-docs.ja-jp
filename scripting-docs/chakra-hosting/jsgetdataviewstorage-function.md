---
title: "JsGetDataViewStorage 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 7c2180e0-51d5-4cc8-ad21-8bf29ff7c583
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsGetDataViewStorage 関数
`DataView` によって使用される、基になるメモリ ストレージを取得します。  
  
## 構文  
  
```cpp  
STDAPI_(JsErrorCode) JsGetDataViewStorage(  
   _In_ JsValueRef dataView,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength  
);  
```  
  
#### パラメーター  
 `dataView`  
 DataView インスタンスです。  
  
 `buffer`  
 DataView のバッファーです。  返されるバッファーの有効期間は、`DataView` の有効期間と同じです。  バッファー ポインターは、ガベージ コレクションのための `DataView` への参照としてはカウントされません。  
  
 `bufferLength`  
 バッファー内のバイト数。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 アクティブ スクリプトのコンテキストが必要です。  
  
 この API は、エッジ モードでのみサポートされます。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)