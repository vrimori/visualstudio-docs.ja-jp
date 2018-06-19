---
title: getUint8 メソッド (DataView) |Microsoft ドキュメント
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
ms.assetid: 9fbf4be3-4c0b-4963-a7a1-d57f1501b4cf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 315baa2ca5abfe006a7f8d524619479d99a11fc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636742"
---
# <a name="getuint8-method-dataview"></a>getUint8 メソッド (DataView)
指定されたビューの先頭からのバイト オフセット位置にある Uint8 値を取得します。 配置制約はありません。マルチ バイト値は、任意のオフセットからフェッチすることがあります。  
  
## <a name="syntax"></a>構文  
  
```  
var testInt = dataView.getUint8(byteOffset);   
```  
  
## <a name="parameters"></a>パラメーター  
 `testInt`  
 必須です。 メソッドから返される Uint8 値。  
  
 `byteOffset`  
 値を取得するバッファー内の場所。  
  
## <a name="remarks"></a>コメント  
 これらのメソッド ビューの末尾を越える読み取りは、例外が発生します。  
  
## <a name="example"></a>例  
 次の例では、DataView で最初の Uint8 を取得する方法を示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getUint8(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]