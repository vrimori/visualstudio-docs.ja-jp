---
title: "Debug オブジェクト (JavaScript) | Microsoft Docs"
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
  - "debug"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Debug オブジェクト"
  - "Debug オブジェクト、Debug オブジェクトの概要"
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Debug オブジェクト (JavaScript)
出力をデバッガーに送信する組み込みのグローバル オブジェクトです。  
  
## 構文  
  
```  
Debug.function  
```  
  
## 解説  
 Debug オブジェクトをインスタンス化することはありません。 そのすべてのプロパティおよびメソッドには、`function` を呼び出してアクセスできます。  
  
 Internet Explorer と [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリのデバッグ方法は異なります。[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリでは、`write` オブジェクトの `writeln` 関数と `Debug` 関数で、実行時に Visual Studio の**出力**ウィンドウに文字列を表示します。[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリのデバッグについて詳しくは、「[Visual Studio でのアプリのデバッグ](../Topic/Debug%20Store%20apps%20in%20Visual%20Studio.md)」をご覧ください。  
  
 Internet Explorer スクリプトをデバッグするには、スクリプト デバッガーをインストールし、スクリプトをデバッグ モードで実行する必要があります。 Internet Explorer 8 以降のバージョンには [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のデバッガーが含まれます。 以前のバージョンの Internet Explorer を使用している場合は、「[方法 : Internet Explorer でスクリプトのデバッグを有効にして起動する](http://go.microsoft.com/fwlink/?LinkId=133801)」をご覧ください。  
  
 スクリプトがデバッグされない場合、関数の影響はありません。  
  
## 使用例  
 この例では、`write` 関数を使用して変数の値を表示します。  
  
```javascript  
var counter = 42; Debug.write("The value of counter is " + counter);  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 定数  
 [デバッグ定数](../../javascript/reference/debug-constants.md)  
  
## プロパティ  
 [Debug.debuggerEnabled プロパティ](../../javascript/reference/debug-debuggerenabled-property.md) &#124; [Debug.setNonUserCodeExceptions プロパティ](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## 関数  
 [Debug.msTraceAsyncCallbackStarting 関数](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md) &#124; [Debug.msTraceAsyncCallbackCompleted 関数](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md) &#124; [Debug.msTraceAsyncOperationCompleted 関数](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md) &#124; [Debug.msTraceAsyncOperationStarting 関数](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md) &#124; [Debug.msUpdateAsyncCallbackRelation 関数](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md) &#124; [Debug.write 関数](../../javascript/reference/debug-write-function-javascript.md) &#124; [Debug.writeln 関数](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## 参照  
 [debugger ステートメント](../../javascript/reference/debugger-statement-javascript.md)