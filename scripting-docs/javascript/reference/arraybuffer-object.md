---
title: "ArrayBuffer オブジェクト | Microsoft Docs"
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# ArrayBuffer オブジェクト
さまざまな型指定された配列のデータを格納するために使用されるバイナリ データの生バッファーを表します。  `ArrayBuffers` を直接読み書きすることはできませんが、必要に応じて、型指定された配列または [DataView オブジェクト](../../javascript/reference/dataview-object.md) に渡して生バッファーを解釈することができます。  
  
 型指定された配列の詳細については、「[型指定された配列](../../javascript/advanced/typed-arrays-javascript.md)」を参照してください。  
  
## 構文  
  
```javascript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## パラメーター  
 `arrayBuffer`  
 必ず指定します。  `ArrayBuffer` オブジェクトを代入する変数名を指定します。  
  
 `length`  
 バッファーの長さを指定します。  ArrayBuffer の内容は 0 に初期化されます。  要求されたバイト数を割り当てることができなかった場合に例外が発生します。  
  
## プロパティ  
 `ArrayBuffer` オブジェクトのプロパティを次の表に示します。  
  
|プロパティ|説明|  
|-----------|--------|  
|[byteLength プロパティ](../../javascript/reference/bytelength-property-arraybuffer.md)|読み取り専用です。  ArrayBuffer の長さ \(バイト単位\)。|  
  
## 関数  
 `ArrayBuffer` オブジェクトの関数を次の表に示します。  
  
|プロパティ|説明|  
|-----------|--------|  
|[ArrayBuffer.isView Function](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|オブジェクトがバッファーのビューを提供するかどうかを決定します。|  
  
## メソッド  
 `ArrayBuffer` オブジェクトのメソッドを次の表に示します。  
  
|プロパティ|説明|  
|-----------|--------|  
|[slice メソッド](../../javascript/reference/slice-method-arraybuffer.md)|`ArrayBuffer` の一部を返します。|  
  
## 使用例  
 次の例は、[XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx) から取得したバイナリ データを処理する ArrayBuffer オブジェクトの使用方法を示します。  個々の値を取得するには、[DataView オブジェクト](../../javascript/reference/dataview-object.md) を使用できます。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## 解説  
 `XmlHttpRequest` の使い方の詳細については、「[XMLHttpRequest enhancements](http://msdn.microsoft.com/ja-jp/be09137c-6546-441b-b953-dcbf72b77069)」を参照してください。  
  
## 必要条件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]