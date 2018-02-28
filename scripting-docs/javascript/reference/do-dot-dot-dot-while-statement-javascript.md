---
title: "do...while ステートメント (JavaScript) |Microsoft ドキュメント"
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
- do_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- terminating loops
- loop structures, do and do-while
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 895d98a3de3a6691ce60bf0456bb838403619f88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="dowhile-statement-javascript"></a>do...while ステートメント (JavaScript)
1 回、ステートメント ブロックを実行し、条件式に評価されるまで、ループの実行を繰り返す`false`です。  
  
## <a name="syntax"></a>構文  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## <a name="parameters"></a>パラメーター  
 `statement`  
 必須です。 場合に実行されるステートメント`expression`は`true`します。 複合ステートメントにすることもできます。  
  
 `expression`  
 必須です。 ブール値に変換できる式`true`または`false`です。 場合`expression`は`true`ループがもう一度実行します。 場合`expression`は`false`ループは終了します。  
  
## <a name="remarks"></a>コメント  
 異なり、`while`ステートメント、`do...while`ループの条件付きの式が評価される前に 1 回実行します。  
  
 任意の行、`do...while`ブロックを使用することができます、`break`プログラム フローを終了するか、ループが発生するステートメントを使用できます、`continue`ステートメントに直接移動する、`while`式。  
  
## <a name="example"></a>例  
 次の例では、内のステートメントで、`do...while`ループ継続して実行している間、変数`i`10 未満です。  
  
```JavaScript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## <a name="example"></a>例  
 次の例では、ループ内のステートメントは、条件が満たされない場合でも 1 回実行されます。  
  
```JavaScript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [break ステートメント](../../javascript/reference/break-statement-javascript.md)   
 [continue ステートメント](../../javascript/reference/continue-statement-javascript.md)   
 [for ステートメント](../../javascript/reference/for-statement-javascript.md)   
 [データ型… ステートメントで](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while ステートメント](../../javascript/reference/while-statement-javascript.md)   
 [ラベル付きステートメント](../../javascript/reference/labeled-statement-javascript.md)