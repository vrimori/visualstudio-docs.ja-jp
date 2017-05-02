---
title: "getFloat32 メソッド (DataView) | Microsoft Docs"
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
ms.assetid: adecf671-bde4-46be-a875-33b6d6e970b1
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# getFloat32 メソッド (DataView)
指定されたビューの先頭からのバイト オフセット位置にある Float32 値を取得します。  配置の制約はありません。オフセットからマルチバイト値がフェッチされている場合があります。  
  
## 構文  
  
```  
var testFloat = dataView.getFloat32(byteOffset, littleEndian);   
```  
  
## パラメーター  
 `testFloat`  
 必須です。  メソッドから返される Float32 値を指定します。  
  
 `byteOffset`  
 値が取得されるバッファーの位置。  
  
 `littleEndian`  
 省略可能です。  false または未定義の場合は、ビッグ エンディアンの値が読み取られます。それ以外の場合はリトル エンディアンの値が読み取られます。  
  
## 解説  
 これらのメソッドでは、ビューの終端を越えて読み取られる場合に例外が発生します。  
  
## 使用例  
 DataView の最初の Float32 を取得する方法の例を次に示します。  
  
```javascript  
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
  
## 必要条件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]