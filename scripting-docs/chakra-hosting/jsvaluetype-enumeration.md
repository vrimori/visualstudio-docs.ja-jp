---
title: "JsValueType 列挙型 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsValueType
helpviewer_keywords:
- JsValueType enumeration
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df4f61cf9118c19a0fc35e7505af422b812d0b43
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="jsvaluetype-enumeration"></a>JsValueType 列挙型
JsValueRef の JavaScript の型。  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="members"></a>メンバー  
  
### <a name="values"></a>値  
  
|名前|説明|  
|----------|-----------------|  
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
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)