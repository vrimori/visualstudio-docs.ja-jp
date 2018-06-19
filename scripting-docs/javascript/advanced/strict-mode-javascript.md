---
title: 厳格モード (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1038
- VS.WebClient.Help.SCRIPT1050
- VS.WebClient.Help.SCRIPT1042
- VS.WebClient.Help.SCRIPT1041
- VS.WebClient.Help.SCRIPT1046
- VS.WebClient.Help.SCRIPT1045
- VS.WebClient.Help.SCRIPT1037
- VS.WebClient.Help.SCRIPT1039
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strict mode
- use strict
ms.assetid: 0f27022a-f41c-4504-965c-5a2701f342cd
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77ee7d54dd265026b2bf4c9af52a71cccf9a7675
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569572"
---
# <a name="strict-mode-javascript"></a>厳格モード (JavaScript)
厳格モードでは、より的確なエラー チェックがコードに導入されます。 厳格モードを使用すると、たとえば、暗黙的に宣言された変数を使用したり、読み取り専用のプロパティに値を割り当てたりすることはできません。また、拡張可能ではないオブジェクトにプロパティを追加することもできません。 制限内容は、この後の「[厳格モードのコードの制約](../../javascript/advanced/strict-mode-javascript.md#rest)」に示します。 厳密モードの詳細については、[ECMAScript 言語仕様第 5 版](http://www.ecma-international.org/publications/standards/Ecma-262.htm)を参照してください。  
  
> [!WARNING]
>  厳格モードは、Internet Explorer 10 より前のバージョンの Internet Explorer ではサポートされません。  
  
## <a name="declaring-strict-mode"></a>厳格モードの宣言  
 ファイル、プログラム、または関数の先頭に `"use strict";` を追加して、厳格モードを宣言できます。 この種類の宣言は*ディレクティブ プロローグ*と呼ばれます。 厳格モードの宣言のスコープは、コンテキストによって異なります。 グローバル コンテキスト (関数のスコープ外) で宣言されている場合は、プログラムのすべてのコードが厳格モードになります。 関数で宣言されている場合は、関数内のすべてのコードが厳格モードになります。 次の例では、すべてのコードは厳格モードであり、関数の外部での変数宣言によって、構文エラー "厳格モードで未定義の変数です" が発生します。  
  
```JavaScript  
"use strict";  
function testFunction(){  
    var testvar = 4;  
    return testvar;  
}  
  
// This causes a syntax error.  
testvar = 5;  
  
```  
  
 次の例では、`testFunction` 内のコードだけが厳格モードです。 関数の外部での変数宣言による構文エラーは発生しませんが、関数内で宣言すると構文エラーが発生します。  
  
```JavaScript  
function testFunction(){  
    "use strict";  
    // This causes a syntax error.  
    testvar = 4;  
    return testvar;  
}  
testvar = 5;  
  
```  
  
<a name="rest"></a>   
## <a name="restrictions-on-code-in-strict-mode"></a>厳格モードのコードの制約  
 次の表は、厳格モードで適用される最も重要な制約を示します。  
  
|||||  
|-|-|-|-|  
|**言語要素**|**制限**|**エラー**|**例**|  
|変数|宣言していない変数を使用する。|SCRIPT5042: 厳格モードで未定義の変数です|`testvar = 4;`|  
|読み取り専用のプロパティ|読み取り専用プロパティに書き込む。|SCRIPT5045: 厳格モードでは、読み取り専用プロパティに割り当てることはできません|`var testObj = Object.defineProperties({}, {     prop1: {         value: 10,         writable: false // by default     },     prop2: {         get: function () {         }     } }); testObj.prop1 = 20;  testObj.prop2 = 30;`|  
|拡張不能プロパティ|`extensible` 属性が `false` に設定されたオブジェクトにプロパティを追加する。|SCRIPT5046: 拡張できないオブジェクトのプロパティを作成することはできません|`var testObj = new Object();  Object.preventExtensions(testObj);  testObj.name = "Bob";`|  
|`delete`|変数、関数、または引数を削除する。<br /><br /> `configurable` 属性が `false` に設定されたプロパティを削除する。|SCRIPT1045: 厳格モードでは、\<式> で delete を呼び出すことはできません|`var testvar = 15; function testFunc() {}; delete testvar; delete testFunc;  Object.defineProperty(testObj, "testvar", {     value: 10,     configurable: false     }); delete testObj.testvar;`|  
|プロパティの複製|オブジェクト リテラルでプロパティを複数回定義する。|SCRIPT1046: 厳格モードでは、プロパティの複数定義は許可されません|`var testObj = {     prop1: 10,     prop2: 15,     prop1: 20 };`|  
|パラメーター名の複製|関数でパラメーター名を複数回使用する。|SCRIPT1038: 厳格モードでは、重複する仮パラメーター名は使用できません|`function testFunc(param1, param1) {     return 1; };`|  
|将来的に使用される予約済みのキーワード|将来的に使用される予約済みのキーワードを変数名や関数名として使用する。|SCRIPT1050: 将来の予約語を識別子に使用することはできません。 厳格モードでは、識別名が予約されています。|-                      `implements`<br /><br /> -                      `interface`<br /><br /> -                      `package`<br /><br /> -                      `private`<br /><br /> -                      `protected`<br /><br /> -                      `public`<br /><br /> -                      `static`<br /><br /> -                      `yield`|  
|8 進数|数値リテラルに 8 進数値を割り当てるか、8 進数値でエスケープを使用する。|SCRIPT1039: 厳格モードでは、8 進数リテラルとエスケープ文字は使用できません|`var testoctal = 010; var testescape = \010;`|  
|`this`|`this` の値が `null` または `undefined` の場合にグローバル オブジェクトに変換されない。||`function testFunc() {     return this; } var testvar = testFunc();`<br /><br /> 非厳格モードでは、`testvar` の値はグローバル オブジェクトですが、厳格モードでは値は `undefined` です。|  
|識別子としての `eval`|文字列 "eval" を識別子 (変数名、関数名、パラメーター名など) として使用することはできない。||`var eval = 10;`|  
|ステートメント内またはブロック内で宣言された関数|ステートメントまたはブロック内で関数を宣言することはできない。|SCRIPT1047: 厳格モードでは、関数宣言をステートメント内またはブロック内で入れ子にすることはできません。 関数宣言は、関数本体内の最上位のレベルまたは直接でのみ記述できます。|`var arr = [1, 2, 3, 4, 5]; var index = null; for (index in arr) {     function myFunc() {}; }`|  
|`eval` 関数内部で宣言された変数|`eval` 関数内で宣言されている変数をその関数外で使用することはできない。|SCRIPT1041: 厳格モードでの 'eval' の使用方法が無効です|`eval("var testvar = 10"); testvar = 15;`<br /><br /> 間接評価は可能ですが、`eval` 関数の外部で宣言されている変数を使用することはできません。<br /><br /> `var indirectEval = eval; indirectEval("var testvar = 10;"); document.write(testVar);`<br /><br /> このコードではエラー SCRIPT5009 が発生します。'testVar' が未定義です。|  
|識別子としての `Arguments`|文字列 "arguments" を識別子 (変数名、関数名、パラメーター名など) として使用することはできない。|SCRIPT1042: 厳格モードでの 'arguments' の使用方法が無効です|`var arguments = 10;`|  
|関数内の `arguments`|ローカルの `arguments` オブジェクトのメンバーの値は変更できない。||`function testArgs(oneArg) {     arguments[0] = 20; }`<br /><br /> 非厳格モードでは、`oneArg` の値を変更することによって `arguments[0]` パラメーターの値を変更し、`oneArg` と `arguments[0]` の両方の値を 20 にすることができます。 厳格モードでは、`arguments[0]` の値を変更しても `oneArg` の値には影響しません。これは、`arguments` オブジェクトが単なるローカル コピーであるためです。|  
|`arguments.callee`|使用できません。||`function (testInt) {     if (testInt-- == 0)         return;     arguments.callee(testInt--); }`|  
|`with`|使用できません。|SCRIPT1037: 厳格モードでは、'with' ステートメントは使用できません|`with (Math){     x = cos(3);     y = tan(7); }`|