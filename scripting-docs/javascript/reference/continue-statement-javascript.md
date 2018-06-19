---
title: continue ステートメント (JavaScript) |Microsoft ドキュメント
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
- continue_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- continue statement
- loop structures, continue statement
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 391f919c4d06a6c529bfee34e21ca7238b3c63b7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636382"
---
# <a name="continue-statement-javascript"></a>continue ステートメント (JavaScript)
ループの現在の反復の実行を中止し、次の反復の実行を開始します。  
  
## <a name="syntax"></a>構文  
  
```  
continue [label];  
```  
  
## <a name="remarks"></a>コメント  
 省略可能な`label`引数を指定するステートメント`continue`適用されます。  
  
 使用することができます、`continue`ステートメント内でのみ、 `while`、 `do...while`、**の**、または`for...in`ループします。 実行する、`continue`ステートメントは、ループの現在のイテレーションを停止し、ループの先頭でプログラム フローが続行されます。 これは、さまざまな種類のループに次の影響があります。  
  
-   `while`および`do...while`ループがその条件をテストし、true の場合、ループをもう一度実行します。  
  
-   `for`ループは、それらのインクリメント式を実行し、テスト式が true の場合、ループをもう一度実行します。  
  
-   `for...in`ループを使用して、指定された変数の次のフィールドに進みます、ループをもう一度実行します。  
  
## <a name="examples"></a>例  
 この例では 1 ~ 9、ループが反復処理します。 間にあるステートメント`continue`との終了、`for`を使用するための本文はスキップされます、`continue`式と共にステートメント`(i < 5)`です。  
  
```JavaScript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 次のコードで、`continue`ステートメントを参照して、`for`前がループ、`Inner:`ラベル。 ときに`j`、24、`continue`ステートメントを`for`ループを使用して、次のイテレーションに移動します。 行ごとに 21 ~ 23 および 25 ~ 30 の数字を印刷します。  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [break ステートメント](../../javascript/reference/break-statement-javascript.md)   
 [do...while ステートメント](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for ステートメント](../../javascript/reference/for-statement-javascript.md)   
 [データ型… ステートメントで](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [ラベル付きステートメント](../../javascript/reference/labeled-statement-javascript.md)   
 [while ステートメント](../../javascript/reference/while-statement-javascript.md)