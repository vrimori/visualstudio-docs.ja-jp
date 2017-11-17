---
title: "Int8Array オブジェクト |Microsoft ドキュメント"
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
ms.assetid: 0e3bdbc5-8d85-4c0d-b399-693b01674803
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e3f85a505f41f2909330e938f4978433fc823f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="int8array-object"></a>Int8Array オブジェクト
8 ビット整数値の型指定された配列。 内容は 0 に初期化されます。 要求されたバイト数を割り当てることができなかった場合に例外が発生します。  
  
## <a name="syntax"></a>構文  
  
```  
  
      int8Array = new Int8Array( length );  
intArray = new Int8Array( array );  
intArray = new Int8Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>パラメーター  
 `int8Array`  
 必須です。 `Int8Array` オブジェクトを代入する変数名を指定します。  
  
 `length`  
 配列内の要素の数を指定します。  
  
 `array`  
 この配列に含まれる配列 (または型指定された配列)。 内容は指定された配列または型指定された配列の内容に初期化され、各要素は Int8 型に変換されます。  
  
 `buffer`  
 Int8Array が表す ArrayBuffer。  
  
 `byteOffset`  
 省略可能です。 Int8Array の開始位置として、バッファーの先頭からのオフセットをバイトで指定します。  
  
 `length`  
 配列の要素数。  
  
## <a name="constants"></a>定数  
 `Int8Array` オブジェクトの定数を次の表に示します。  
  
|定数|説明|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT 定数](../../javascript/reference/bytes-per-element-constant-int8array.md)|配列の各要素のサイズ (バイト単位)。|  
  
## <a name="properties"></a>プロパティ  
 `Int8Array` オブジェクトの定数を次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[buffer プロパティ](../../javascript/reference/buffer-property-int8array.md)|読み取り専用です。 この配列によって参照される ArrayBuffer を取得します。|  
|[byteLength プロパティ](../../javascript/reference/bytelength-property-int8array.md)|読み取り専用です。 構築時に固定された、この配列の ArrayBuffer の先頭からの長さ (バイト単位)。|  
|[byteOffset プロパティ](../../javascript/reference/byteoffset-property-int8array.md)|読み取り専用です。 構築時に固定された、この配列の ArrayBuffer の先頭からのオフセット (バイト単位)。|  
|[length プロパティ](../../javascript/reference/length-property-int8array.md)|配列の長さ。|  
  
## <a name="methods"></a>メソッド  
 `Int8Array` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[set メソッド (Int8Array)](../../javascript/reference/set-method-int8array.md)|値または値の配列を設定します。|  
|[subarray メソッド (Int8Array)](../../javascript/reference/subarray-method-int8array.md)|この配列の ArrayBuffer ストアの新しい Int8Array ビューを取得します。|  
  
## <a name="example"></a>例  
 次の例は、Int8Array オブジェクトを使用して、XMLHttpRequest から取得したバイナリ データを処理する方法を示します。  
  
```JavaScript  
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
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]