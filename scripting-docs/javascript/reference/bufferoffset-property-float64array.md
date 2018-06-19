---
title: bufferOffset プロパティ (Float64Array) |Microsoft ドキュメント
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
ms.assetid: 9b566ec9-97d1-4a54-96cd-c1608f0ed330
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2d64af7d1f7aeb9f4f42ee1854c5a6a93ad5505
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633422"
---
# <a name="bufferoffset-property-float64array"></a>bufferOffset プロパティ (Float64Array)
読み取り専用です。 構築時に固定された、この配列の ArrayBuffer の先頭からのオフセット (バイト単位)。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
var arrayOffset = float64Array.byteOffset;  
```  
  
## <a name="example"></a>例  
 配列の offset を取得する方法の例を次に示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float64Array(buffer.byteLength / 8);  
            alert(floatArr.byteOffset);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]