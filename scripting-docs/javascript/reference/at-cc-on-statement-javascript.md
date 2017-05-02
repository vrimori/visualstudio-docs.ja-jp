---
title: "@cc_on ステートメント (JavaScript) | Microsoft Docs"
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
  - "@cc_on_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@cc_on ステートメント"
  - "@if ステートメント"
  - "@set ステートメント"
  - "条件付きコンパイル, アクティブ"
ms.assetid: fdeda7ee-b9f4-4e52-8aa2-21c90c02a332
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# @cc_on ステートメント (JavaScript)
スクリプトのコメント内での条件付きコンパイルのサポートをアクティブにします。  
  
> [!WARNING]
>  条件付きコンパイルは、Internet Explorer 11 標準モードと [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。  条件付きコンパイルは、Internet Explorer 10 標準モードと、それ以前のすべてのバージョンでサポートされています。  
  
## 構文  
  
```  
@cc_on   
```  
  
## 解説  
 `@cc_on` ステートメントにより、スクリプトのコメント内の条件付きコンパイルが有効になります。  
  
 ASP ページまたは ASP.NET ページ用に作成されたスクリプトや、コマンド ライン プログラム用に作成されたスクリプトでは、コンパイラの機能が他の方法を使用して決定されるため、条件付きコンパイル変数を使用することは一般的ではありません。  
  
 Web ページ用のスクリプトを作成するとき、常にコメント内に条件付きコンパイル コードを配置してください。  これにより、条件付きコンパイルをサポートしないホストでこれらのコードが無視されます。  
  
 条件付きコンパイルをサポートしないブラウザーがスクリプトを有効な構文として受け入れるように、コメントで `@cc_on` ステートメントを使用することを強くお勧めします。  
  
 `@if` ステートメントまたは `@set` ステートメントをコメント外に記述することでも、条件付きコンパイルをアクティブにできます。  
  
## 使用例  
 `@cc_on` ステートメントの使用例を次に示します。  
  
```javascript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on the 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on the 16-bit version of Windows.");  
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
 [@if ステートメント](../../javascript/reference/at-if-statement-javascript.md)   
 [@set ステートメント](../../javascript/reference/at-set-statement-javascript.md)