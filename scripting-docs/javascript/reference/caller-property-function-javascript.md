---
title: "caller プロパティ (Function) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: caller
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- caller property
- function calls, functions that are executing
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c6eef1b8304612c2ed16a4cc389bf3b2a28b70f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="caller-property-function-javascript"></a>caller プロパティ (Function) (JavaScript)
現在の関数を呼び出した関数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
functionName.caller  
```  
  
## <a name="remarks"></a>コメント  
 `functionName`オブジェクトのいずれかの名前が関数を実行します。  
  
 `caller`プロパティが定義されている場合にのみ、関数の関数が実行されています。 関数が呼び出された場合、上からのレベル、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]プログラム、`caller`含む`null`です。  
  
 場合、`caller`プロパティが文字列のコンテキストで使用では、結果は同じに`functionName`.`toString`、つまり、関数の逆コンパイルされたテキストを表示します。  
  
 `caller` プロパティの使用例を次に示します。  
  
```JavaScript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [function ステートメント](../../javascript/reference/function-statement-javascript.md)