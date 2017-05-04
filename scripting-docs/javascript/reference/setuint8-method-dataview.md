---
title: "setUint8 メソッド (DataView) | Microsoft Docs"
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
ms.assetid: b294262b-3f4b-4183-a292-5a6982cbdd27
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# setUint8 メソッド (DataView)
指定されたビューの先頭からのバイト オフセット位置に Uint8 値を格納します。  
  
## 構文  
  
```  
dataView.setUint8(byteOffset, value);   
```  
  
## パラメーター  
 `byteOffset`  
 値が設定されるバッファーの位置。  
  
 `value`  
 設定する値。  
  
## 解説  
 これらのメソッドでは、ビューの終端を越えて書き込まれる場合に例外が発生します。  
  
## 使用例  
 DataView の最初の Uint8 を設定する方法の例を次に示します。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint8(0, 9);  
        }  
    }  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]