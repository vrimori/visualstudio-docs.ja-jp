---
title: "length プロパティ (Function) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Length プロパティ"
  - "length プロパティ (function)"
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# length プロパティ (Function) (JavaScript)
関数に定義されている引数の数を取得します。  
  
## 構文  
  
```  
  
functionName.length  
```  
  
## 解説  
 必須の *functionName* オブジェクトには、実行中の関数の名前を指定します。  
  
 関数のインスタンスが作成されると、スクリプト エンジンによって、関数の定義に含まれている引数の数が関数の **length** プロパティに初期設定されます。  
  
 **length** プロパティと異なる数の引数を指定して関数を呼び出した場合に何が起こるかは、各関数に依存します。  
  
## 使用例  
 **length** プロパティの使用例を次に示します。  
  
```javascript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 参照  
 [arguments プロパティ \(Function\)](../../javascript/reference/arguments-property-function-javascript.md)   
 [length プロパティ \(Array\)](../../javascript/reference/length-property-array-javascript.md)   
 [length プロパティ \(String\)](../../javascript/reference/length-property-string-javascript.md)