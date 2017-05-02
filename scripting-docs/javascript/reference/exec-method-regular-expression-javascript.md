---
title: "exec メソッド (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "exec"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Exec メソッド"
  - "対応する文字列"
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# exec メソッド (Regular Expression) (JavaScript)
正規表現パターンを使って文字列に対して検索を実行し、検索結果を配列に格納して返します。  
  
## 構文  
  
```  
  
rgExp.exec(str)   
```  
  
## パラメーター  
 `rgExp`  
 必須です。  検索に使用する正規表現のパターンと適用できるフラグを格納した **Regular Expression** オブジェクトのインスタンスです。  
  
 `str`  
 必須です。  検索対象とする `String` オブジェクトの名前またはリテラル文字列を指定します。  
  
## 解説  
 パターンに一致する文字列が見つからなかった場合、`exec` メソッドは `null` を返します。  一致する文字列が見つかった場合は、`exec` は配列を返し、さらにグローバルな `RegExp` オブジェクトのプロパティが検索結果を反映して更新されます。  配列の要素 0 には一致結果全体が、要素が 1 から *n* には、一致結果の中に副次的に含まれる一致の内容が格納されます。  この処理は、グローバル フラグ \(**g**\) が設定されていない場合の `match` メソッドの処理と同じです。  
  
 正規表現でグローバル フラグが設定されている場合、`exec` により、`lastIndex` の値で指定された位置から文字列の検索が開始されます。  グローバル フラグが設定されていない場合、`exec` により、`lastIndex` の値に関係なく、検索は文字列の先頭から開始されます。  
  
 `exec` メソッドが返す配列には、**input**、**index**、および **lastIndex** の 3 つのプロパティがあります。**input** プロパティには、検索された文字列全体が格納されます。  **index** プロパティには、検索された文字列内の一致した部分文字列の位置が格納されます。  `lastIndex` プロパティには、一致文字列の末尾の文字に続く位置が格納されます。  
  
## 使用例  
 `exec` メソッドの使用例を次に示します。  
  
```javascript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)  
  
## 参照  
 [match メソッド \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [search メソッド \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [test メソッド \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/ja-jp/3b62e27c-4f07-4726-a95b-6e841807bfaf)