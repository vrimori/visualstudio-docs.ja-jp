---
title: "サポートされていない値の引数の循環参照 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d25489065ceece41108a75c9d3763a95e4adb924
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="circular-reference-in-value-argument-not-supported"></a>value 引数の循環参照はサポートされません。
呼び出しが試行されて`JSON.stringify`が無効な値を使用します。 `value`引数、配列またはオブジェクトを循環参照が含まれています。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   引数の循環参照を削除します。  
  
## <a name="example"></a>例  
 に、この例では、コードによって、ランタイム エラーが発生`john`への参照を持つ`mary`と`mary`への参照を持つ`john`します。 削除するには、循環参照を削除するか、または設定解除プロパティ`brother`から、`mary`オブジェクトまたは`sister`プロパティから、`john`オブジェクト。  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>関連項目  
 [JSON オブジェクト](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse 関数](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript ランタイム エラー](../../javascript/reference/javascript-run-time-errors.md)