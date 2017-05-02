---
title: "set メソッド (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: 1298443d-5c4c-4329-9ad2-35e213dca157
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# set メソッド (Uint8ClampedArray)
値または値の配列を設定します。  
  
## 構文  
  
```javascript  
uint8ClampedArray.set(index, value); uint8ClampedArray.set(array, offset);   
```  
  
## パラメーター  
 `index`  
 設定する位置のインデックス。  
  
 `value`  
 設定する値。  
  
 `array`  
 設定する値の型指定された配列、または型指定されていない配列。  
  
 `offset`  
 現在の配列内で値が書き込まれる位置のインデックス。  
  
## 解説  
 入力配列が、型指定された配列の場合、2 種類の配列で基になる [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) は同一のものが使用されることがあります。  この場合は、すべてのデータが最初にどちらの配列とも重複しない一時バッファーにコピーされ、そこからデータが現在の配列にコピーされたかのように値が設定されます。  
  
 オフセットと指定された配列の長さを加算すると現在の型指定された配列の範囲外になる場合は、例外が発生します。  
  
## 使用例  
 次の例は、配列の先頭の要素の設定方法を示します。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## 参照  
 [ArrayBuffer オブジェクト](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray オブジェクト](../../javascript/reference/uint8clampedarray-object-javascript.md)