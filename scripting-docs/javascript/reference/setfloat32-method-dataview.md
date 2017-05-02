---
title: "setFloat32 メソッド (DataView) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b3f68048-c817-48d2-bc17-945e3bcc94d7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# setFloat32 メソッド (DataView)
指定されたビューの先頭からのバイト オフセット位置に Float32 値を設定します。  配置の制約はありません。オフセットにマルチバイト値が設定されている場合があります。  
  
## 構文  
  
```  
dataView.setFloat32 (byteOffset, value, littleEndian);   
```  
  
## パラメーター  
 `byteOffset`  
 値が取得されるバッファーの位置。  
  
 `value`  
 設定する値。  
  
 `littleEndian`  
 省略可能です。  false または未定義の場合は、ビッグ エンディアンの値が書き込まれます。それ以外の場合はリトル エンディアンの値が書き込まれます。  
  
## 解説  
 これらのメソッドでは、ビューの終端を越えて書き込まれる場合に例外が発生します。  
  
## 使用例  
 DataView の最初の Float32 を設定する方法の例を次に示します。  
  
```javascript  
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
  
## 必要条件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]