---
title: Float64Array オブジェクト |Microsoft ドキュメント
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
ms.assetid: 74c945dc-56ae-458c-b0aa-782f240e9b6c
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20544812d94c1234d85d714f6e469d0de4f4c5ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637412"
---
# <a name="float64array-object"></a>Float64Array オブジェクト
64 ビット浮動小数値の型指定された配列です。 内容は 0 に初期化されます。 要求されたバイト数を割り当てることができなかった場合に例外が発生します。  
  
## <a name="syntax"></a>構文  
  
```  
  
      float64Array = new Float64Array( length );  
float64Array = new Float64Array( array );  
float64Array = new Float64Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>パラメーター  
 `float64Array`  
 必須です。 変数名を**Float64Array**オブジェクトが割り当てられます。  
  
 `length`  
 配列内の要素の数を指定します。  
  
 `array`  
 この配列に含まれる配列 (または型指定された配列)。 内容は指定された配列または型指定された配列の内容に初期化され、各要素は Float64 型に変換されます。  
  
 `buffer`  
 Float64Array が表す ArrayBuffer を指定します。  
  
 `byteOffset`  
 省略可能です。 Float64Array の開始位置として、バッファーの先頭からのオフセットをバイトで指定します。  
  
 `length`  
 配列の要素数。  
  
## <a name="constants"></a>定数  
 `Float64Array` オブジェクトの定数を次の表に示します。  
  
|定数|説明|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT 定数](../../javascript/reference/bytes-per-element-constant-float64array.md)|配列の各要素のサイズ (バイト単位)。|  
  
## <a name="properties"></a>プロパティ  
 `Float64Array` オブジェクトの定数を次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[buffer プロパティ](../../javascript/reference/bytelength-property-float64array.md)|読み取り専用です。 この配列によって参照される ArrayBuffer を取得します。|  
|[byteLength プロパティ](../../javascript/reference/bytelength-property-float64array.md)|読み取り専用です。 構築時に固定された、この配列の ArrayBuffer の先頭からの長さ (バイト単位)。|  
|[byteOffset プロパティ](../../javascript/reference/length-property-float64array.md)|読み取り専用です。 構築時に固定された、この配列の ArrayBuffer の先頭からのオフセット (バイト単位)。|  
|[length プロパティ](../../javascript/reference/length-property-float64array.md)|配列の長さ。|  
  
## <a name="methods"></a>メソッド  
 `Float64Array` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[get メソッド](../../javascript/reference/get-method-float64array.md)|省略可能。 指定したインデックス位置にある要素を取得します。|  
|[set メソッド (Float64Array)](../../javascript/reference/set-method-float64array.md)|値または値の配列を設定します。|  
|[subarray メソッド (Float64Array)](../../javascript/reference/subarray-method-float64array.md)|この配列の ArrayBuffer ストアの新しい Float64Array ビューを取得します。|  
  
## <a name="example"></a>例  
 次の例は、Float64Array オブジェクトを使用して、XmlHttpRequest から取得したバイナリ データを処理する方法を示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Float64Array(buffer.byteLength / 8);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getFloat64(i * 8);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]