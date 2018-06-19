---
title: set メソッド (Int8Array) |Microsoft ドキュメント
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
ms.assetid: 4beae82e-8556-48aa-86c6-18c8859d913e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfa9c319caf448e20888aeefa2f29aaade9aa364
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639812"
---
# <a name="set-method-int8array"></a>set メソッド (Int8Array)
値または値の配列を設定します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
int8Array.set(index, value);  
int8Array.set(array, offset);  
  
```  
  
## <a name="parameters"></a>パラメーター  
 `index`  
 設定する位置のインデックス。  
  
 `value`  
 設定する値。  
  
 `array`  
 設定する値の型指定された配列、または型指定されていない配列。  
  
 `offset`  
 現在の配列内で値が書き込まれる位置のインデックス。  
  
## <a name="remarks"></a>コメント  
 入力配列が TypedArray の場合は、2 種類の配列で、基になる ArrayBuffer が同じであることがあります。 この場合は、すべてのデータが最初にどちらの配列とも重複しない一時バッファーにコピーされ、そこからデータが現在の配列にコピーされたかのように値が設定されます。  
  
 オフセットと指定された配列の長さを加算すると現在の TypedArray の範囲外になる場合は、例外が発生します。  
  
## <a name="example"></a>例  
 次の例は、配列の先頭の要素の設定方法を示します。  
  
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
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]