---
title: エラー オブジェクト (JavaScript) |Microsoft ドキュメント
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
- Error
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Error object
ms.assetid: 0b27d6ec-3997-4e91-a6c0-5afbaf494db7
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efc03f13a501a1a13a2e7f3eea000b406559f30b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637102"
---
# <a name="error-object-javascript"></a>Error オブジェクト (JavaScript)
エラーに関する情報を格納します。  
  
## <a name="syntax"></a>構文  
  
```  
  
      errorObj = new Error()  
errorObj = new Error([number])  
errorObj = new Error([number[, description]])  
```  
  
## <a name="parameters"></a>パラメーター  
 `errorObj`  
 必須です。 `Error` オブジェクトを代入する変数名を指定します。 変数代入は `throw` ステートメントを使用してエラーを作成するときには省略されます。  
  
 `number`  
 省略可能です。 エラーに割り当てられる数値を指定します。 省略した場合は 0 です。  
  
 `description`  
 省略可能です。 エラーを説明する短い文字列を指定します。 省略した場合は空の文字列です。  
  
## <a name="remarks"></a>コメント  
 ランタイム エラーが発生した場合はいつでも、エラーを記述する `Error` オブジェクトのインスタンスが作成されます。 このインスタンスには、エラー (`description` プロパティ) およびエラー番号 (`number` プロパティ) の説明を含む 2 種類の組み込みプロパティがあります。 詳細については、次を参照してください。 [JavaScript ランタイム エラー](../../javascript/reference/javascript-run-time-errors.md)です。  
  
 エラー番号は 32 ビット値です。 上位の 16 ビット ワードは機能識別符号です。下位のワードは実際のエラー コードです。  
  
 `Error` オブジェクトは、前の構文を使用して明示的に作成することも、`throw` ステートメントを使用してスローすることもできます。 どちらの場合も、選択した任意のプロパティを追加して、`Error` オブジェクトの機能を拡張できます。  
  
 通常、ローカル変数で作成される、 **try… catch**ステートメントを暗黙的に作成された参照`Error`オブジェクト。 したがって、エラー番号と説明を任意の方法で使用できます。  
  
## <a name="example"></a>例  
 次のコードは、`Error` オブジェクトの使用例です。  
  
```  
function checkInput(x) {  
    try  
    {  
        if (isNaN(parseInt(x))) {  
            throw new Error("Input is not a number.");  
        }  
    }  
    catch(e)  
    {  
        document.write(e.description);  
    }  
}  
  
checkInput("not a number");  
```  
  
## <a name="example"></a>例  
 次の例は、暗黙的に作成された `Error` オブジェクトの使用方法を示します。  
  
```JavaScript  
try  
   {  
   // Cause an error.  
   x = y;  
   }  
catch(e)  
   {  
      document.write(e);  
      document.write ("<br />");  
  
      document.write ("Number: ");  
      document.write (e.number & 0xFFFF);  
      document.write ("<br />");  
  
      document.write ("Facility Code: ");  
      document.write(e.number>>16 & 0x1FFF);  
      document.write ("<br />");  
  
      document.write ("Description: ");  
      document.write (e.description);  
   }  
  
// Output:  
// ReferenceError: 'y' is undefined  
// Number: 5009  
// Facility Code: 10  
// Description: 'y' is undefined  
  
```  
  
## <a name="methods"></a>メソッド  
 [toString メソッド (エラー)](../../javascript/reference/tostring-method-error.md) &#124;です。[valueOf メソッド (Date)](../../javascript/reference/valueof-method-date.md)  
  
## <a name="properties"></a>プロパティ  
 [constructor プロパティ (Error)](../../javascript/reference/constructor-property-error.md) &#124;です。[description プロパティ](../../javascript/reference/description-property-error-javascript.md)&#124;です。[メッセージ プロパティ](../../javascript/reference/message-property-error-javascript.md)&#124;です。[name プロパティ](../../javascript/reference/name-property-error-javascript.md)&#124;です。[number プロパティ](../../javascript/reference/number-property-error-javascript.md)&#124;です。[prototype プロパティ (Error)](../../javascript/reference/prototype-property-error.md) &#124;です。[stack プロパティ (Error)](../../javascript/reference/stack-property-error-javascript.md) &#124;です。[stackTraceLimit プロパティ (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [New 演算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [throw ステートメント](../../javascript/reference/throw-statement-javascript.md)   
 [try… catch... 最後にステートメント](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [var ステートメント](../../javascript/reference/var-statement-javascript.md)   
 [Hilo JavaScript のサンプル アプリ (Windows ストア)](http://hilojs.codeplex.com/SourceControl/latest)