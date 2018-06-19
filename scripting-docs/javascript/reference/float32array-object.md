---
title: Float32Array オブジェクト |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4b29456a-1488-4006-ae66-5bf4c05003b1
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f7ef022b43179d2d9ce3f88fc78b8854d3cea62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637312"
---
# <a name="float32array-object"></a>Float32Array オブジェクト
32 ビット浮動小数値の型指定された配列です。 内容は 0 に初期化されます。 要求されたバイト数を割り当てることができなかった場合に例外が発生します。  
  
## <a name="syntax"></a>構文  
  
```  
  
      float32Array = new Float32Array( length );  
float32Array = new Float32Array( array );  
float32Array = new Float32Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>パラメーター  
 `float32Array`  
 必須です。 変数名を**Float32Array**オブジェクトが割り当てられます。  
  
 `length`  
 配列内の要素の数を指定します。  
  
 `array`  
 この配列に含まれる配列 (または型指定された配列)。 内容は指定された配列または型指定された配列の内容に初期化され、各要素は Float32 型に変換されます。  
  
 `buffer`  
 Float32Array が表す ArrayBuffer を指定します。  
  
 `byteOffset`  
 省略可能です。 Float32Array の開始位置として、バッファーの先頭からのオフセットをバイトで指定します。  
  
 `length`  
 配列の要素数。  
  
## <a name="constants"></a>定数  
 `Float32Array` オブジェクトの定数を次の表に示します。  
  
|定数|説明|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT 定数](../../javascript/reference/bytes-per-element-constant-float32array.md)|配列の各要素のサイズ (バイト単位)。|  
  
## <a name="properties"></a>プロパティ  
 `Float32Array` オブジェクトの定数を次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[buffer プロパティ](../../javascript/reference/buffer-property-float32array.md)|読み取り専用です。 この配列によって参照される ArrayBuffer を取得します。|  
|[byteLength プロパティ](../../javascript/reference/bytelength-property-float32array.md)|読み取り専用です。 構築時に固定された、この配列の ArrayBuffer の先頭からの長さ (バイト単位)。|  
|[byteOffset プロパティ](../../javascript/reference/byteoffset-property-float32array.md)|読み取り専用です。 構築時に固定された、この配列の ArrayBuffer の先頭からのオフセット (バイト単位)。|  
|[length プロパティ](../../javascript/reference/length-property-float32array.md)|配列の長さ。|  
|||  
  
## <a name="methods"></a>メソッド  
 `Float32Array` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[get メソッド](../../javascript/reference/get-method-float32array.md)|省略可能。 指定したインデックス位置にある要素を取得します。|  
|[set メソッド (Float32Array)](../../javascript/reference/set-method-float32array.md)|値または値の配列を設定します。|  
|[subarray メソッド (Float32Array)](../../javascript/reference/subarray-method-float32array.md)|この配列の ArrayBuffer ストアの新しい Float32Array ビューを取得します。|  
  
## <a name="example"></a>例  
 次の例は、Float32Array オブジェクトを使用して、XmlHttpRequest から取得したバイナリ データを処理する方法を示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Float32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getFloat32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]