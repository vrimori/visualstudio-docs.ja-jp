---
title: "DataView オブジェクト |Microsoft ドキュメント"
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
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 370ee1afbdf7fe1d87843c4979833d54a575a4fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="dataview-object"></a>DataView オブジェクト
DataView オブジェクトを使用すると、ArrayBuffer 内の任意の場所でさまざまな種類のバイナリ データを読み書きできます。  
  
## <a name="syntax"></a>構文  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dataView`  
 必須です。 変数名を**DataView**オブジェクトが割り当てられます。  
  
 `buffer`  
 DataView が表す ArrayBuffer です。  
  
 `byteOffset`  
 省略可能です。 DataView の開始位置として、バッファーの先頭からのオフセットをバイトで指定します。  
  
 `byteLength`  
 省略可能です。 DataView で表す必要があるバッファーのセクションの長さ (バイト単位) を指定します。  
  
## <a name="remarks"></a>コメント  
 byteOffset と byteLength の両方が省略されている場合、DataView は ArrayBuffer の範囲全体を対象とします。 byteLength が省略されている場合、DataView は、指定された byteOffset から ArrayBuffer の末尾までを対象とします。 指定した byteOffset と byteLength が ArrayBuffer の末尾を超える領域を参照すると、例外が発生します。  
  
## <a name="properties"></a>プロパティ  
 `DataView` オブジェクトのプロパティを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[buffer プロパティ](../../javascript/reference/buffer-property-dataview.md)|読み取り専用です。 このビューによって参照される ArrayBuffer を取得します。|  
|[byteLength プロパティ](../../javascript/reference/bytelength-property-dataview.md)|読み取り専用です。 構築時に固定された、このビューの ArrayBuffer の先頭からの長さ (バイト単位)。|  
|[byteOffset プロパティ](../../javascript/reference/byteoffset-property-dataview.md)|読み取り専用です。 構築時に固定された、このビューの ArrayBuffer の先頭からのオフセット (バイト単位)。|  
  
## <a name="methods"></a>メソッド  
 `DataView` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[getInt8 メソッド](../../javascript/reference/getint8-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置にある Int8 値を取得します。|  
|[getUint8 メソッド (DataView)](../../javascript/reference/getuint8-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置にある Uint8 値を取得します。|  
|[getInt16 メソッド (DataView)](../../javascript/reference/getint16-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置にある Int16 値を取得します。|  
|[getUint16 メソッド (DataView)](../../javascript/reference/getuint16-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置にある Uint16 値を取得します。|  
|[getInt32 メソッド (DataView)](../../javascript/reference/getint32-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置にある Int32 値を取得します。|  
|[getUint32 メソッド (DataView)](../../javascript/reference/getuint32-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置にある Uint32 値を取得します。|  
|[getFloat32 メソッド (DataView)](../../javascript/reference/getfloat32-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置にある Float32 値を取得します。|  
|[getFloat64 メソッド (DataView)](../../javascript/reference/getfloat64-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置にある Float64 値を取得します。|  
|[setInt8 メソッド (DataView)](../../javascript/reference/setint8-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置に Int8 値を格納します。|  
|[setUint8 メソッド (DataView)](../../javascript/reference/setuint8-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置に Uint8 値を格納します。|  
|[setInt16 メソッド (DataView)](../../javascript/reference/setint16-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置に Int16 値を格納します。|  
|[setUint16 メソッド (DataView)](../../javascript/reference/setuint16-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置に Uint16 値を格納します。|  
|[setInt32 メソッド (DataView)](../../javascript/reference/setint32-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置に Int32 値を格納します。|  
|[setUint32 メソッド (DataView)](../../javascript/reference/setuint32-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置に Uint32 値を格納します。|  
|[setFloat32 メソッド (DataView)](../../javascript/reference/setfloat32-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置に Float32 値を格納します。|  
|[setFloat64 メソッド (DataView)](../../javascript/reference/setfloat64-method-dataview.md)|指定されたビューの先頭からのバイト オフセット位置に Float64 値を格納します。|  
  
## <a name="example"></a>例  
 次の例は、DataView オブジェクトを使用して、XmlHttpRequest から取得したバイナリ データを処理する方法を示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var ints = new Int32Array(dataView.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]