---
title: "subarray メソッド (Float32Array) | Microsoft Docs"
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
ms.assetid: 97aa27c0-d650-411e-b929-dd9c4a2ae9a5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# subarray メソッド (Float32Array)
サブ配列の最初と最後のメンバーを指定して、この配列の [ArrayBuffer オブジェクト](../../javascript/reference/arraybuffer-object.md) ストアの新しい Float32Array ビューを取得します。  
  
## 構文  
  
```javascript  
var newFloat32Array = float32Array.subarray(begin, end);  
```  
  
## Parameters  
 `newFloat32Array`  
 The subarray returned by this method.  
  
 `begin`  
 The index of the beginning of the array.  
  
 `end`  
 The index of the end of the array.  
  
## 解説  
 If either `begin` or `end` is negative, it refers to an index from the end of the array, as opposed to from the beginning.  If `end` is unspecified, the subarray contains all elements from `begin` to the end of the typed array.  The range specified by the `begin` and `end` values is clamped to the valid index range for the current array.  If the computed length of the new typed array would be negative, it is clamped to zero.  The returned array is of the same type as the array on which this method is invoked.  
  
## 使用例  
 The following example shows how to get a subarray three elements long, starting with the first element of the array.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var floatArr = new Float32Array(buffer.byteLength / 4);  
            var subArr = floatArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]