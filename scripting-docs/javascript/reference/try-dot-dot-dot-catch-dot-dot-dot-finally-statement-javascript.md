---
title: try… catch... 最後にステートメント (JavaScript) |Microsoft ドキュメント
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
- try_JavaScriptKeyword
- finally_JavaScriptKeyword
- catch_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- try-catch exception handling, finally block
- try-catch exception handling, about try-catch exception handling
- try-catch exception handling, catch block
- try-catch exception handling
ms.assetid: b7a0a54e-dfaa-4e41-bf25-bcaa43e601fb
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b05f15e593aeb7cb921f6237fad30b589cfdfe66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641732"
---
# <a name="trycatchfinally-statement-javascript"></a>try...catch...finally ステートメント (JavaScript)
あるブロックでスローされたエラーが別のブロックで処理されるコード ブロックを設定します。 `try` ブロック内でスローされたエラーは、`catch` ブロックでキャッチされます。 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]。  
  
## <a name="syntax"></a>構文  
  
```  
try {  
    tryStatements  
}  
catch(exception){  
    catchStatements  
}  
finally {  
    finallyStatements  
}  
```  
  
## <a name="parameters"></a>パラメーター  
 `tryStatements`  
 必須です。 エラーが発生する可能性のあるステートメントを指定します。  
  
 `exception`  
 必須です。 任意の変数名を指定します。 `exception` の初期値は、スローされたエラーの値です。  
  
 `catchStatements`  
 省略可能です。 関連付けられた `tryStatements` で発生するエラーを処理するステートメントを指定します。  
  
 `finallyStatements`  
 省略可能です。 他のエラー処理がすべて発生すると無条件に実行されるステートメントを指定します。  
  
## <a name="remarks"></a>コメント  
 `try...catch...finally` ステートメントでは、コード内の所定のブロックで発生する可能性のあるエラーの一部またはすべてに対して、コードを実行しながらエラー処理を実行できます。 処理されないエラーが発生すると、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は通常のエラー メッセージを表示します。  
  
 `try` ブロックは、エラーを発生させる可能性のあるコードを含みます。`catch` ブロックは、エラーの一部またはすべてを処理するコードを含みます。 `try` ブロックでエラーが発生すると、プログラムの制御が `catch` ブロックに渡されます。 `exception` の値は、`try` ブロックで発生したエラーの値です。 エラーが発生しない場合、`catch` ブロックのコードは実行されません。  
  
 `throw` を使用してエラーを次のレベルまで渡して、エラーを再スローできます。  
  
 `try` ブロックのすべてのステートメントが実行され、`catch` ブロックでのエラー処理が完了すると、エラーが処理されたかどうかに関係なく `finally` ブロックのステートメントが実行されます。 内のコード、`finally`ブロックが処理されないエラーが発生した場合を除きを実行することが保証 (内の実行時エラーなど、**キャッチ**ブロック) します。  
  
## <a name="example"></a>例  
 `ReferenceError` 例外をスローし、エラーの名前およびそのメッセージを表示する例を次に示します。  
  
```JavaScript  
try {  
    addalert("bad call");  
}  
catch(e) {  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF);  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
  
// Output:  
Error Message: 'addalert' is undefined  
Error Code: 5009  
Error Name: ReferenceError  
  
```  
  
## <a name="example"></a>例  
 次の例では、エラーを再スローする方法と、入れ子になった `try...catch` ブロックの実行を示しています。 入れ子になった `try` ブロックからスローされたエラーは、入れ子になった `catch` ブロックに渡されます。ここで、エラーが再スローされます。 入れ子になった `finally` ブロックが実行された後、外側の `catch` ブロックがエラーを処理し、最後に外側の `finally` ブロックが実行されます。  
  
```JavaScript  
try {  
    document.write("Outer try running...<br/>");  
  
    try {  
        document.write("Nested try running...<br/>");  
        throw new Error(301, "an error");  
    }  
    catch (e) {  
        document.write ("Nested catch caught " + e.message + "<br/>");  
        throw e;  
    }  
    finally {  
        document.write ("Nested finally is running...<br/>");  
    }  
}  
catch (e) {  
    document.write ("Outer catch caught " + e.message + "<br/>");  
}  
finally {  
    document.write ("Outer finally running");  
}  
  
// Output:  
// Outer try running...  
// Nested try running...  
// Nested catch caught error from nested try  
// Nested finally is running...  
// Outer catch caught error from nested try  
// Outer finally running  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
> [!NOTE]
>  Internet Explorer 8 標準モード以降、**キャッチ**ブロックが必要なくなりました`finally`を実行します。  
  
## <a name="see-also"></a>関連項目  
 [throw ステートメント](../../javascript/reference/throw-statement-javascript.md)   
 [スクリプト Junkie 構成ウィザードのサンプル アプリ](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)