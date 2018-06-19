---
title: if... else ステートメント (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- else_JavaScriptKeyword
- if_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- if statement, if...else
- loop structures, if...else statements
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fad12b970f69a15040acb59195f957a2a6eec3e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637332"
---
# <a name="ifelse-statement-javascript"></a>if...else ステートメント (JavaScript)
式の値に応じてステートメント グループを条件付きで実行します。  
  
## <a name="syntax"></a>構文  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## <a name="parameters"></a>パラメーター  
 `condition1`  
 必須です。 ブール式。 場合`condition1`は`null`または`undefined`、`condition1`として扱われる`false`です。  
  
 `statement1`  
 省略可能です。 場合に実行されるステートメント`condition1`は**true**です。 複合ステートメントにすることもできます。  
  
 `condition2`  
 評価する条件です。  
  
 `statement2`  
 省略可能です。 場合に実行されるステートメント`condition2`は`true`します。 複合ステートメントにすることもできます。  
  
 `statement3`  
 両方`condition1`と`condition2`は`false`、このステートメントを実行します。  
  
## <a name="example"></a>例  
 次のコードは、使用する方法を示しています。 `if`、 `if else`、および`else`です。  
  
 囲むことをお勧め`statement1`と`statement2`中かっこ ({}) わかりやすくするための不注意によるエラーを回避するとします。  
  
```JavaScript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [条件 (三項) 演算子 (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)