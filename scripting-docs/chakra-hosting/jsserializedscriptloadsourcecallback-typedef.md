---
title: "JsSerializedScriptLoadSourceCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSerializedScriptLoadSourceCallback Typedef
ランタイムによって、シリアル化されたスクリプトのソース コードを読み込むために呼び出されます。 呼び出し元では、`JsSerializedScriptUnloadCallback` までスクリプト バッファーを有効な状態に保つ必要があります。  
  
## 構文  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### パラメーター  
 `sourceContext`  
 `JsParseSerializedScriptWithCallback` または `JsRunSerializedScriptWithCallback` に渡されるコンテキスト。  
  
 `scriptBuffer`  
 返されるスクリプト。  
  
## 解説  
  
> [!WARNING]
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)