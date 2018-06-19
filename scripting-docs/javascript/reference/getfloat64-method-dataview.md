---
title: getFloat64 メソッド (DataView) |Microsoft ドキュメント
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
ms.assetid: 347adeb6-b24c-4e7d-8b6b-8e36aacdcae1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab6d52fcaa82cc957ba47b5ef2acdfbef90152d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636462"
---
# <a name="getfloat64-method-dataview"></a>getFloat64 メソッド (DataView)
指定されたビューの先頭からのバイト オフセット位置にある Float64 値を取得します。 配置制約はありません。マルチ バイト値は、任意のオフセットからフェッチすることがあります。  
  
## <a name="syntax"></a>構文  
  
```  
var testFloat = dataView.getFloat64(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>パラメーター  
 `testFloat`  
 必須です。 メソッドから返される Float64 値。  
  
 `byteOffset`  
 値を取得するバッファー内の場所。  
  
 `littleEndian`  
 省略可能です。 False または定義されていない場合は、ビッグ エンディアンの値を読み取る必要があります、それ以外の場合、リトル エンディアン値を読み取る必要があります。  
  
## <a name="remarks"></a>コメント  
 これらのメソッド ビューの末尾を越える読み取りは、例外が発生します。  
  
## <a name="example"></a>例  
 次の例では、DataView で最初の Float64 を取得する方法を示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getFloat64(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]