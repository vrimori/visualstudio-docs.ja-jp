---
title: "slice メソッド (ArrayBuffer) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25fc10a02b4a3422a6720ad91c8bba29906da0e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-arraybuffer"></a>slice メソッド (ArrayBuffer)
一部を返します、 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>パラメーター  
 `arrayBufferObj`  
 必須です。 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)セクションはからコピーされるオブジェクト。  
  
 `start`  
 必須です。 コピーするセクションの先頭のバイト インデックス。  
  
 `end`  
 省略可能です。 コピーするセクションの末尾のバイト インデックス。  
  
## <a name="remarks"></a>コメント  
 `slice`メソッドを返します、 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)の指定部分を格納しているオブジェクト`arrayBufferObj`です。  
  
 `slice` メソッドは、`end` が示す (ただしそれに限定されない) バイトまでコピーします。 場合`start`または`end`は負の場合、指定したインデックスとして扱われます`length`  +  `start`または`end`をそれぞれ、`length`の長さ、 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md). `end` が省略されている場合は、`arrayBufferObj` の最後まで抽出を継続します。 場合`end`の前に発生`start`を新しいデータはコピーされません[ArrayBuffer](../../javascript/reference/arraybuffer-object.md)です。  
  
## <a name="example"></a>例  
 `slice` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ArrayBuffer オブジェクト](../../javascript/reference/arraybuffer-object.md)