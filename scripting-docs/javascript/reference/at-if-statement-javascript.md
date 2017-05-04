---
title: "@if ステートメント (JavaScript) | Microsoft Docs"
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
  - "@if_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@if ステートメント"
  - "条件付きステートメント, if"
  - "elif ステートメント"
  - "else ステートメント"
  - "if ステートメント, @if"
ms.assetid: ff11b29d-c06a-4276-b11d-db73e2da98ac
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# @if ステートメント (JavaScript)
式の値に応じてステートメント グループを条件付きで実行します。  
  
> [!WARNING]
>  条件付きコンパイルは、Internet Explorer 11 標準モードと [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。  条件付きコンパイルは、Internet Explorer 10 標準モードと、それ以前のすべてのバージョンでサポートされています。  
  
## 構文  
  
```  
  
      @if (  
   condition1  
)  
   text1  
[@elif (  
   condition2  
)  
   text2]  
[@else  
   text3]  
@end   
```  
  
## パラメーター  
 *condition1, condition2*  
 省略可能。  ブール式に強制変換できる式を指定します。  
  
 `text1`  
 省略可能です。  `condition1` に指定した条件が真 \(**true**\) の場合に解析するテキストを指定します。  
  
 `text2`  
 省略可能です。  `condition1` に指定した条件が偽 \(**false**\) で `condition2` に指定した条件が真 \(**true**\) の場合に解析するテキストを指定します。  
  
 `text3`  
 省略可能です。  `condition1` も `condition2` も偽 \(**false**\) の場合に解析するテキストを指定します。  
  
## 解説  
 `@if` ステートメントを作成する際、各句を個別の行に配置する必要はありません。  複数の **@elif** 句を使用することもできます。  ただし、**@elif** 句はすべて **@else** 句より前に記述する必要があります。  
  
 `@if` ステートメントは、一般にテキスト出力に使用するテキストを複数の候補の中から選択する場合に使用します。  
  
 ASP ページ用に作成されたスクリプト、ASP.NET ページ用に作成されたスクリプト、またはコマンド ライン プログラム用に作成されたスクリプトで条件付きコンパイル変数を使用することは一般的ではありません。  これは、他の方法を使用してコンパイラの機能を決定できるためです。  
  
 Web ページ用のスクリプトを作成するとき、常にコメント内に条件付きコンパイル コードを追加してください。  これにより、条件付きコンパイルをサポートしないホストでこれらのコードが無視されます。  
  
## 使用例  
 **@if...@elif...@else...@end** ステートメントの使用例を次に示します。  
  
```javascript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on a 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on a 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## 必要条件  
 Internet Explorer のすべてのバージョンでサポートされていますが、[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。  
  
## 参照  
 [条件付きコンパイル](../../javascript/advanced/conditional-compilation-javascript.md)   
 [条件付きコンパイル変数](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc\_on ステートメント](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@set ステートメント](../../javascript/reference/at-set-statement-javascript.md)