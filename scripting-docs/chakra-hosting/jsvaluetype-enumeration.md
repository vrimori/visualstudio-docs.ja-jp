---
title: "JsValueType 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueType"
helpviewer_keywords: 
  - "JsValueType 列挙型"
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# JsValueType 列挙型
JsValueRef の JavaScript の型。  
  
## 構文  
  
```  
enum JsValueType {  
    JsUndefined      = 0,  
    JsNull           = 1,  
    JsNumber         = 2,  
    JsString         = 3,  
    JsBoolean        = 4,  
    JsObject         = 5,  
    JsFunction       = 6,  
    JsError          = 7,  
    JsArray          = 8,  
    JsSymbol         = 9,  
    JsArrayBuffer    = 10,  
    JsTypedArray     = 11,  
    JsDataView       = 12,  
};  
```  
  
## メンバー  
  
### 値  
  
|名前|説明|  
|--------|--------|  
|`JsUndefined`|値は、`undefined` 値です。|  
|`JsNull`|値は、`null` 値です。|  
|`JsNumber`|値は、JavaScript 数値です。|  
|`JsString`|値は、JavaScript 文字列値です。|  
|`JsBoolean`|値は、JavaScript ブール値です。|  
|`JsObject`|値は、JavaScript オブジェクト値です。|  
|`JsFunction`|値は、JavaScript 関数オブジェクト値です。|  
|`JsError`|値は、JavaScript エラー オブジェクト値です。|  
|`JsArray`|値は、JavaScript 配列オブジェクト値です。|  
|`JsSymbol`|値は、JavaScript シンボル値です。<br /><br /> この列挙値は、エッジ モードでのみサポートされています。|  
|`JsArrayBuffer`|値は、JavaScript `ArrayBuffer` オブジェクト値です。<br /><br /> この列挙値は、エッジ モードでのみサポートされています。|  
|`JsTypedArray`|値は、型指定された JavaScript 配列オブジェクト値です。<br /><br /> この列挙値は、エッジ モードでのみサポートされています。|  
|`JsDataView`|値は、JavaScript `DataView` オブジェクト値です。<br /><br /> この列挙値は、エッジ モードでのみサポートされています。|  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)