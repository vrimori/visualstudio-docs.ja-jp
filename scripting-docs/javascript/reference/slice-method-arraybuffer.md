---
title: "slice メソッド (ArrayBuffer) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# slice メソッド (ArrayBuffer)
[ArrayBuffer](../../javascript/reference/arraybuffer-object.md) の一部を返します。  
  
## 構文  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## パラメーター  
 `arrayBufferObj`  
 必ず指定します。  このセクションは [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) オブジェクトからコピーします。  
  
 `start`  
 必ず指定します。  コピーするセクションの先頭のバイト インデックス。  
  
 `end`  
 省略可能です。  コピーするセクションの末尾のバイト インデックス。  
  
## 解説  
 `slice` メソッドは、`arrayBufferObj` の指定部分を含む [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) オブジェクトを返します。  
  
 `slice` メソッドは、`end` が示す \(ただしそれに限定されない\) バイトまでコピーします。  `start` または `end` が負の場合、指定された各インデックスは `length` \+ `start` または `end` として扱われます \(ここで `length` は [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) の長さ\)。  `end` が省略されている場合は、`arrayBufferObj` の最後まで抽出を継続します。  `start` より前に `end` があると、新しい [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) にデータはコピーされません。  
  
## 使用例  
 `slice` メソッドを使用する方法の例を次に示します。  
  
```javascript  
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
  
## 必要条件  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## 参照  
 [ArrayBuffer オブジェクト](../../javascript/reference/arraybuffer-object.md)