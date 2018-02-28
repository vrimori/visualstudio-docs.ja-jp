---
title: "文字列オブジェクト (JavaScript) |Microsoft ドキュメント"
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
- String_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object
- String object, overview
ms.assetid: 8063ecd5-5778-4e87-b985-b21420171914
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d58f567bb301b29324fee8ed75fc95fd1a4791ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="string-object-javascript"></a>String オブジェクト (JavaScript)
テキスト文字列を表すオブジェクトです。このオブジェクトを使用すると、各種文字列操作、文字列の書式設定、文字列内の一部分の取得、文字列内での指定した文字列の検索などを行うことができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
newString = new String(["stringLiteral"])  
```  
  
## <a name="parameters"></a>パラメーター  
 `newString`  
 必須です。 `String` オブジェクトを代入する変数名を指定します。  
  
 `stringLiteral`  
 省略可能です。 任意の Unicode 文字グループ。  
  
## <a name="remarks"></a>コメント  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] にはエスケープ シーケンスが用意されており、直接入力できない文字を文字列として使用できます。 たとえば、`\t` はタブ文字を指定します。 詳細については、「[特殊文字](../../javascript/advanced/special-characters-javascript.md)」を参照してください。  
  
## <a name="string-literals"></a>文字列リテラル。  
 A*文字列リテラル*一重引用符または二重引用符で囲まれた 0 個以上の文字です。 文字列リテラルには、`string` のプライマリ (プリミティブ) データ型があります。 A*文字列オブジェクト*を使用して作成された、 [new 演算子](../../javascript/reference/new-operator-decrementjavascript.md)のデータ型を持つ`Object`します。  
  
 文字列リテラルのデータ型が `String` のオブジェクトと同じではない例を次に示します。  
  
```JavaScript  
var strLit = "This is a string literal.";  
var strObj = new String("This is a string object.");  
  
document.write(typeof strLit);  
document.write("<br/>");  
document.write(typeof strObj);  
// Output:  
// string  
// object  
```  
  
## <a name="methods-for-string-literals"></a>文字列リテラルのメソッド  
 文字列リテラルのメソッドを呼び出すと、一時的に文字列のラッパー オブジェクトに変換されます。 文字列リテラルは、その作成に `new` 演算子が使用されているかのように扱われます。  
  
 `toUpperCase` メソッドを文字列リテラルに適用する例を次に示します。  
  
```JavaScript  
var strLit = "This is a string literal.";  
  
var result1 = strLit.toUpperCase();  
  
var result2 = (new String(strLit)).toUpperCase();  
  
document.write(result1);  
document.write("<br/>");  
document.write(result2);  
// Output:   
// THIS IS A STRING LITERAL.  
// THIS IS A STRING LITERAL.  
```  
  
## <a name="accessing-an-individual-character"></a>個々の文字へのアクセス  
 文字列の個々の文字には、読み取り専用の配列インデックス付きプロパティとしてアクセスできます。 この機能は、[!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] で導入されました。 文字列の個々の文字にアクセスする例を次に示します。  
  
```JavaScript  
var str = "abcd";  
var result = str[2];  
document.write (result);  
// Output: c  
  
