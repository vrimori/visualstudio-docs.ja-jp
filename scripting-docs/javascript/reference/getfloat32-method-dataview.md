---
title: getFloat32 メソッド (DataView) |Microsoft ドキュメント
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
ms.assetid: adecf671-bde4-46be-a875-33b6d6e970b1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75fc5be6d8563a44504ae2d1c7ddd9429eccb390
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636502"
---
# <a name="getfloat32-method-dataview"></a>getFloat32 メソッド (DataView)
指定されたビューの先頭からのバイト オフセット位置にある Float32 値を取得します。 配置制約はありません。マルチ バイト値は、任意のオフセットからフェッチすることがあります。  
  
## <a name="syntax"></a>構文  
  
```  
var testFloat = dataView.getFloat32(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>パラメーター  
 `testFloat`  
 必須です。 メソッドから返される Float32 値。  
  
 `byteOffset`  
 値を取得するバッファー内の場所。  
  
 `littleEndian`  
 省略可能です。 False または定義されていない場合は、ビッグ エンディアンの値を読み取る必要があります、それ以外の場合、リトル エンディアン値を読み取る必要があります。  
  
## <a name="remarks"></a>コメント  
 これらのメソッド ビューの末尾を越える読み取りは、例外が発生します。  
  
## <a name="example"></a>例  
 次の例では、DataView で最初の Float32 を取得する方法を示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getFloat32(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]