---
title: "name プロパティ (Error) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "name"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Name プロパティ"
  - "name プロパティ, エラー名"
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# name プロパティ (Error) (JavaScript)
エラー名を返します。  
  
## 構文  
  
```  
  
errorObj.  
name  
  
```  
  
## パラメーター  
 `errorObj`  
 必須です。  `Error` オブジェクトのインスタンスを指定します。  
  
## 解説  
 **name** プロパティは、エラーの名前または例外種別を返します。  ランタイム エラーが発生すると、次に示すネイティブの例外種別の 1 つが name プロパティに設定されます。  
  
|例外の種類|意味|  
|-----------|--------|  
|ConversionError|このエラーは、オブジェクトを変換不可能な対象に変換しようとしたときに発生します。|  
|RangeError|関数に範囲外の引数を指定したときに、このエラーが発生します。  たとえば、有効な正の整数でない長さの `Array` オブジェクトを作成しようとすると、このエラーが発生します。|  
|ReferenceError|無効な参照が検出されたときに、このエラーが発生します。  たとえば、あるはずの参照が `null` だったときに、このエラーが発生します。|  
|RegExpError|正規表現でコンパイル エラーがあるときに、このエラーが発生します。  ただし、正規表現が正常にコンパイルされた後は、このエラーは発生しません。  たとえば、正規表現のパターンを宣言するときの構文が無効である場合や、フラグが **i**、**g**、または **m** 以外である場合、または同じフラグが複数個含まれる場合などに、このエラーが発生します。|  
|SyntaxError|ソース テキストを解析して、そのソース テキストの構文が正しくないときに、このエラーが発生します。  たとえば、`eval` 関数の呼び出しで無効なプログラム テキストを引数として指定したときに、このエラーが発生します。|  
|TypeError|オペランドの実際の型が、既定の型と一致しないときに、このエラーが発生します。  たとえば、関数の呼び出し対象がオブジェクトではない場合や、その呼び出しをサポートしていない場合にこのエラーが発生します。|  
|URIError|無効な URI \(Uniform Resource Indicator\) が検出されたときに、このエラーが発生します。  たとえば、エンコードまたはデコードされている文字列に無効な文字が見つかると、このエラーが発生します。|  
  
## 使用例  
 TypeError 例外をスローし、エラーの名前およびそのメッセージを表示する例を次に示します。  
  
```javascript  
try  
{  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## 使用例  
 このコードによって、次のような出力が生成されます。  
  
```javascript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **対象**: [Error オブジェクト](../../javascript/reference/error-object-javascript.md)  
  
## 参照  
 [description プロパティ \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [message プロパティ \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [number プロパティ \(Error\)](../../javascript/reference/number-property-error-javascript.md)