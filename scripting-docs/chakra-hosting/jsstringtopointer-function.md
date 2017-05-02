---
title: "JsStringToPointer 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStringToPointer"
helpviewer_keywords: 
  - "JsStringToPointer 関数"
ms.assetid: c7aa7a09-489d-4435-8f8a-aeb62f8875ae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsStringToPointer 関数
文字列値の文字列ポインターを取得します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsStringToPointer(  
   _In_ JsValueRef value,  
   _Outptr_result_buffer_(*stringLength) const wchar_t **stringValue,  
   _Out_ size_t *stringLength  
);  
```  
  
#### パラメーター  
 `value`  
 文字列ポインターに変換する文字列値。  
  
 `stringValue`  
 文字列ポインター。  
  
 `stringLength`  
 文字列の長さ。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 この関数は、文字列値の文字列ポインターを取得します。  値の型が文字列でない場合は、`JsErrorInvalidArgument` で失敗します。  返される文字列の有効期間は、取得元の値の有効期間と同じになりますが、文字列ポインターはその値への参照とは見なされません \(したがって、継続的な収集は行われません\)。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)