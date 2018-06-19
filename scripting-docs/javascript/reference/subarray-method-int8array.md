---
title: subarray メソッド (Int8Array) |Microsoft ドキュメント
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
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e32c3a0da7e3173273eb40bf52bb6583bd77df51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640012"
---
# <a name="subarray-method-int8array"></a>subarray メソッド (Int8Array)
この配列の ArrayBuffer ストアの新しい Int8Array ビューを取得します。begin から end まで (begin は含まれますが、end は含まれません) の要素を参照します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## <a name="parameters"></a>パラメーター  
 `newInt8Array`  
 このメソッドで返されるサブ配列。  
  
 `begin`  
 配列の先頭のインデックス。  
  
 `end`  
 配列の末尾のインデックス。 これは、内包的ではありません。  
  
## <a name="remarks"></a>コメント  
 begin または end が負の場合は、配列の先頭からではなく、配列の末尾からのインデックスを参照します。 end が指定されていない場合、サブ配列には、TypedArray の先頭から末尾までのすべての要素が含まれます。 開始値および終了値で指定された範囲は、現在の配列の有効なインデックスの範囲に固定されます。 新しい TypedArray の計算された長さが負となる場合は、ゼロに固定されます。 返される TypedArray は、このメソッドが呼び出される配列と同じ型になります。  
  
## <a name="example"></a>例  
 次の例は、配列の先頭の要素から開始して、長さが要素 2 つ分のサブ配列を取得する方法を示しています。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]