---
title: BYTES_PER_ELEMENT 定数 (Int32Array) |Microsoft ドキュメント
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
ms.assetid: 95a84abb-c8d3-4fa9-8944-0fde9cfdb3df
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a230cf93d3308199e823b433e53bfcaafb3d48d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633962"
---
# <a name="bytesperelement-constant-int32array"></a>BYTES_PER_ELEMENT 定数 (Int32Array)
配列の各要素のサイズ (バイト単位)。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
var arraySize = int32Array.BYTES_PER_ELEMENT;  
```  
  
## <a name="example"></a>例  
 次の例は、配列の要素のサイズの取得方法を示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int32Array(buffer.byteLength / 4);  
            alert(intArr.BYTES_PER_ELEMENT);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]