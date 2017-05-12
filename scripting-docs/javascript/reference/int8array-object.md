---
title: "Int8Array オブジェクト | Microsoft Docs"
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
ms.assetid: 0e3bdbc5-8d85-4c0d-b399-693b01674803
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Int8Array オブジェクト
8 ビット整数値の型指定された配列。  内容は 0 に初期化されます。  要求されたバイト数を割り当てることができなかった場合に例外が発生します。  
  
## 構文  
  
```  
  
      int8Array = new Int8Array( length );  
intArray = new Int8Array( array );  
intArray = new Int8Array( buffer, byteOffset, length);  
```  
  
## パラメーター  
 `int8Array`  
 必須。  `Int8Array` オブジェクトを代入する変数名を指定します。  
  
 `length`  
 配列内の要素の数を指定します。  
  
 `array`  
 この配列に含まれる配列 \(または型指定された配列\)。  内容は指定された配列または型指定された配列の内容に初期化され、各要素は Int8 型に変換されます。  
  
 `buffer`  
 Int8Array が表す ArrayBuffer。  
  
 `byteOffset`  
 省略可能。  Int8Array の開始位置として、バッファーの先頭からのオフセットをバイトで指定します。  
  
 `length`  
 配列の要素数。  
  
## 定数  
 `Int8Array` オブジェクトの定数を次の表に示します。  
  
|定数|説明|  
|--------|--------|  
|[BYTES\_PER\_ELEMENT 定数](../../javascript/reference/bytes-per-element-constant-int8array.md)|配列の各要素のサイズ \(バイト単位\)。|  
  
## プロパティ  
 `Int8Array` オブジェクトの定数を次の表に示します。  
  
|プロパティ|説明|  
|-----------|--------|  
|[buffer プロパティ](../../javascript/reference/buffer-property-int8array.md)|読み取り専用です。  この配列によって参照される ArrayBuffer を取得します。|  
|[byteLength プロパティ](../../javascript/reference/bytelength-property-int8array.md)|読み取り専用です。  構築時に固定された、この配列の ArrayBuffer の先頭からの長さ \(バイト単位\)。|  
|[byteOffset プロパティ](../../javascript/reference/byteoffset-property-int8array.md)|読み取り専用です。  構築時に固定された、この配列の ArrayBuffer の先頭からのオフセット \(バイト単位\)。|  
|[length プロパティ](../../javascript/reference/length-property-int8array.md)|配列の長さ。|  
  
## メソッド  
 次のテーブルは、`Int8Array` オブジェクトのメソッドの一覧です。  
  
|メソッド|説明|  
|----------|--------|  
|[set メソッド \(Int8Array\)](../../javascript/reference/set-method-int8array.md)|値または値の配列を設定します。|  
|[subarray メソッド \(Int8Array\)](../../javascript/reference/subarray-method-int8array.md)|この配列の ArrayBuffer ストアの新しい Int8Array ビューを取得します。|  
  
## 使用例  
 次の例は、Int8Array オブジェクトを使用して、XMLHttpRequest から取得したバイナリ データを処理する方法を示します。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int8Array(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]