---
title: "toJSON メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toJSON method
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a131c7b248ca0486ab0b3b02d40e4351136c37c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="tojson-method-date-javascript"></a>toJSON メソッド (Date) (JavaScript)
によって使用される、 [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) JavaScript Object Notation (JSON) シリアル化のため、オブジェクトのデータの変換を有効にするメソッド。  
  
## <a name="syntax"></a>構文  
  
```  
  
objectname.toJSON()  
```  
  
## <a name="parameters"></a>パラメーター  
 `objectname`  
 必須です。 どの JSON のシリアル化が必要なオブジェクトです。  
  
## <a name="remarks"></a>コメント  
 `toJSON`メソッドを使って、`JSON.stringify`関数。 `JSON.stringify`シリアル化、 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] JSON テキストの値。 場合、`toJSON`に用意されているメソッド`JSON.stringify`、`toJSON`メソッドが呼び出されます`JSON.stringify`と呼びます。  
  
 `toJSON`メソッドは、組み込みのメンバー、[日付](../../javascript/reference/date-object-javascript.md)[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクト。 UTC タイム ゾーン (サフィックス Z で示されます) を ISO 形式の日付の文字列を返します。  
  
 オーバーライドすることができます、`toJSON`のメソッド、`Date`入力するか、定義、 `toJSON` JSON のシリアル化する前に特定のオブジェクトの種類のデータの変換を実現するために他のオブジェクト型のメソッドです。  
  
## <a name="example"></a>例  
 次の例では、`toJSON`を大文字に変換された文字列メンバーの値をシリアル化するメソッド。 `toJSON`メソッドが呼び出されます`JSON.stringify`と呼びます。  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`toJSON`の組み込みメンバーであるメソッド、[日付](../../javascript/reference/date-object-javascript.md)オブジェクト。  
  
```JavaScript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]**に適用されます:** [オブジェクトの日付](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [JSON オブジェクト](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse 関数](../../javascript/reference/json-parse-function-javascript.md)   
 [JSON.stringify 関数](../../javascript/reference/json-stringify-function-javascript.md)   
 [JavaScript メソッド](../../javascript/reference/javascript-methods.md)