var result = "the"[0];  
document.write(result);  
// Output: t  
```  
  
## <a name="requirements"></a>要件  
 `String Object` は、[!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)] で導入されました。 次の一覧にあるメンバーの一部は、それ以降のバージョンで導入されています。  
  
<a name="js56jsobjstringprop"></a>   
## <a name="properties"></a>プロパティ  
 `String` オブジェクトのプロパティを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[constructor プロパティ](../../javascript/reference/constructor-property-string.md)|オブジェクトを作成する関数を指定します。|  
|[length プロパティ (String)](../../javascript/reference/length-property-string-javascript.md)|`String` オブジェクトの長さを返します。|  
|[prototype プロパティ](../../javascript/reference/prototype-property-string.md)|指定されたオブジェクトのクラスのプロトタイプへの参照を返します。|  
  
## <a name="functions"></a>関数  
 `String` オブジェクトの関数を次の表に示します。  
  
|関数|説明|  
|--------------|-----------------|  
|[String.fromCharCode 関数](../../javascript/reference/string-fromcharcode-function-javascript.md)|1 つ以上の Unicode のコード値から 1 つの文字列を作成します。|  
|[String.fromCodePoint 関数](../../javascript/reference/string-fromcodepoint-function-javascript.md)|Unicode UTF-16 コード ポイントに関連付けられた文字列を返します。|  
|[String.raw 関数](../../javascript/reference/string-raw-function-javascript.md)|テンプレート文字列の未加工の文字列形式を返します。|  
  
<a name="js56jsobjstringmeth"></a>   
## <a name="methods"></a>メソッド  
 `String` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[anchor メソッド](../../javascript/reference/html-tag-methods-javascript.md)|テキストを NAME 属性のある HTML アンカーで囲みます。|  
|[big メソッド](../../javascript/reference/html-tag-methods-javascript.md)|HTML の配置\<BIG > テキスト タグで囲みます。|  
|[blink メソッド](../../javascript/reference/html-tag-methods-javascript.md)|HTML の配置\<BLINK > テキスト タグで囲みます。|  
|[bold メソッド](../../javascript/reference/html-tag-methods-javascript.md)|HTML の配置\<B > テキスト タグで囲みます。|  
|[charAt メソッド](../../javascript/reference/charat-method-string-javascript.md)|指定されたインデックス番号の位置にある文字を返します。|  
|[charCodeAt メソッド](../../javascript/reference/charcodeat-method-string-javascript.md)|指定された文字の Unicode でのコード値を返します。|  
|[codePointAt メソッド](../../javascript/reference/codepointat-method-string-javascript.md)|Unicode UTF-16 の文字のコード ポイントを返します。|  
|[concat メソッド (String)](../../javascript/reference/concat-method-string-javascript.md)|指定された 2 つの文字列を連結した文字列を返します。|  
|[endsWith メソッド](../../javascript/reference/endswith-method-string-javascript.md)|文字列または部分文字列が渡された文字列で終わるかどうかを示すブール値を返します。|  
|[includes メソッド](../../javascript/reference/includes-method-string-javascript.md)|渡された文字列が文字列オブジェクトに含まれているかどうかを示すブール値を返します。|  
|[fixed メソッド](../../javascript/reference/html-tag-methods-javascript.md)|HTML の配置\<TT > テキスト タグで囲みます。|  
|[fontcolor メソッド](../../javascript/reference/html-tag-methods-javascript.md)|HTML の配置\<フォント > テキストの周囲の色の属性を持つタグ。|  
|[fontsize メソッド](../../javascript/reference/html-tag-methods-javascript.md)|HTML の配置\<フォント > テキストの周辺の SIZE 属性を持つタグ。|  
|[hasOwnProperty メソッド](../../javascript/reference/hasownproperty-method-object-javascript.md)|指定した名前のプロパティがオブジェクトにあるかどうかを表すブール値を返します。|  
|[indexOf メソッド (String)](../../javascript/reference/indexof-method-string-javascript.md)|文字列内で最初に見つかった部分文字列の文字位置を返します。|  
|[isPrototypeOf メソッド](../../javascript/reference/isprototypeof-method-object-javascript.md)|オブジェクトが、別のオブジェクトのプロトタイプ チェーンに存在するかどうかを表すブール値を返します。|  
|[italics メソッド](../../javascript/reference/html-tag-methods-javascript.md)|HTML の配置\<I > テキスト タグで囲みます。|  
|[lastIndexOf メソッド (String)](../../javascript/reference/lastindexof-method-string-javascript.md)|文字列内で最後に見つかった部分文字列を返します。|  
|[link メソッド](../../javascript/reference/html-tag-methods-javascript.md)|テキストを HREF 属性付きの HTML アンカーで囲みます。|  
|[localeCompare メソッド](../../javascript/reference/localecompare-method-string-javascript.md)|現在のロケールにおいて、2 つの文字列が同じかどうかを表す値を返します。|  
|[match メソッド](../../javascript/reference/match-method-string-javascript.md)|指定されたを使用して、文字列内で検索**正規表現**オブジェクトし、配列として結果を返します。|  
|[normalize メソッド](../../javascript/reference/normalize-method-string-javascript.md)|指定した文字列の Unicode 正規化形式を返します。|  
|[propertyIsEnumerable メソッド](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|指定したプロパティがオブジェクトの一部であるかどうか、および列挙可能かどうかを表すブール値を返します。|  
|[repeat メソッド](../../javascript/reference/repeat-method-string-javascript.md)|元の文字列を指定した回数繰り返したものと同等の値を持つ、新しい文字列オブジェクトを返します。|  
|[replace メソッド](../../javascript/reference/replace-method-string-javascript.md)|正規表現を使用して文字列内のテキストを置換して結果を返します。|  
|[search メソッド](../../javascript/reference/search-method-string-javascript.md)|正規表現検索に一致する、最初の部分文字列の位置を返します。|  
|[slice メソッド (String)](../../javascript/reference/slice-method-string-javascript.md)|文字列の一部分を返します。|  
|[small メソッド](../../javascript/reference/html-tag-methods-javascript.md)|HTML の配置\<小さな > テキスト タグで囲みます。|  
|[split メソッド](../../javascript/reference/split-method-string-javascript.md)|文字列が複数の部分文字列に分割されたときの文字列の配列を返します。|  
|[startsWith メソッド](../../javascript/reference/startswith-method-string-javascript.md)|文字列または部分文字列が渡された文字列で開始するかどうかを示すブール値を返します。|  
|[strike メソッド](../../javascript/reference/html-tag-methods-javascript.md)|HTML の配置\<STRIKE > テキスト タグで囲みます。|  
|[sub メソッド](../../javascript/reference/html-tag-methods-javascript.md)|HTML の配置\<SUB > テキスト タグで囲みます。|  
|[substr メソッド](../../javascript/reference/substr-method-string-javascript.md)|文字列内の、指定位置からの指定された長さを持つ部分を返します。|  
|[substring メソッド](../../javascript/reference/substring-method-string-javascript.md)|`String` オブジェクト内の指定された位置にある部分文字列を返します。|  
|[sup メソッド](../../javascript/reference/html-tag-methods-javascript.md)|HTML の配置\<SUP > テキスト タグで囲みます。|  
|[toLocaleLowerCase メソッド](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|ホスト環境の現在のロケールに従って、すべての英字を小文字に変換した文字列を返します。|  
|[toLocaleString メソッド](../../javascript/reference/tolocalestring-method-object-javascript.md)|現在のロケールを使用して、文字列に変換されたオブジェクトを返します。|  
|[toLocaleUpperCase メソッド](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|ホスト環境の現在のロケールに従って、すべての英字を大文字に変換した文字列を返します。|  
|[toLowerCase メソッド](../../javascript/reference/tolowercase-method-javascript.md)|すべての英字を小文字に変換した文字列を返します。|  
|[toString メソッド](../../javascript/reference/tostring-method-string-1.md)|文字列を返します。|  
|[toUpperCase メソッド](../../javascript/reference/touppercase-method-string-javascript.md)|すべての英字を大文字に変換した文字列を返します。|  
|[trim メソッド](../../javascript/reference/trim-method-string-javascript.md)|先頭および末尾の空白と行終端記号の文字を削除した文字列を返します。|  
|[valueOf メソッド](../../javascript/reference/valueof-method-string.md)|文字列を返します。|  
  
## <a name="see-also"></a>関連項目  
 [New 演算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [スクロール、パン、ズームのサンプル アプリ](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)