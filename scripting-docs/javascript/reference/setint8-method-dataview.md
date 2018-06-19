---
title: setInt8 メソッド (DataView) |Microsoft ドキュメント
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
ms.assetid: 0a0e1450-e0c4-4778-8706-4d332442d882
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6f9bd9c4b3bea25686036d199d1a987927172d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639492"
---
# <a name="setint8-method-dataview"></a>setInt8 メソッド (DataView)
ビューの先頭から指定したバイト オフセット位置に Int8 値を格納します。  
  
## <a name="syntax"></a>構文  
  
```  
dataView.setInt8(byteOffset, value);   
```  
  
## <a name="parameters"></a>パラメーター  
 `byteOffset`  
 値の設定をバッファー内の場所。  
  
 `value`  
 設定する値。  
  
## <a name="remarks"></a>コメント  
 これらのメソッドでは、ビューの末尾を越える書きがある場合に例外が発生します。  
  
## <a name="example"></a>例  
 次の例では、DataView で最初の Int8 を設定する方法を示します。  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setInt8(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]