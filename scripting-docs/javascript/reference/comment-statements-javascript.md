---
title: "コメント ステートメント (JavaScript) | Microsoft Docs"
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
  - "Comment_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "コメント ステートメント"
  - "コメント, 無視"
ms.assetid: b604824f-ac17-49d3-bcdb-2a893ab5fff8
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# コメント ステートメント (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] パーサーがコメントを無視するようにします。  
  
## 構文  
  
```  
Single-line Comment:  
// comment   
```  
  
```  
Multiline Comment:  
/*  
comment  
*/  
```  
  
```  
Comments with conditional compilation:  
//@CondStatement   
  
/*@  
condStatement  
@*/  
```  
  
## 解説  
 `comment` 引数は、スクリプトに含めるコメントのテキストです。  `condStatement` 引数は、条件付きコンパイルがアクティブになっている場合に使用します。  単一行コメントを使用する場合は、"\/\/" と "@" 文字の間にスペースを入れないでください。  
  
 コメントを使用して、スクリプトの一部が [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] パーサーに読み取られないようにします。  コメントを使用して、プログラム内に説明のための注記を含めることができます。  
  
 単一行コメントを使用する場合、パーサーは、コメント マーカーと行末の間にあるすべてのテキストを無視します。  複数行コメントを使用する場合、パーサーは、開始マーカーと終了マーカーの間にあるすべてのテキストを無視します。  
  
 コメントを使用して、条件付きコンパイルをサポートすると共に、その機能をサポートしないブラウザーとの互換性も維持することができます。  これらのブラウザーは、それらの形式のコメントを、それぞれ単一行または複数行のコメントとして処理します。  
  
## 使用例  
 次の例では、コメントの最も一般的な使用方法を示します。  
  
```javascript  
/* This is a multiline comment that  
    can span as many lines as necessary.  */  
function myfunction(arg1, arg2){  
    var r;  
    // This is a single line comment.  
    r = arg1 + arg2  
    return(r);  
}  
```  
  
## 使用例  
 次の例では、条件付きコンパイルを使用する方法を示します。  この例では、`@cc_on` ステートメントによって条件付きコンパイルがアクティブにされた場合にだけ使用される、特殊なコメント区切り文字を使用しています。  条件付きコンパイルをサポートしないスクリプト エンジンでは、条件付きコンパイルがサポートされていないというメッセージのみが表示されます。  
  
```javascript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]