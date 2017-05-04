---
title: "debugger ステートメント (JavaScript) | Microsoft Docs"
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
  - "debugger_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "debugger ステートメント"
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# debugger ステートメント (JavaScript)
実行を中断するステートメントです。  
  
## 構文  
  
```  
debugger  
```  
  
## 解説  
 `debugger` ステートメントは、プロシージャ内の任意の場所に置いて、実行を中断できます。  `debugger` ステートメントは、プログラム コードのブレークポイントと同じ動作をします。  
  
 `debugger` ステートメントは実行を中断しますが、ファイルを閉じたり、変数をクリアしたりはしません。  
  
> [!NOTE]
>  スクリプトをデバッグする場合を除いて、`debugger` ステートメントの影響はありません。  
  
## 使用例  
 `debugger` ステートメントを使用して、`for` ループを繰り返すごとに実行を中断する例を次に示します。  
  
> [!NOTE]
>  この例を実行するには、スクリプト デバッガーをインストールし、スクリプトをデバッグ モードで実行する必要があります。  
>   
>  Internet Explorer 8 には、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] デバッガーが含まれています。  Internet Explorer の旧バージョンを使用する場合は、「[方法: Internet Explorer でスクリプトのデバッグを有効にして起動する](http://go.microsoft.com/fwlink/?LinkId=133801)」を参照してください。  
  
```javascript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 参照  
 [JavaScript ステートメント](../../javascript/reference/javascript-statements.md)   
 [条件付きコンパイル](../../javascript/advanced/conditional-compilation-javascript.md)