---
title: "JsNativeFunction Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsNativeFunction Typedef
関数コールバック。  
  
## 構文  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### パラメーター  
 呼び出し先  
 呼び出されている関数を表す `Function` オブジェクト。  
  
 isConstructCall  
 これが通常の呼び出しまたは "新しい" 呼び出しのいずれであるかを示します。  
  
 引数  
 呼び出しの引数。  
  
 argumentCount  
 引数の数。  
  
## プロパティ値\/戻り値  
 呼び出しの結果 \(存在する場合\)。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)