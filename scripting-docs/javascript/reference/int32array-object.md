---
title: "Int32Array オブジェクト | Microsoft Docs"
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
ms.assetid: 48696299-e41e-4590-b1b5-26fe19f68139
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Int32Array オブジェクト
32 ビット整数値の型指定された配列。  内容は 0 に初期化されます。  要求されたバイト数を割り当てることができなかった場合に例外が発生します。  
  
## 構文  
  
```  
  
      int32Array = new Int32Array( length );  
int32Array = new Int32Array( array );  
int32Array = new Int32Array( buffer, byteOffset, length);  
```  
  
## パラメーター  
 `int32Array`  
 必須。  **Int32Array** オブジェクトを代入する変数名を指定します。  
  
 `length`  
 配列内の要素の数を指定します。  
  
 `array`  
 この配列に含まれる配列 \(または型指定された配列\)。  内容は指定された配列または型指定された配列の内容に初期化され、各要素は Int32 型に変換されます。  
  
 `buffer`  
 Int32Array が表す ArrayBuffer を指定します。  
  
 `byteOffset`  
 省略可能。  Int32Array の開始位置として、バッファーの先頭からのオフセットをバイトで指定します。  
  
 `length`  
 配列の要素数。  
  
## 定数  
 `Int32Array` オブジェクトの定数を次の表に示します。  
  
|定数|説明|  
|--------|--------|  
|[BYTES\_PER\_ELEMENT 定数](../../javascript/reference/bytes-per-element-constant-int32array.md)|配列の各要素のサイズ \(バイト単位\)。|  
  
## プロパティ  
 `Int32Array` オブジェクトの定数を次の表に示します。  
  
|プロパティ|説明|  
|-----------|--------|  
|[buffer プロパティ](../../javascript/reference/buffer-property-int32array.md)|読み取り専用です。  この配列によって参照される ArrayBuffer を取得します。|  
|[byteLength プロパティ](../../javascript/reference/bytelength-property-int32array.md)|読み取り専用です。  構築時に固定された、この配列の ArrayBuffer の先頭からの長さ \(バイト単位\)。|  
|[byteOffset プロパティ](../../javascript/reference/byteoffset-property-int32array.md)|読み取り専用です。  構築時に固定された、この配列の ArrayBuffer の先頭からのオフセット \(バイト単位\)。|  
|[length プロパティ](../../javascript/reference/length-property-int32array.md)|配列の長さ。|  
  
## メソッド  
 次のテーブルは、`Int32Array` オブジェクトのメソッドの一覧です。  
  
|メソッド|説明|  
|----------|--------|  
|[set メソッド \(Int32Array\)](../../javascript/reference/set-method-int32array.md)|値または値の配列を設定します。|  
|[subarray メソッド \(Int32Array\)](../../javascript/reference/subarray-method-int32array.md)|この配列の ArrayBuffer ストアの新しい Int32Array ビューを取得します。|  
  
## 使用例  
 次の例は、Int32Array オブジェクトを使用して、XMLHttpRequest から取得したバイナリ データを処理する方法を示します。  
  
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
  
## 必要条件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]