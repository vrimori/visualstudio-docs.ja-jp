---
title: "Uint8ClampedArray オブジェクト (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: 0c5537f7-00b4-487a-8fba-ef032e67e7bd
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51673eadc8eb905355bf136dc82b2f240462180a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="uint8clampedarray-object-javascript"></a>Uint8ClampedArray オブジェクト (JavaScript)
0 ～ 255 の範囲に制限される値による 8 ビットの符号なし整数で型指定された配列。 内容は 0 に初期化されます。 要求されたバイト数を割り当てることができない場合は、例外がスローされます。  
  
## <a name="syntax"></a>構文  
  
```  
  
      uint8ClampedArray = new Uint8ClampedArray( length );  
uint8ClampedArray = new Uint8ClampedArray( array );  
uint8ClampedArray = new Uint8ClampedArray( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>パラメーター  
 `uint8ClampedArray`  
 必須です。 `Uint8ClampedArray` オブジェクトを代入する変数名を指定します。  
  
 `length`  
 省略可能です。 配列の要素数。  
  
 `array`  
 省略可能です。 この配列が含む配列 (または型指定された配列)。 内容は指定された配列または型指定された配列の内容に初期化され、各要素は `Uint8` 型に変換されます。  
  
 `buffer`  
 省略可能です。 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)を`Uint8ClampedArray`を表します。  
  
 `byteOffset`  
 省略可能です。 `Uint8ClampedArray` の開始位置として、バッファーの先頭からのオフセットをバイトで指定します。  
  
 `length`  
 省略可能です。 配列の要素数。  
  
## <a name="remarks"></a>コメント  
 `Uint8ClampedArray` オブジェクトに保存される値は、0 ～ 255 の間になります。 配列メンバーに負の値を設定すると、値には 0 が設定されます。 255 より大きい値を設定すると、値としては 255 が設定されます。  
  
 値が、`Uint8ClampedArray`オブジェクトに丸められます、最も近い偶数の値と呼ばれる銀行型丸め方式です。  
  
## <a name="constants"></a>定数  
 `Uint8ClampedArray` オブジェクトの定数を次の表に示します。  
  
|定数|説明|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT 定数](../../javascript/reference/bytes-per-element-constant-uint8clampedarray.md)|配列の各要素のサイズ (バイト単位)。|  
  
## <a name="properties"></a>プロパティ  
 `Uint8ClampedArray` オブジェクトの定数を次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[buffer プロパティ](../../javascript/reference/buffer-property-uint8clampedarray.md)|読み取り専用です。 取得、 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)はこの配列によって参照されます。|  
|[byteLength プロパティ](../../javascript/reference/bytelength-property-uint8clampedarray.md)|読み取り専用です。 この配列の先頭からの長さ、 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)、(バイト単位) の構築時に固定済みです。|  
|[byteOffset プロパティ](../../javascript/reference/byteoffset-property-uint8clampedarray.md)|読み取り専用です。 この配列の先頭からのオフセット、 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)、(バイト単位) の構築時に固定済みです。|  
|[length プロパティ](../../javascript/reference/length-property-uint8clampedarray.md)|配列の長さ。|  
  
## <a name="methods"></a>メソッド  
 `Uint8ClampedArray` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[set メソッド](../../javascript/reference/set-method-uint8clampedarray.md)|値または値の配列を設定します。|  
|[subarray メソッド](../../javascript/reference/subarray-method-uint8clampedarray.md)|新しい取得`Uint8ClampedArray`の表示、 [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)サブ配列の最初と最後の要素を指定し、この配列に格納します。|  
  
## <a name="example"></a>例  
 次の例は、`Uint8ClampedArray` オブジェクトを使用して、`XmlHttpRequest` から取得したバイナリ データを処理する方法を示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8ClampedArray(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="example"></a>例  
 次の例は、`Uint8ClampedArray` で値を制限する方法を示します。  
  
```JavaScript  
var ints = new Uint8ClampedArray(2);  
ints[0] = -1;  // 0 will be assigned.  
ints[1] = 256; // 255 will be assigned.  
  
```  
  
## <a name="example"></a>例  
 次の例は、`Uint8ClampedArray` で値を丸める方法を示します。  
  
```  
var ints = new Uint8ClampedArray(4);  
ints[0] = 11.3; // 11 will be assigned (same as Int8Array).  
ints[1] = 11.8; // 12 will be assigned (same as Int8Array).  
ints[2] = 10.5; // 10 will be assigned (rounded to the nearest   
                // even value).  
ints[3] = 11.5; // 12 will be assigned (rounded to the nearest   
                // even value).  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Uint8Array オブジェクト](../../javascript/reference/uint8array-object.md)   
 [ArrayBuffer オブジェクト](../../javascript/reference/arraybuffer-object.md)
