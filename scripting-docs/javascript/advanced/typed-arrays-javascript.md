---
title: "型指定された配列 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: fa82c562-0ebf-4559-aecc-166e59f7fb64
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# 型指定された配列 (JavaScript)
ネットワーク プロトコル、バイナリ ファイル形式、生のグラフィックス バッファーなどのソースからバイナリ データを処理するための型指定された配列を使用できます。  型指定された配列は、既知のバイト レイアウトのメモリ内バイナリ データの管理のために使用することもできます。  
  
## 例  
 次のコードは、[ArrayBuffer オブジェクト](../../javascript/reference/arraybuffer-object.md)を [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx) の応答として使用する方法を示しています。  [DataView オブジェクト](../../javascript/reference/dataview-object.md)の異なるメソッドを使用するか、バイトを適切な型指定された配列にコピーして、応答内のバイトを操作できます。  
  
> [!TIP]
>  `XmlHttpRequest` でさまざまな応答タイプを使用する方法について詳しくは、[XMLHttpRequest.responseType](http://msdn.microsoft.com/ja-jp/8d7738d1-4bfd-4cf1-8015-174def089556)、[XMLHttpRequest enhancements](http://msdn.microsoft.com/ja-jp/be09137c-6546-441b-b953-dcbf72b77069)、および [さまざまな種類のコンテンツのダウンロード \(Windows ストア アプリ\)](http://msdn.microsoft.com/ja-jp/c0006bbd-17f9-4c6a-af81-2acaf109111d) を参照してください。  
  
```javascript  
...  
<div id="xhrDiv"></div>  
...  
var name = "http://www.microsoft.com";  
var xhrDiv = document.getElementById("xhrDiv");  
  
var req = new XMLHttpRequest();  
req.open("GET", name, true);  
req.responseType = "arraybuffer";  
req.onreadystatechange = function () {  
if (req.readyState == req.DONE) {  
    var arrayResponse = req.response;  
    var dataView = new DataView(arrayResponse);  
    var ints = new Uint32Array(dataView.byteLength / 4);  
  
    xhrDiv.style.backgroundColor = "#00FF00";  
    xhrDiv.innerText = "Array is " + ints.length + "uints long";  
    }  
}  
req.send();  
```  
  
## ArrayBuffer  
 [ArrayBuffer オブジェクト](../../javascript/reference/arraybuffer-object.md)は、型指定されたさまざまな配列のデータを格納するために使用する生データのバッファーを表します。  `ArrayBuffer` に対して読み取りまたは書き込みを実行することはできませんが、型指定された配列または [DataView オブジェクト](../../javascript/reference/dataview-object.md) にこのオブジェクトを渡して生バッファーを解釈することができます。  `ArrayBuffer` を使用して、任意の種類のデータ \(または混合型のデータ\) を格納できます。  
  
## DataView  
 [DataView オブジェクト](../../javascript/reference/dataview-object.md)を使用すると、`ArrayBuffer` 内の任意の場所でさまざまな種類のバイナリ データを読み書きできます。  
  
## 型指定された配列  
 型指定された配列の型は、インデックスを付けて操作できる [ArrayBuffer オブジェクト](../../javascript/reference/arraybuffer-object.md)のビューを表します。  配列のすべての型は固定長です。  
  
||||  
|-|-|-|  
|名前|サイズ \(バイト単位\)|説明|  
|[Int8Array オブジェクト](../../javascript/reference/int8array-object.md)|1|8 ビット、2 の補数の符号付き整数|  
|[Uint8Array オブジェクト](../../javascript/reference/uint8array-object.md)|1|8 ビット符号なし整数|  
|[Int16Array オブジェクト](../../javascript/reference/int16array-object.md)|2|16 ビット、2 の補数の符号付き整数|  
|[Uint16Array オブジェクト](../../javascript/reference/uint16array-object.md)|2|16 ビット符号なし整数|  
|[Int32Array オブジェクト](../../javascript/reference/int32array-object.md)|4|32 ビット、2 の補数の符号付き整数|  
|[Uint32Array オブジェクト](../../javascript/reference/uint32array-object.md)|4|32 ビット符号なし整数|  
|[Float32Array オブジェクト](../../javascript/reference/float32array-object.md)|4|32 ビット IEEE 浮動小数点|  
|[Float64Array オブジェクト](../../javascript/reference/float64array-object.md)|9|64 ビット IEEE 浮動小数点|