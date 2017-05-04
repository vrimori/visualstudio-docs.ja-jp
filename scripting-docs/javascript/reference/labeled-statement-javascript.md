---
title: "ラベル付きステートメント (JavaScript) | Microsoft Docs"
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
  - "labeled_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue ステートメント"
  - "識別子, ステートメント"
  - "labeled ステートメント"
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# ラベル付きステートメント (JavaScript)
ステートメントの識別子を指定します。  
  
## 構文  
  
```  
  
      label :  
   statements   
```  
  
## パラメーター  
 *label*  
 必須です。  ラベル付きステートメントを参照するときに使用する、固有の識別子を指定します。  
  
 `statements`  
 省略可能です。  *label* に関連する 1 つ以上のステートメントを指定します。  
  
## 解説  
 ラベルは、**break** と **continue** が適用されるステートメントを指定するために、**break** ステートメントと **continue** ステートメントによって使用されます。  
  
## 使用例  
 次のコードでは、**continue** ステートメントは、`Inner:` ステートメントが前に付いた **for** ループを参照しています。  `j` が 24 に達すると、**continue** ステートメントが実行され、その **for** ループが次の反復処理に移ります。  各行には 21 ～ 23 と 25 ～ 30 の数字が出力されます。  
  
```javascript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 参照  
 [break ステートメント](../../javascript/reference/break-statement-javascript.md)   
 [continue ステートメント](../../javascript/reference/continue-statement-javascript.md)