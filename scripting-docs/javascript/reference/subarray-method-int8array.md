---
title: "subarray メソッド (Int8Array) | Microsoft Docs"
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
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# subarray メソッド (Int8Array)
この配列の ArrayBuffer ストアの新しい Int8Array ビューを取得します。begin から end まで \(begin は含まれますが、end は含まれません\) の要素を参照します。  
  
## 構文  
  
```javascript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## パラメーター  
 `newInt8Array`  
 このメソッドで返されるサブ配列。  
  
 `begin`  
 配列の先頭のインデックス。  
  
 `end`  
 配列の末尾のインデックス。  これは、内包的ではありません。  
  
## 解説  
 begin または end が負の場合は、配列の先頭からではなく、配列の末尾からのインデックスを参照します。  end が指定されていない場合、サブ配列には、TypedArray の先頭から末尾までのすべての要素が含まれます。  開始値および終了値で指定された範囲は、現在の配列の有効なインデックスの範囲に固定されます。  新しい TypedArray の計算された長さが負となる場合は、ゼロに固定されます。  返される TypedArray は、このメソッドが呼び出される配列と同じ型になります。  
  
## 使用例  
 次の例は、配列の先頭の要素から開始して、長さが要素 2 つ分のサブ配列を取得する方法を示しています。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]