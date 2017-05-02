---
title: "HTML Tag メソッド (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "anchor メソッド [JavaScript]"
  - "big メソッド [JavaScript]"
  - "blink メソッド [JavaScript]"
  - "bold メソッド [JavaScript]"
  - "fixed メソッド [JavaScript]"
  - "fontcolor メソッド [JavaScript]"
  - "fontsize メソッド [JavaScript]"
  - "HTML Tag メソッド [JavaScript]"
  - "italics メソッド [JavaScript]"
  - "link メソッド [JavaScript]"
  - "small メソッド [JavaScript]"
  - "sub メソッド [JavaScript]"
  - "sup メソッド [JavaScript]"
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# HTML Tag メソッド (JavaScript)
HTML タグのメソッドを使用すると、`String` オブジェクトのテキストの周囲に HTML 要素を配置できます。  
  
## 構文  
 各 HTML タグ メソッドの構文と説明を次の表に示します。  
  
 構文列の `string1` は `String` オブジェクトまたはリテラルです。  
  
 標準列は、HTML 4 についての [W3C \(World Wide Web Consortium\)](http://go.microsoft.com/fwlink/?LinkId=199553) 勧告を示します。  "使用回避" は、スタイル シートを優先的に使用し、その HTML 要素の使用を避けるように促しています。  
  
|構文|メソッドの説明|パラメーターの説明|標準|  
|--------|-------------|---------------|--------|  
|`string1`.anchor\(`name`\)|テキストを HTML の NAME 属性付きの \<A\> タグと \<\/A\> タグで囲みます。|`name` パラメーターは、HTML の \<A\> タグと \<\/A\> タグの NAME 属性に配置されるテキストです。||  
|`string1`.big\(\)|テキストを HTML の \<BIG\> タグと \<\/BIG\> タグで囲みます。||使用回避|  
|`string1`.blink\(\)|テキストを HTML の \<BLINK\> タグと \<\/BLINK\> タグで囲みます。  \<BLINK\> タグは、Internet Explorer ではサポートされていません。||非標準|  
|`string1`.bold\(\)|テキストを HTML の \<B\> タグと \<\/B\> タグで囲みます。||使用回避|  
|`string1`.fixed\(\)|テキストを HTML の \<TT\> タグと \<\/TT\> タグで囲みます。||使用回避|  
|`string1`.fontcolor\(`color`\)|テキストを HTML の COLOR 属性付きの \<FONT\> タグと \<\/FONT\> タグで囲みます。|`color` パラメーターは色の 16 進値または定義済みの名前を含む文字列値です。  有効な定義済みの色の名前は [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] をホストするブラウザーおよびバージョンによって異なります。|非推奨|  
|`string1`.fontsize\(`size`\)|テキストを HTML の SIZE 属性付きの \<FONT\> タグと \<\/FONT\> タグで囲みます。|`size` パラメーターは、テキストのサイズを指定する整数値です。  有効な整数値は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のホストのブラウザーおよびバージョンによって異なります。|非推奨|  
|`string1`.italics\(\)|テキストを HTML の \<I\> タグと \<\/I\> タグで囲みます。||使用回避|  
|`string1`.link\(`href`\)|テキストを HTML の HREF 属性付きの \<A\> タグと \<\/A\> タグで囲みます。|`href` パラメーターは、HTML の \<A\> タグと \<\/A\> タグの HREF 属性に配置されるテキストです。||  
|`string1`.small\(\)|テキストを HTML の \<SMALL\> タグと \<\/SMALL\> タグで囲みます。||使用回避|  
|`string1`.strike\(\)|テキストを HTML の \<STRIKE\> タグと \<\/STRIKE\> タグで囲みます。||非推奨|  
|`string1`.sub\(\)|テキストを HTML の \<SUB\> タグと \<\/SUB\> タグで囲みます。|||  
|`string1`.sup\(\)|テキストを HTML の \<SUP\> タグと \<\/SUP\> タグで囲みます。|||  
  
## 解説  
 HTML タグが文字列に既に適用されているかどうかを判断するためのチェックは実行されません。  
  
## 使用例  
 HTML タグ メソッドを使用する方法の例を次に示します。  
  
```javascript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## 要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)