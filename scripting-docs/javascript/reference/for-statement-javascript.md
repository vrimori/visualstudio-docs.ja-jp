---
title: for ステートメント (JavaScript) |Microsoft ドキュメント
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
- for_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- loop structures, for statements
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7142dbb8c00a351918d0821c3ca7dba3d7b2acb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637142"
---
# <a name="for-statement-javascript"></a>for ステートメント (JavaScript)
指定された条件が true の場合に限りのステートメントのブロックを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## <a name="parameters"></a>パラメーター  
 `initialization`  
 省略可能です。 任意の式を指定します。 この式は、ループが実行される前に 1 回だけ実行されます。  
  
 `test`  
 省略可能です。 ブール式。 場合`test`は`true`、`statement`を実行します。 場合`test`場合`false`ループは終了します。  
  
 `increment`  
 省略可能です。 任意の式を指定します。 インクリメント式は、ループの各パスの最後に実行されます。  
  
 `statement`  
 省略可能です。 場合に実行されるステートメントを 1 つまたは複数`test`は**true**です。 複合ステートメントにすることもできます。  
  
## <a name="remarks"></a>コメント  
 通常使用する、`for`ループがある、既知の回数実行をループします。 A`for`ループは配列を反復処理して、順次処理を実行するために便利です。  
  
 条件式のテストは、ループの実行前にそのために発生、`for`ステートメントは、0 回以上を実行します。  
  
 任意の行、`for`ループ ステートメント ブロックを行うこともできます、 `break` 、ループを終了するステートメントを使用できる、`continue`ステートメント、ループの次のイテレーションに制御を転送します。  
  
## <a name="example"></a>例  
 次の例で、`for`ステートメントが次のようにかっこで囲んだのステートメントを実行します。  
  
-   最初に、変数の初期値`i`が評価されます。  
  
-   値と長い`i`が 9、小さい、`document.write`ステートメントが実行されると`i`が再評価されます。  
  
-   ときに`i`、9 よりも大きいが、条件が false になるし、ループの外側に制御が移ります。  
  
```JavaScript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## <a name="example"></a>例  
 すべての式の`for`ステートメントは省略可能です。 次の例で、`for`ステートメントは、無限ループを作成し、`break`ループを終了するステートメントを使用します。  
  
```JavaScript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [データ型… ステートメントで](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while ステートメント](../../javascript/reference/while-statement-javascript.md)