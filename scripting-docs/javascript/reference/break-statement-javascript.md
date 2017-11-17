---
title: "break ステートメント (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: break_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- break statement
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f085a4e51309bf9a060e9ffa352c6ae85924237
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="break-statement-javascript"></a>break ステートメント (JavaScript)
終了、現在のループまたはと組み合わせて、 `label`、関連するステートメントを終了します。  
  
## <a name="syntax"></a>構文  
  
```  
break [label];  
```  
  
## <a name="remarks"></a>コメント  
 省略可能な`label`引数は、ステートメントから切断されることのラベルを指定します。  
  
 通常使用する、`break`ステートメントで`switch`ステートメントと`while`、 `for`、 `for...in`、または`do...while`ループします。 最も頻繁に使用する、`label`引数`switch`がステートメントで使用できます、ステートメントはすべて単純型または複合かどうか。  
  
 実行する、`break`ステートメントは、現在のループまたはステートメントから終了し、直後のステートメントでスクリプトの実行を開始します。  
  
## <a name="examples"></a>例  
 この例では、カウンターは設定 1 から 99 までカウントするにはただし、`break`ステートメント 14 カウント、ループを終了します。  
  
```JavaScript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 次のコードで、`break`ステートメントを参照して、`for`前がループ、`Inner:`ステートメントです。 ときに`j`24、等しく、`break`ステートメントにより、プログラム フローをループを終了します。 行ごとに 21 ~ 23 の数値を印刷します。  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [continue ステートメント](../../javascript/reference/continue-statement-javascript.md)   
 [do...while ステートメント](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for ステートメント](../../javascript/reference/for-statement-javascript.md)   
 [データ型… ステートメントで](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [ラベル付きステートメント](../../javascript/reference/labeled-statement-javascript.md)   
 [while ステートメント](../../javascript/reference/while-statement-javascript.md)