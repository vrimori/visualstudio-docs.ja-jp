---
title: "条件 (三項) 演算子 (?:)(JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '?:'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional operators
- conditional (Ternary) operator
- ternary
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dc34b5c633cfc02219cb01061e1aaa017e0f7f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-ternary-operator--javascript"></a>条件 (三項) 演算子 (?:) (JavaScript)
条件に応じて 2 つの式のどちらかを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
test ? expression1 : expression2  
```  
  
## <a name="parameters"></a>パラメーター  
 `test`  
 任意のブール式。  
  
 `expression1`  
 `test` が `true` の場合は式が返されます。 コンマ式も使用できます。  
  
 `expression2`  
 `test` が `false` の場合は式が返されます。 複数の式がコンマ式によってリンクされている可能性があります。  
  
## <a name="remarks"></a>コメント  
 `?:` 演算子を使用して、`if...else` ステートメントと同じ処理を簡単に実行できます。 この演算子は通常、`if...else` ステートメントが記述しづらい長い式の 1 部として使用されます。 例:  
  
```JavaScript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 例では、"おや evening"を含む文字列を作成します。 午後 6 時以降後の場合は。 上記の例は、`if...else` ステートメントを使用すると、次のようになります。  
  
```JavaScript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [if... else ステートメント](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [スクリプト Junkie 構成ウィジェットのサンプル アプリ](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)