---
title: "Uint16Array オブジェクト |Microsoft ドキュメント"
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
ms.assetid: e684647d-04d0-41a9-9089-16612e18ec7d
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 447c0509a29f1696e0204d6f37ff88d3c0bdecae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="uint16array-object"></a>Uint16Array オブジェクト
16 ビット符号なし整数値の型指定された配列。 内容は 0 に初期化されます。 要求されたバイト数を割り当てることができなかった場合に例外が発生します。  
  
## <a name="syntax"></a>構文  
  
```  
  
      uint16Array = new Uint16Array( length );  
uint16Array = new Uint16Array( array );  
uint16Array = new Uint16Array( buffer, byteOffset, length );  
```  
  
## <a name="parameters"></a>パラメーター  
 `uint16Array`  
 必須です。 変数名を**Uint16Array**オブジェクトが割り当てられます。  
  
 `length`  
 配列内の要素の数を指定します。  
  
 `array`  
 この配列に含まれる配列 (または型指定された配列)。 内容は指定された配列または型指定された配列の内容に初期化され、各要素は Uint16 型に変換されます。  
  
 `buffer`  
 Uint16Array が表す ArrayBuffer を指定します。  
  
 `byteOffset`  
 省略可能です。 Uint16Array の開始位置として、バッファーの先頭からのオフセットをバイトで指定します。  
  
 `length`  
 配列の要素数。  
  
## <a name="constants"></a>定数  
 `Uint16Array` オブジェクトの定数を次の表に示します。  
  
|定数|説明|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT 定数](../../javascript/reference/bytes-per-element-constant-uint16array.md)|配列の各要素のサイズ (バイト単位)。|  
  
## <a name="properties"></a>プロパティ  
 `Uint16Array` オブジェクトの定数を次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[buffer プロパティ](../../javascript/reference/buffer-property-uint16array.md)|読み取り専用です。 この配列によって参照される ArrayBuffer を取得します。|  
|[byteLength プロパティ](../../javascript/reference/bytelength-property-uint16array.md)|読み取り専用です。 構築時に固定された、この配列の ArrayBuffer の先頭からの長さ (バイト単位)。|  
|[byteOffset プロパティ](../../javascript/reference/byteoffset-property-uint16array.md)|読み取り専用です。 構築時に固定された、この配列の ArrayBuffer の先頭からのオフセット (バイト単位)。|  
|[length プロパティ](../../javascript/reference/length-property-uint16array.md)|配列の長さ。|  
|||  
  
## <a name="methods"></a>メソッド  
 `Uint16Array` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[set メソッド (Uint16Array)](../../javascript/reference/set-method-uint16array.md)|値または値の配列を設定します。|  
|[subarray メソッド (Uint16Array)](../../javascript/reference/subarray-method-uint16array.md)|この配列の ArrayBuffer ストアの新しい Uint16Array ビューを取得します。|  
  
## <a name="example"></a>例  
 次の例は、Uint16Array オブジェクトを使用して、XMLHttpRequest から取得したバイナリ データを処理する方法を示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]