---
title: while ステートメント (JavaScript) |Microsoft ドキュメント
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
- while_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- loop structures, while statements
- while statement
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de64bf9181a0fc86a528fa7af21216b99530f217
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641252"
---
# <a name="while-statement-javascript"></a>while ステートメント (JavaScript)
指定された条件がなるまでステートメントまたは一連のステートメント実行`false`です。  
  
## <a name="syntax"></a>構文  
  
```  
while (expression) {  
    statements  
}   
```  
  
## <a name="parameters"></a>パラメーター  
 `expression`  
 必須です。 ループの各反復処理する前にチェックインされるブール式です。 場合`expression`は`true`ループを実行します。 場合`expression`は`false`ループは終了します。  
  
 `statements`  
 省略可能です。 場合に実行されるステートメントを 1 つまたは複数`expression`は`true`します。  
  
## <a name="remarks"></a>コメント  
 `while`ステートメント チェック`expression`ループを最初に実行する前にします。 場合`expression`は`false`現時点では、ループは実行されません。  
  
## <a name="example"></a>例  
 次の例は、`while` ステートメントの使用方法を示します。  
  
```JavaScript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [break ステートメント](../../javascript/reference/break-statement-javascript.md)   
 [continue ステートメント](../../javascript/reference/continue-statement-javascript.md)   
 [do...while ステートメント](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for ステートメント](../../javascript/reference/for-statement-javascript.md)   
 [for...in ステートメント](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)