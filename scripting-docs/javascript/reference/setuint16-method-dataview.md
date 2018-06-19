---
title: setUint16 メソッド (DataView) |Microsoft ドキュメント
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
ms.assetid: bdf47cda-7fa5-4aaa-8aa2-8cf9a8d56cb3
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 935c117995e00284a0083a6bdf7aedfc8c51d15c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639702"
---
# <a name="setuint16-method-dataview"></a>setUint16 メソッド (DataView)
ビューの先頭から指定したバイト オフセット位置にある Uint16 値を設定します。 配置制約はありません。任意のオフセット位置にマルチ バイト値を設定することがあります。  
  
## <a name="syntax"></a>構文  
  
```  
dataView.setUint16(byteOffset, value, littleEndian);   
```  
  
## <a name="parameters"></a>パラメーター  
 `testInt`  
 必須です。 メソッドから返される Uint16 値。  
  
 `value`  
 設定する値。  
  
 `byteOffset`  
 値を取得するバッファー内の場所。  
  
 `littleEndian`  
 省略可能です。 False または定義されていない場合、ビッグ エンディアン値を記述する必要があります、それ以外の場合、リトル エンディアンの値を書き込む必要があります。  
  
## <a name="remarks"></a>コメント  
 これらのメソッドでは、ビューの末尾を越える書きがある場合に例外が発生します。  
  
## <a name="example"></a>例  
 次の例では、DataView で最初の Uint16 を設定する方法を示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint16(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]