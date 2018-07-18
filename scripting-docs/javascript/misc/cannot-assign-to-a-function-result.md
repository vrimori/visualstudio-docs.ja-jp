---
title: 関数の結果に割り当てることはできません |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e7ea718aa97ab7b2eb0924458826cd1eac5672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632982"
---
# <a name="cannot-assign-to-a-function-result"></a>関数の結果に割り当てられません。
関数の結果に値を代入しようとしました。 関数の結果を変数に割り当てることができますが、変数として使用することはできません。 関数自体に新しい値を代入する場合は、(関数呼び出し演算子) のかっこを省略します。 次の例では、このエラーを生成するような状況を示します。  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ものとして関数呼び出しの結果の値を使用しないで*に割り当てる*です。 関数呼び出しの結果を割り当てることができます*変数に*もします。  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   または、割り当てることができます、関数自体 (とその戻り値ではなく) を変数にします。  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>関連項目  
 [Function オブジェクト](../../javascript/reference/function-object-javascript.md)   
 [JavaScript コードの記述](../../javascript/writing-javascript-code.md)   
 [関数](../../javascript/functions-javascript.md)