---
title: "caller プロパティ (Function) (JavaScript) | Microsoft Docs"
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
  - "caller"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "caller プロパティ"
  - "関数呼び出し、関数 (実行する)"
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# caller プロパティ (Function) (JavaScript)
現在の関数を呼び出した関数を取得します。  
  
## 構文  
  
```  
  
functionName.caller  
```  
  
## 解説  
 `functionName` オブジェクトは、実行中の関数の名前です。  
  
 `caller` プロパティは、実行中の関数に対してのみ定義されます。  関数が [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] プログラムのトップレベルから呼び出された場合、`caller` は `null` になります。  
  
 文字列のコンテキストで `caller` プロパティを使用すると、`functionName`.`toString` と同じ結果になります。つまり、関数の逆コンパイルされたテキストが表示されます。  
  
 `caller` プロパティの使用例を次に示します。  
  
```javascript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 参照  
 [function ステートメント](../../javascript/reference/function-statement-javascript.md)