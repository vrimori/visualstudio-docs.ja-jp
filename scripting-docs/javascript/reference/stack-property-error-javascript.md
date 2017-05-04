---
title: "stack プロパティ (Error) (JavaScript) | Microsoft Docs"
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
  - "Error.stack"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "エラー スタック [JavaScript]"
  - "JavaScript エラー スタック"
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# stack プロパティ (Error) (JavaScript)
スタック トレース フレームを含む文字列としてエラー スタックを取得または設定します。  
  
## 構文  
  
```  
  
object  
.stack   
```  
  
## 解説  
 エラーが構築され、エラーが発生してトレース情報が取得されると、`stack` プロパティは、`undefined` に設定されます。  エラーが複数回発生すると、エラーが発生するたびに `stack`プロパティが更新されます。  
  
 スタック フレームは、FunctionName で \<完全修飾名または URL\>:\<行番号\>:\<列番号\> という形式で表示されます。  
  
 独自のエラー オブジェクトを作成し、値にスタック トレースを設定すると、エラーがスローされたときに、値は上書きされません。  
  
 `stack` プロパティの場合、フレーム内にインライン関数は表示されません。  物理スタックのみが表示されます。  
  
## 使用例  
 次の例では、エラーをキャッチしたときにスタックを取得する方法を示します。  
  
```javascript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## 使用例  
 次の例では、スタックを設定してから取得する方法を示します。  
  
```javascript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## 必要条件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **対照**: [Error オブジェクト](../../javascript/reference/error-object-javascript.md)  
  
## 参照  
 [description プロパティ \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [message プロパティ \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [name プロパティ \(Error\)](../../javascript/reference/name-property-error-javascript.md)   
 [stackTraceLimit プロパティ \(Error\)](../../javascript/reference/stacktracelimit-property-error-javascript.md)