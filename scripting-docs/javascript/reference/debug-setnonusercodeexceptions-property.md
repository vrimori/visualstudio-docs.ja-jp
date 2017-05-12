---
title: "Debug.setNonUserCodeExceptions プロパティ | Microsoft Docs"
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
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Debug.setNonUserCodeExceptions プロパティ
このスコープの任意の try\-catch ブロックが、デバッガーによって "ユーザーにハンドルされていない" として処理されるかどうかを決定します。  例外は、"スローされる"、"ユーザーにハンドルされていない"、または "ハンドルされていない" に分類できます。  
  
 指定されたスコープでこのプロパティが `true` に設定されていると、デバッガーは、ユーザーにハンドルされていない例外が発生したときに中断するように開発者によって指定されている場合に、そのスコープ内でスローされる例外に対してなんらかの操作 \(中断など\) を行うと判断できます。  このプロパティが `false` に設定されている場合は、プロパティがまったく設定されていない場合と同じです。  
  
 デバックの詳細については、「[Active Script Debugging Overview \(アクティブ スクリプト デバッグの概要\)](http://go.microsoft.com/fwlink/p/?LinkId=249469)」を参照してください。  
  
## 構文  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## 使用例  
 次のコードに、このプロパティを設定する方法を示します。  
  
```javascript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## 必要条件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]