---
title: "テンプレート文字列 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7b6aa430fd4f958c5519093b85d399060b6031a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="template-strings-javascript"></a>テンプレート文字列 (JavaScript)
[!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] では、テンプレート文字列を使用して、埋め込み式のある文字列リテラルを作成できます。 テンプレート文字列は、複数行の文字列の組み込みサポートも提供します。  
  
 テンプレート文字列を作成するには、単一引用符や二重引用符の代わりにアクサン グラーブ記号 (バック ティックとも呼ばれる) (`) を使用して文字列を囲みます。 次のコード例は、単純なテンプレート文字列を示しています。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 テンプレート文字列には、改行文字 (\n) を使用しないで改行を含めることができます。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 テンプレート文字列内にプレース ホルダーを指定するには、$ の文字を使用します。 構文は ${*式*} で、次の例に示されているように、*式* には変数や関数などの任意の JavaScript 式を指定できます。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 タグ付きテンプレート関数。これにより、テンプレート文字列の引数で呼び出される関数を使用して、テンプレート文字列の値を変更できます。 最初の引数は、それに含まれるテンプレート文字列式で区切られた文字列リテラルの配列で、2 番目の引数は、テンプレート文字列式の値を含む配列 ([Rest パラメーター](../../javascript/functions-javascript.md)) です。  
  
 次の例では、タグ付きテンプレート関数 buildURL を使用して URL を作成します。 関数名の直後にテンプレート文字列を使用する構文になります。  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 渡された未加工の文字列にアクセスする必要がある場合、タグ付きテンプレート関数に渡される最初の引数は、渡された文字列の未加工の文字列形式を返す `raw` プロパティをサポートします。  
  
```  
function buildURL(strArray, ...valArray) {  
    console.log(strArray.raw);  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
// Ouput:  
// http://msdn.microsoft.com/  
// /  
// en-us  
// library  
```  
  
> [!NOTE]
>  また、[String.raw](../../javascript/reference/string-raw-function-javascript.md) 関数を使って、テンプレート文字列の未加工の文字列形式を返すこともできます。  
  
## <a name="see-also"></a>関連項目  
 [JavaScript 言語リファレンス](../../javascript/javascript-language-reference.md)   
 [高度な JavaScript](../../javascript/advanced/advanced-javascript.md)