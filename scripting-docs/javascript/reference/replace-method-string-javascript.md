---
title: "replace メソッド (String) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: replace
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- replacing strings
- Replace method
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e78e17d4b9060a3a52498109a744c13cdf972abb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="replace-method-string-javascript"></a>replace メソッド (String) (JavaScript)
正規表現または検索文字列を使用して、文字列内のテキストを置換します。  
  
## <a name="syntax"></a>構文  
  
```  
  
stringObj. replace(rgExp, replaceText)  
```  
  
## <a name="parameters"></a>パラメーター  
 `stringObj`  
 必須です。 置換対象となる `String` オブジェクトの名前またはリテラル文字列を指定します。 この文字列がによって変更されない、**置換**メソッドです。 むしろ、このメソッドの戻り値が、置換によって生成される文字列です。  
  
 `rgExp`  
 必須です。 インスタンス、**正規表現**正規表現パターンおよび適用できるフラグを含むオブジェクト。 正規表現を表す `String` オブジェクトまたはリテラル文字列である場合もあります。 場合`rgExp`のインスタンスではない、**正規表現**オブジェクト、文字列に変換されますと結果の正確な検索が行われた; は行われません、文字列を正規表現に変換します。  
  
 `replaceText`  
 必須です。 `String` で、`rgExp` と一致した部分と置き換えるテキストを格納する `stringObj` オブジェクトまたはリテラル文字列を指定します。 [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 5.5 以降では、`replaceText` 引数で、置換するテキストを返す関数を指定することもできます。  
  
## <a name="return-value"></a>戻り値  
 結果、**置換**メソッドのコピーである`stringObj`指定された置換を終えた後です。  
  
## <a name="remarks"></a>コメント  
 次の表にある変数を使用して、最後に検出した一致やその文字列を指定できます。 一致変数は、テキストの置換処理において、対象を動的に指定する必要がある場合に使用します。  
  
|文字|説明|  
|----------------|-------------|  
|**$$**|`$` ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降)|  
|**$&**|`stringObj` でパターンが完全に一致した部分を指定します。 ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降)|  
|`$``|部分を表します`stringObj`で説明されている一致の直前まで **$&**です。 ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降)|  
|`$'`|部分を表します`stringObj`で説明されている一致に依存している **$&**です。 ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降)|  
|`$`  ***n***|*n*番目のキャプチャのサブマッチ場所 *n* は 1 ~ 9 の 1 つの 10 進数字です。 ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降)|  
|`$`  ***nn***|*nn* Th、サブマッチをキャプチャする場所 *nn* はの 01 ~ 99 の 2 桁の 10 進数。 ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降)|  
  
 場合`replaceText`は、次をそれぞれ一致する文字列、関数が呼び出された関数の場合、 *m* + 3 個の引数を*m*残されたキャプチャ内のかっこの数は、`rgExp`です。 1 個目の引数は一致したサブ文字列です。 次*m*引数は、検索結果そのものです。 引数*m*内のオフセットが +`stringObj`一致した位置、および引数*m* + 3 は`stringObj`します。 結果は、該当する関数呼び出しの戻り値をそれぞれ一致する文字列と置換した文字列値で返されます。  
  
 **置換**メソッドは、グローバルのプロパティを更新`RegExp`オブジェクト。  
  
## <a name="example"></a>例  
 次の例では、使用、**置換**メソッドに置換するすべての"the"を"a"です。  
  
```JavaScript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 さらに、**置換**メソッドは、パターンに一致する文字列どうしを置換できます。 文字列の中の単語の各ペアを入れ替える例を次に示します。  
  
```JavaScript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumps lazy the dog.  
```  
  
 置換テキストを返す関数を使用する方法を次に示します。この例は [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] 以降で動作します。 これは、摂氏変換によって、「F」に続くすべての数値のインスタンスを置き換えます。  
  
```JavaScript  
function f2c(s1) {  
    // Initialize pattern.  
    var test = /(\d+(\.\d*)?)F\b/g;  
  
    // Use a function for the replacement.  
    var s2 = s1.replace(test,  
      function($0,$1,$2)  
           {   
           return((($1-32) * 5/9) + "C");  
           }  
        )  
    return s2;  
}  
document.write(f2c("Water freezes at 32F and boils at 212F."));  
  
// Output: Water freezes at 0C and boils at 100C.  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**:[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [exec メソッド (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match メソッド (String)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)   
 [search メソッド (String)](../../javascript/reference/search-method-string-javascript.md)   
 [test メソッド (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [正規表現プログラミング (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [代替と部分式 (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [前方参照 (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [HTML5 ドラッグ アンド ドロップのサンプル アプリ](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)