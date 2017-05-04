---
title: "テンプレート文字列 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# テンプレート文字列 (JavaScript)
[!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] では、テンプレート文字列を使用して、埋め込み式のある文字列リテラルを作成できます。  テンプレート文字列は、複数行の文字列の組み込みサポートも提供します。  
  
 テンプレート文字列を作成するには、単一引用符や二重引用符の代わりにアクサン グラーブ記号 \(バック ティックとも呼ばれる\) \(\`\) を使用して文字列を囲みます。  次のコード例は、単純なテンプレート文字列を示しています。  
  
```  
`Template strings can include 'single quotes' and "double quotes" inline.`  
  
```  
  
 テンプレート文字列には、改行文字 \(\\n\) を使用しないで改行を含めることができます。  
  
```  
`Template strings can include line breaks and don't need the linefeed character.`  
```  
  
 テンプレート文字列内にプレース ホルダーを指定するには、$ の文字を使用します。  構文は ${*式*} で、次の例に示されているように、*式* には変数や関数などの任意の JavaScript 式を指定できます。  
  
```  
var name = "Bob";  
var str = `Hello ${name}, how are you this fine ${partOfDay()}?`  
console.log(str);  
  
function partOfDay () {  
    var hour = new Date().getHours();  
  
    if (hours <= 12) {  
        return “morning”;  
    } else if (hours <= 5) {  
        return “afternoon”;  
    } else {  
        return “evening”;  
    }  
}  
  
// Output:  
// Hello Bob, how are you this fine afternoon?  
```  
  
 タグ付きテンプレート関数。これにより、テンプレート文字列の引数で呼び出される関数を使用して、テンプレート文字列の値を変更できます。  最初の引数は、それに含まれるテンプレート文字列式で区切られた文字列リテラルの配列で、2 番目の引数は、テンプレート文字列式の値を含む配列 \([Rest パラメーター](../../javascript/functions-javascript.md)\) です。  
  
 次の例では、タグ付きテンプレート関数 buildURL を使用して URL を作成します。  関数名の直後にテンプレート文字列を使用する構文になります。  
  
```  
function buildURL(strArray, ...valArray) {  
    var newUrl = strArray[0] + "ja-ja" + "/" + valArray[1] +  
    "/" + valArray[2];  
  
    return newUrl;  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
console.log(url);  
  
// Output:  
// http://msdn.microsoft.com/ja-ja/library/dn771551.aspx  
```  
  
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
>  また、[String.raw](../../javascript/reference/string-raw-function-javascript.md) 関数を使用して、テンプレート文字列の未加工の文字列形式を返すこともできます。  
  
## 参照  
 [JavaScript 言語リファレンス](../../javascript/javascript-language-reference.md)   
 [高度な JavaScript](../../javascript/advanced/advanced-javascript.md)