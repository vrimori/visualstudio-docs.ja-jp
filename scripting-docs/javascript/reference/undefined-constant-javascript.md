---
title: "undefined 定数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- undefined
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- undefined property
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ba7fa8b160e4f5d954c8d6545da5fae41c2f74b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="undefined-constant-javascript"></a>undefined 定数 (JavaScript)
値が定義されていない、初期化されていない変数などです。  
  
## <a name="syntax"></a>構文  
  
```  
undefined  
```  
  
## <a name="remarks"></a>コメント  
 `undefined`定数のメンバーである、`Global`オブジェクト、およびスクリプト エンジンが初期化されたときに使用可能になります。 変数が宣言されましたが、初期化されていませんが場合、その値は**未定義**です。  
  
 変数が宣言されていない場合に比較できません`undefined`文字列"undefined"を変数の型を比較することができますが、します。  
  
 `undefined`定数にする場合に利用を明示的にはテストまたは未定義変数を設定します。  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`undefined`定数。  
  
```JavaScript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## <a name="requirements"></a>要件  
 `undefined`プロパティで導入された[!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)]、および読み取り専用に行った[!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)]です。  
  
 **適用されます**:[グローバル オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [typeof 演算子](../../javascript/reference/typeof-operator-decrementjavascript.md)