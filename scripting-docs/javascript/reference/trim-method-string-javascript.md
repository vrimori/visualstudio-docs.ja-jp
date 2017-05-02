---
title: "trim メソッド (String) (JavaScript) | Microsoft Docs"
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
  - "trim メソッド"
ms.assetid: 03d38c7e-25cd-4ede-b58e-1a10b5249bab
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# trim メソッド (String) (JavaScript)
文字列から先頭および末尾の空白と行終端記号の文字を削除します。  
  
## 構文  
  
```  
  
stringObj.trim()  
```  
  
## パラメーター  
 `stringObj`  
 必須です。  `String` オブジェクトまたは文字列リテラル。  この文字列は、`trim` メソッドでは変更されません。  
  
## 戻り値  
 元の文字列から先頭および末尾の空白と行終端記号の文字を削除した文字列。  
  
## 解説  
 削除される文字には、空白、タブ、フォーム フィード、キャリッジ リターン、ライン フィードが含まれます。  空白と行終端記号の文字の一覧については、「[特殊文字](../../javascript/advanced/special-characters-javascript.md)」を参照してください。  
  
 トリム メソッドを実装する方法を示す例については、[プロトタイプとプロトタイプ継承](../../javascript/advanced/prototypes-and-prototype-inheritance.md) を参照してください。  
  
## 使用例  
 `trim` メソッドの使用例を次に示します。  
  
```javascript  
var message = "    abc def     \r\n  ";  
  
document.write("[" + message.trim() + "]");  
document.write("<br/>");  
document.write("length: " + message.trim().length);  
  
// Output:  
//  [abc def]  
//  length: 7  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [特殊文字](../../javascript/advanced/special-characters-javascript.md)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)   
 [スクロール、パン、ズームのサンプル アプリ](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)