---
title: setInt32 メソッド (DataView) |Microsoft ドキュメント
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
ms.assetid: 07e5f068-0e3f-4c23-84b3-c72658d7f194
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00f3f6b03cdd3a8d5d7b95184f1c0ff5c356592a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639132"
---
# <a name="setint32-method-dataview"></a>setInt32 メソッド (DataView)
ビューの先頭から指定したバイト オフセット位置に Int32 値を設定します。 配置制約はありません。任意のオフセット位置にマルチ バイト値を設定することがあります。  
  
## <a name="syntax"></a>構文  
  
```  
dataView.setInt32 (byteOffset, value, littleEndian);   
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
 次の例では、DataView で最初の Int32 を設定する方法を示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setInt32(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]