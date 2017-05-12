---
title: "関数の結果に割り当てられません。 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5003"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 関数の結果に割り当てられません。
関数の戻り値に値を代入しようとしました。  関数の戻り値は、変数に代入することはできますが、変数として使用することはできません。  関数自体に新しい値を割り当てる場合は、かっこ \(関数呼び出し演算子\) を省略します。  このエラーが発生する状況を例を次に示します。  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### このエラーを解決するには  
  
-   関数の戻り値を "代入先" として使用しないようにします。  ただし、関数の戻り値を "変数" に代入することはできます。  
  
    ```javascript  
    myVar = myFunction(42);  
    ```  
  
-   または、関数の戻り値ではなく、関数自体を変数に割り当てることもできます。  
  
    ```javascript  
    myFunction = new Function("return 42;");  
    ```  
  
## 参照  
 [Function オブジェクト](../../javascript/reference/function-object-javascript.md)   
 [JavaScript コードの記述](../../javascript/writing-javascript-code.md)   
 [関数](../../javascript/functions-javascript.md)