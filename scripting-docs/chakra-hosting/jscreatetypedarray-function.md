---
title: "JsCreateTypedArray 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 937a2a91-6f5f-4aaa-a018-d3089702bf36
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsCreateTypedArray 関数
型指定された Javascript 配列オブジェクトを作成します。  
  
## 構文  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateTypedArray(  
   _In_ JsTypedArrayType arrayType,  
   _In_ JsValueRef baseArray,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int elementLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### パラメーター  
 `arrayType`  
 作成する配列の型。  
  
 `baseArray`  
 新しい配列の基本の配列です。  基本の配列がない場合は、`JS_INVALID_REFERENCE` を使用します。  
  
 `byteOffset`  
 参照する結果の型指定された配列の `baseArray` \(`ArrayBuffer`\) の先頭からのオフセット \(バイト単位\)。  `baseArray` が `ArrayBuffer` オブジェクトの場合にのみ適用されます。  それ以外の場合は 0 にする必要があります。  
  
 `elementLength`  
 配列の要素数。  `baseArray` を含まない型指定された新しい配列 \(`baseArray` は `JS_INVALID_REFERENCE`\) を作成する場合、または `baseArray` が `ArrayBuffer` オブジェクトの場合のみ適用されます。  それ以外の場合は 0 にする必要があります。  
  
 `result`  
 型指定された新しい配列のオブジェクト。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 `baseArray` には、`ArrayBuffer`、別の型指定された配列、または JavaScript `Array` を指定できます。  `ArrayBuffer` の場合、返された型指定された配列は `baseArray` を使用します。それ以外の場合は、基になるソース配列のコピーを作成および使用します。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
 この API は、エッジ モードでのみサポートされます。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)