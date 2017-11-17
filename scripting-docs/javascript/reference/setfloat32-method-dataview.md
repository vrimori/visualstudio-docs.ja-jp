---
title: "setFloat32 メソッド (DataView) |Microsoft ドキュメント"
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
ms.assetid: b3f68048-c817-48d2-bc17-945e3bcc94d7
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a72bf2781bfbae7c7cd301d02ad71ebfbeffa13
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="setfloat32-method-dataview"></a>setFloat32 メソッド (DataView)
ビューの先頭から指定したバイト オフセット位置にある Float32 値を設定します。 配置制約はありません。任意のオフセット位置にマルチ バイト値を設定することがあります。  
  
## <a name="syntax"></a>構文  
  
```  
dataView.setFloat32 (byteOffset, value, littleEndian);   
```  
  
## <a name="parameters"></a>パラメーター  
 `byteOffset`  
 値を取得するバッファー内の場所。  
  
 `value`  
 設定する値。  
  
 `littleEndian`  
 省略可能です。 False または定義されていない場合、ビッグ エンディアン値を記述する必要があります、それ以外の場合、リトル エンディアンの値を書き込む必要があります。  
  
## <a name="remarks"></a>コメント  
 これらのメソッドでは、ビューの末尾を越える書きがある場合に例外が発生します。  
  
## <a name="example"></a>例  
 次の例では、DataView で最初の Float32 を設定する方法を示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setFloat32(0, 9.1);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]