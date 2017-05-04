---
title: "再帰 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "関数、再帰関数呼び出し"
  - "再帰プロシージャ"
  - "関数呼び出し、再帰"
ms.assetid: 885855a6-3838-457d-9eb4-cce1ccaa5a8d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# 再帰 (JavaScript)
再帰は、関数で関数自身を呼び出す、重要なプログラミング技法です。  
  
## 階乗の例を次に示します。  
 再帰法を使用した例としては、階乗の計算があります。  数値 *n* の階乗は 1 \* 2 \* 3 \*...   *n* の乗算で計算されます。  次の例では、結果を計算する `while` ループを使用することにより、階乗を繰り返し計算する方法を示します。  
  
```javascript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    var tmp = num;  
    while (num-- > 2) {  
        tmp *= num;  
    }  
    return tmp;  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```  
  
 例は非常に簡単に再帰的にすることができます。  `while` ループを使用して値を計算する代わりに `factorial` を再度呼び出して、次の最小値を渡すことができます。  値が 1 になると再帰は停止します。  
  
```javascript  
function factorial(num)  
{  
    // If the number is less than 0, reject it.  
    if (num < 0) {  
        return -1;  
    }  
    // If the number is 0, its factorial is 1.  
    else if (num == 0) {  
        return 1;  
    }  
    // Otherwise, call this recursive procedure again.  
    else {  
        return (num * factorial(num - 1));  
    }  
}  
  
var result = factorial(8);  
document.write(result);  
  
// Output: 40320  
```