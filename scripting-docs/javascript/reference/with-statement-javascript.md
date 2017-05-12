---
title: "with ステートメント (JavaScript) | Microsoft Docs"
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
  - "with_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "With ステートメント"
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# with ステートメント (JavaScript)
ステートメントで使用する既定のオブジェクトを設定します。  
  
## 構文  
  
```  
with (object) {  
    statements  
}   
```  
  
## パラメーター  
 `object`  
 既定のオブジェクト。  
  
 `statements`  
 `object` を既定のオブジェクトとして使用する 1 つ以上のステートメントを指定します。  
  
## 解説  
 一般に、`with` ステートメントは特定の場面で、記述するコードの量を少なくするために使用します。  
  
> [!WARNING]
>  厳密モードでは `with` は使用できません。  `with` を使用すると、コードの読み取りとデバッグが困難になる場合があるため、通常は避けるようにしてください。  
  
## 使用例  
 この例では、`Math` オブジェクトが繰り返し使用されています。  
  
```javascript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## 使用例  
 `with` ステートメントを使用してこの例を記述し直すと、コードがより簡潔になります。  
  
```javascript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [this ステートメント](../../javascript/reference/this-statement-javascript.md)