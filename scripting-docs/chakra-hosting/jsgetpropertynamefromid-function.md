---
title: "JsGetPropertyNameFromId 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetPropertyNameFromId"
helpviewer_keywords: 
  - "JsGetPropertyNameFromId 関数"
ms.assetid: b4ca442c-573d-4bc3-adf7-1b8d48480b3a
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetPropertyNameFromId 関数
プロパティ ID に関連付けられた名前を取得します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyNameFromId(  
   _In_ JsPropertyIdRef propertyId,  
   _Outptr_result_z_ const wchar_t **name  
);  
```  
  
#### パラメーター  
 `propertyId`  
 名前を取得するプロパティ ID。  
  
 `name`  
 プロパティ ID に関連付けられた名前。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 アクティブ スクリプトのコンテキストが必要です。  
  
 返されたバッファーは、ランタイムがアクティブである限り有効であり、ランタイムの破棄後には使用できません。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)