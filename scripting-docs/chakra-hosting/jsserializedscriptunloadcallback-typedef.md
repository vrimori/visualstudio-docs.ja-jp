---
title: "JsSerializedScriptUnloadCallback typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSerializedScriptUnloadCallback typedef
スクリプトの実行に関連するリソースがすべて終了したときに、ランタイムによって呼び出されます。 この時点で、呼び出し元はソース \(読み込まれている場合\)、バイト コード、およびコンテキストを解放する必要があります。  
  
## 構文  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### パラメーター  
 `sourceContext`  
 `JsParseSerializedScriptWithCallback` または `JsRunSerializedScriptWithCallback` に渡されるコンテキスト。  
  
## 解説  
  
> [!WARNING]
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)