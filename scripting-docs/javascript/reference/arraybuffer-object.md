---
title: "ArrayBuffer オブジェクト |Microsoft ドキュメント"
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c253d63d12a4a5e71d1661aae560b74debecdd62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="arraybuffer-object"></a>ArrayBuffer オブジェクト
さまざまな型指定された配列のデータを格納するために使用されるバイナリ データの生バッファーを表します。 `ArrayBuffers`読み取りまたはを直接書き込むことはできません型指定された配列を渡すことができますが、または[DataView オブジェクト](../../javascript/reference/dataview-object.md)に応じて生バッファーを解釈します。  
  
 型指定された配列の詳細については、次を参照してください。[型指定される配列](../../javascript/advanced/typed-arrays-javascript.md)です。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## <a name="parameters"></a>パラメーター  
 `arrayBuffer`  
 必須です。 `ArrayBuffer` オブジェクトを代入する変数名を指定します。  
  
 `length`  
 バッファーの長さを指定します。 ArrayBuffer の内容は 0 に初期化されます。 要求されたバイト数を割り当てることができなかった場合に例外が発生します。  
  
## <a name="properties"></a>プロパティ  
 `ArrayBuffer` オブジェクトのプロパティを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[byteLength プロパティ](../../javascript/reference/bytelength-property-arraybuffer.md)|読み取り専用です。 ArrayBuffer の長さ (バイト単位)。|  
  
## <a name="functions"></a>関数  
 `ArrayBuffer` オブジェクトの関数を次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[ArrayBuffer.isView 関数](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|オブジェクトがバッファーのビューを提供するかどうかを決定します。|  
  
## <a name="methods"></a>メソッド  
 `ArrayBuffer` オブジェクトのメソッドを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[slice メソッド](../../javascript/reference/slice-method-arraybuffer.md)|`ArrayBuffer` の一部を返します。|  
  
## <a name="example"></a>例  
 次の例から取得したバイナリ データを処理する ArrayBuffer オブジェクトを使用する方法を示しています、 [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx)です。 使用することができます、 [DataView オブジェクト](../../javascript/reference/dataview-object.md)を個々 の値を取得します。  
  
```JavaScript  
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
  
## <a name="remarks"></a>コメント  
 使用しての詳細については`XmlHttpRequest`を参照してください[XMLHttpRequest enhancements](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069)です。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]